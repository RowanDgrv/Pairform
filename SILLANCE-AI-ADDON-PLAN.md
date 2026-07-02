# Assistant IA Sillance — Plan financier de l'add-on coach

> Option payante, séparée, pour le coach : un résumé + des recommandations
> automatiques sur **chaque activité** (zones, FC, allure/puissance, découplage),
> jugés **par rapport à l'objectif** de la séance.

---

## 1. Architecture de coût (ce qui se paie réellement)

On **sépare le calcul du jugement** :

- **Couche déterministe (gratuite)** : tout le bilan chiffré (zones FC, %FCmax,
  temps en zone cible, découplage, pics par intervalle) est calculé **dans
  l'app**, côté client / Postgres. Zéro coût marginal.
- **Couche IA (payante)** : seul le **payload chiffré** part vers Claude, qui
  **rédige** le verdict + les recos. Claude n'invente aucun chiffre → réponses
  courtes, fiables, bon marché.

### Coût d'un résumé (estimation par tokens)

| Poste | Tokens | Mis en cache ? |
|---|---|---|
| System prompt + rubriques (Z2 / LT1 / seuil / VMA / VO2max…) | ~2 000 | ✅ cache (TTL 5 min) |
| Payload dynamique (bilan chiffré de la séance) | ~500 | ❌ |
| Réponse (verdict + 2-3 recos) | ~400 | — |

**Le prompt caching est clé** : les rubriques (le gros du prompt) sont identiques
à chaque appel → facturées au tarif « cache read » (≈ 10 % du prix d'entrée).

| Modèle | Coût / résumé | Pour 200 résumés/mois | Pour 500 résumés/mois |
|---|---|---|---|
| **Claude Sonnet 4.6** (qualité) | ≈ **0,0075 €** | ≈ **1,50 €** | ≈ 3,75 € |
| **Claude Haiku 4.5** (volume) | ≈ **0,0025 €** | ≈ 0,50 € | ≈ 1,25 € |

*(Hypothèses : Sonnet ~3 $/M in · 15 $/M out · 0,30 $/M cache-read ; Haiku ~1 $/M in · 5 $/M out. 1 $ ≈ 0,93 €.)*

> **Décision technique** : Sonnet 4.6 par défaut (le verdict coaching mérite la
> qualité), bascule Haiku 4.5 possible si un coach dépasse un très gros volume.
> Coût stocké une fois par séance (table `session_summaries`) → **jamais
> recalculé**, donc pas de double facturation si le coach rouvre l'analyse.

---

## 2. Les 3 modèles de monétisation comparés

| | A. **Add-on séparé** *(retenu)* | B. Inclus dans le palier haut | C. Quota + surcoût |
|---|---|---|---|
| Prix | **12 €/mois** en plus | 0 € (bundlé) | X inclus puis paiement à l'usage |
| Revenu net / coach | **~10,5 €/mois** | +0 € direct (renforce la rétention) | variable |
| Coût API porté | largement couvert | dilué dans le palier | aligné mais minime |
| Complexité Stripe | 1 produit récurrent | nulle | métrage usage = lourd |
| Lisibilité client | **forte** (« je paie l'IA ») | faible | moyenne |
| Risque | faible | manque à gagner | sur-ingénierie |

**Pourquoi A.** Le coût API est tellement bas (~1,50 €/mois pour un coach actif)
que le **métrage à l'usage (C) ne vaut pas sa complexité**. Le bundle (B) noie la
valeur. Un **add-on à 12 €/mois** est lisible (« j'active l'assistant IA »),
finance très largement l'API, et crée une **ligne de revenu nette nouvelle**.

---

## 3. Compte de résultat de l'add-on (modèle A)

Marge brute par coach abonné (hypothèse coach actif, 200 résumés/mois, Sonnet 4.6) :

```
Prix add-on .......................... 12,00 €
– Frais Stripe (~1,4 % + 0,25 €) .... – 0,42 €
– Coût API Claude (200 résumés) ..... – 1,50 €
= Marge brute ........................ 10,08 €   →  ~84 % de marge
```

Projection (marge brute mensuelle, hors coût fixe d'infra déjà payé pour le SaaS) :

| Coachs ayant l'add-on | Revenu | Coût API | Stripe | **Marge brute / mois** |
|---|---|---|---|---|
| 10 | 120 € | 15 € | 4 € | **~101 €** |
| 50 | 600 € | 75 € | 21 € | **~504 €** |
| 200 | 2 400 € | 300 € | 84 € | **~2 016 €** |
| 500 | 6 000 € | 750 € | 210 € | **~5 040 €** |

**Seuil de rentabilité** : dès le **1er abonné** (le coût API d'un coach <2 €
est couvert par les 12 €). Le risque financier est quasi nul.

---

## 4. Place dans la grille Sillance

L'add-on **se cumule** à l'abonnement coach existant (il ne le remplace pas) :

- **Sillance SaaS coach** (la sub `plan_kind = 'coach'`) — accès à l'app.
- **+ Assistant IA** — `12 €/mois`, nouvelle entitlement `ai_addon`.

Et il s'inscrit dans la logique « la data/analyse justifie le palier » déjà posée
côté Club (Coaching+ 119 €). Ici l'IA est le **cran d'analyse supérieur** côté
coach solo.

### Fair-use plutôt que quota dur
Inclure **jusqu'à ~300 résumés/mois** (couvre quasi tous les coachs). Au-delà,
on ne coupe pas : on bascule en Haiku 4.5 (coût ÷3) ou on propose un palier
« IA Pro ». Pas de compteur anxiogène pour le client.

---

## 5. Garde-fous

- **Coût plafonné par design** : 1 résumé = 1 appel court, mis en cache → pas de
  dérive. Un résumé déjà généré est relu depuis `session_summaries` (0 € API).
- **Pas de surprise** : le front affiche « démo » tant que l'add-on n'est pas
  activé ; aucun appel API n'est émis sans abonnement actif (gate `ai_addon`
  vérifié côté edge function, jamais côté front).
- **Qualité** : Claude ne reçoit que des chiffres déjà calculés → pas
  d'hallucination de données, verdict vérifiable contre les graphiques.

---

### En une phrase
**12 €/mois, ~84 % de marge, rentable dès le premier abonné, et un coût API si
bas (~1,5 €/coach) que la seule vraie question est commerciale, pas technique.**
