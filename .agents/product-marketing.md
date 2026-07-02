# Product Marketing Context — Sillance

*Dernière mise à jour : 2026-07-02 · V1 (auto-rédigée, à valider par Rowan)*
*Marché FR → document en français. Focus : Phase 1 = coachs solo triathlon & Hyrox.*

---

## Product Overview
**One-liner :** Sillance, la plateforme qui fait progresser coach et athlète ensemble — planification + analyse de données d'entraînement, dans le sillage l'un de l'autre.

**Ce que c'est :** une app web pour coachs d'endurance (triathlon, Hyrox, multisport) et leurs athlètes. Le coach planifie les séances, l'athlète les exécute (montre connectée / fichier .FIT), et Sillance transforme la donnée brute en **analyse décisionnelle** : charge d'entraînement (PMC — CTL/ATL/TSB), TSS multi-sport, courbe puissance-durée, durabilité, profil Hyrox, découplage aérobie, comparaison de séances, et un assistant IA qui résume chaque séance.

**Catégorie (le rayon où on nous cherche) :** logiciel de coaching / plateforme d'analyse d'entraînement d'endurance. Alternative française et Hyrox-native à TrainingPeaks / Nolio.

**Type :** SaaS web (Supabase). B2B (coach) qui embarque le B2C (athlète).

**Business model :**
- SaaS Sillance : abonnement coach (+ athlète Phase 3, + club Phase 2).
- Coach → ses athlètes : le coach vend son coaching via Sillance (offre ~99 €/mois éditable, encaissement Stripe Connect).
- Add-on **Assistant IA** : 12 €/mois (résumés de séance générés par Claude).
- Club (Phase 2) : échelle 3 offres — à la séance 15 € / abo club 59 € / Coaching+ 119 € (la data est réservée au palier haut).

---

## Target Audience — Phase 1 (à ne PAS élargir au lancement)
**Qui :** coach **indépendant** d'endurance, seul, qui suit 5–40 athlètes.
- **Coach triathlon** (le cœur de cible, l'avantage déloyal de Rowan : c'est son monde).
- **Coach / box Hyrox** (marché en explosion, **sans logiciel dédié** aujourd'hui → océan bleu).

**Profil type :** ancien athlète ou passionné devenu coach, à l'aise avec la donnée mais **noyé dans Excel + WhatsApp + TrainingPeaks à moitié**. Vend son suivi 80–200 €/mois/athlète. Sa crédibilité = la qualité de son analyse et de son feedback.

**Jobs to be done (ce pour quoi il « embauche » Sillance) :**
1. « Voir la donnée réelle de mes athlètes au même endroit » (depuis que Strava a fermé l'accès coach en 11/2024, c'est cassé).
2. « Passer moins de temps à bricoler des tableaux et plus à coacher. »
3. « Justifier mon tarif par une analyse que l'athlète ne peut pas faire seul. »
4. « Encaisser mes athlètes proprement, sans virements à la main. »

**Anti-cible (Phase 1) :** clubs multi-coachs, fédérations, salles de sport généralistes, athlètes solo sans coach. (Viennent en Phase 2/3.)

---

## Personas
Coach solo = il est **utilisateur, champion, décideur ET payeur** à la fois → cycle de vente court, pas de comité. C'est un énorme avantage.

| Persona | Ce qui compte pour lui | Son défi | Ce qu'on lui promet |
|---|---|---|---|
| **Coach solo (acheteur)** | Crédibilité, gain de temps, revenu récurrent | Data éparpillée, outils US chers/complexes, admin chronophage | « Une analyse qui te fait passer pour le meilleur coach de tes athlètes — et tu es payé automatiquement. » |
| **Athlète (utilisateur final)** | Comprendre sa progression, se sentir suivi | Il balance des chiffres qu'il ne sait pas lire | « Avance dans le sillage de ton coach : tes données deviennent un plan. » |

---

## Problems & Pain Points
**Problème central :** le coach d'endurance croule sous la donnée mais n'a pas d'outil qui la lui rende **exploitable, française et Hyrox-compatible**, sans y passer ses soirées.

**Pourquoi les alternatives ne suffisent pas :**
- **Strava** ne montre plus la data d'un athlète à son coach (API restreinte depuis 11/2024). Le canal « gratuit » historique est mort.
- **TrainingPeaks / WKO** : puissant mais **cher, en anglais, pensé vélo/US**, complexe, zéro Hyrox, aucune brique de facturation coach→athlète.
- **Excel + WhatsApp** : gratuit mais chronophage, pas d'analyse, pas d'image pro, rien de récurrent.
- **Nolio** (rival FR direct) : bon sur le suivi, mais pas d'angle Hyrox, analyse et identité moins fortes.

**Ce que ça lui coûte :** des heures d'admin chaque semaine, une image « bricoleur », un tarif difficile à défendre, et de la donnée gâchée (il ne « voit » pas ce qui se passe).

**Tension émotionnelle :** peur de paraître amateur face à un athlète exigeant ; frustration de « sentir » qu'il pourrait mieux faire mais de ne pas avoir les moyens de le prouver.

---

## Competitive Landscape
- **Direct — Nolio (FR) :** même promesse (plateforme coach-athlète FR). Faille : pas de verticale Hyrox, analyse et identité de marque moins différenciantes, moins « cockpit performance ».
- **Direct — TrainingPeaks / WKO (US) :** incumbent analyse. Faille : anglais, cher, complexe, orienté vélo, aucun Hyrox, pas de facturation coach→athlète intégrée.
- **Secondaire — Strava / Garmin Connect :** l'athlète y est déjà. Faille : conçus pour l'athlète solo, **pas pour la paire coach-athlète**, et Strava a fermé la porte au coach.
- **Indirect — Excel + WhatsApp + Google Sheets :** le vrai concurrent quotidien. Faille : zéro analyse, zéro automatisation, zéro récurrence de revenu, image non-pro.

---

## Differentiation
**Différenciateurs clés :**
1. **L'analyse comme moat** — PMC (CTL/ATL/TSB), TSS multi-sport transparent (Coggan vélo · rTSS course · sTSS nat · hrTSS FC · sRPE Hyrox/renfo), courbe puissance-durée, **durabilité** (puissance sous fatigue), **découplage** aérobie, comparateur de séances similaires. Personne en FR ne pousse aussi loin l'analyse rendue lisible.
2. **Hyrox-native** — profil Hyrox à 2 axes (charge aérobie/musculaire) + dégradation d'allure + « compromised running », fondé sur la 1ʳᵉ étude scientifique Hyrox (Frontiers 2025). **Marché sans logiciel = premier arrivé.**
3. **Device-agnostic post-Strava** — sync Garmin / Coros / import .FIT/.TCX/.GPX. On répond au trou laissé par la fermeture Strava au lieu de le subir.
4. **La paire, pas le solo** — séparation nette des rôles coach/athlète, la donnée circule dans le bon sens. C'est le sens du nom : *sillage*.
5. **Facturation coach→athlète intégrée** (Stripe Connect) — le coach est payé automatiquement, tarif éditable.
6. **Assistant IA** — résumé + recommandations chiffrées par séance (add-on).
7. **Français, épuré, premium** — esthétique « cockpit de performance », pas un tableur anglophone.

**Pourquoi c'est mieux :** le coach passe de « je bricole et je devine » à « j'analyse, je décide, je facture » — et il en tire une image pro qui justifie son tarif.

---

## Objections
| Objection | Réponse |
|---|---|
| « J'ai déjà TrainingPeaks / mon Excel. » | Sillance réunit l'analyse ET la relation ET la facturation, en français, avec Hyrox — là où TP s'arrête et où Excel te coûte tes soirées. Import de tes données, tu ne repars pas de zéro. |
| « Mes athlètes sont sur Strava. » | Justement : depuis 11/2024 Strava ne te laisse plus voir leur data. Sillance récupère via Garmin/Coros/.FIT — tu revois enfin ce qui se passe. |
| « C'est encore un abo de plus. » | Il te rapporte : tu encaisses tes athlètes via Sillance (Stripe). L'outil se paie tout seul dès le 1er athlète facturé dessus. |
| « Trop compliqué / pas le temps d'apprendre. » | Interface épurée, mode démo pour tout explorer sans risque, et l'assistant IA fait le résumé à ta place. |
| « L'analyse, je sais déjà la faire. » | Alors tu gagnes le temps de la produire — et tes athlètes voient un rendu pro qu'ils ne peuvent pas obtenir seuls. |

**Anti-persona :** le coach qui ne veut pas de data (« au feeling »), l'athlète sans coach, la grosse structure multi-coachs à cycle d'achat long. Pas la Phase 1.

---

## Switching Dynamics (JTBD — 4 forces)
- **Push (ce qui le dégoûte de l'existant) :** Strava fermé au coach, Excel chronophage, TP cher/anglais/pas Hyrox, admin de paiement pénible.
- **Pull (ce qui l'attire) :** analyse poussée en FR, Hyrox-native, facturation intégrée, image premium, récupération de la data device.
- **Habit (ce qui le retient) :** ses tableaux Excel « qui marchent », l'inertie, la peur de re-saisir.
- **Anxiety (ce qui l'inquiète) :** « migrer va me prendre des heures », « mes athlètes vont devoir changer leurs habitudes ». → Rassurer : import, onboarding guidé, mode démo, la sync est côté coach.

---

## Customer Language
**Comment il décrit le problème (à capter en vrai en interview) :**
- « Depuis que Strava a coupé, je vois plus rien de mes gars. »
- « Je passe mes dimanches soirs sur Excel. »
- « TrainingPeaks c'est une usine à gaz, et en anglais. »
- « Y'a rien pour le Hyrox. »

**Comment il décrit la solution :**
- « Enfin un truc français qui analyse pour de vrai. »
- « Je fais pro sans y passer des heures. »

**Mots à utiliser :** sillage, cadence, charge, fraîcheur (TSB), durabilité, lisible, décisionnel, français, Hyrox, cockpit, progresser ensemble, être payé automatiquement.
**Mots à éviter :** « dashboard » à outrance, jargon US non traduit, « all-in-one » creux, « révolutionnaire », promesses de perf magiques.

**Glossaire produit :**
| Terme | Sens |
|---|---|
| Sillage | Aspiration derrière un nageur/cycliste = avancer porté par l'autre. Marque + thèse produit. |
| PMC / CTL-ATL-TSB | Charge chronique / aiguë / fraîcheur — le tableau de forme. |
| TSS multi-sport | Monnaie commune de charge (vélo/course/nat/FC/Hyrox). |
| Durabilité | Puissance/allure conservée sous fatigue. |
| Découplage | Dérive FC vs puissance/allure = signal d'endurance. |

---

## Brand Voice
**Ton :** expert mais accessible, direct, un peu sportif/complice — jamais corporate, jamais bullshit.
**Style :** phrases courtes, chiffrées, concrètes. On parle à un coach, pas à un DSI.
**Personnalité (5 adjectifs) :** précis, exigeant, français, premium, complice.
**Ancrage visuel :** cockpit sombre, Oswald, accent teal #46C2D8, mark « sillage ». (NE PAS partir en éditorial clair/soin — décision arrêtée.)

---

## Proof Points
**À construire (le nerf du lancement — Rowan doit collecter ça vite) :**
- 3–5 coachs pilotes triathlon + 2–3 coachs/box Hyrox → verbatims + avant/après (heures gagnées, athlètes facturés).
- Métrique produit : « X min pour analyser une séance vs Y sur Excel ».
- Caution scientifique : profil Hyrox fondé sur l'étude Frontiers in Physiology 2025.
- Histoire fondateur (authentique, à assumer) : passionné data, compagne athlète élite (Emma Terebo) — « on se pousse vers le haut » = le sillage.

**Value themes :**
| Thème | Preuve |
|---|---|
| Analyse décisionnelle | PMC, durabilité, découplage, profil Hyrox, IA |
| Gain de temps | Sync auto, résumé IA, fin d'Excel |
| Revenu du coach | Facturation Stripe intégrée, tarif éditable |
| Hyrox-native | Seul outil dédié, base scientifique |

---

## Goals
**Objectif business (Phase 1) :** acquérir les premiers coachs solo payants (tri + Hyrox), valider le willingness-to-pay et récolter les premiers cas clients.
**Action de conversion clé :** « Essayer la démo » → créer un compte coach → connecter un premier athlète.
**Métriques actuelles :** pré-lancement (produit fonctionnel, Supabase branché, pas encore d'utilisateurs réels).

---

## Annexe — 3 variantes de HERO pour la landing (Phase 1 coachs)

> Design imposé : cockpit sombre, Oswald, teal. « ance » de Sillance en accent.

**Variante A — le moat data (recommandée) :**
- Sur-titre : `COACHS TRIATHLON & HYROX`
- Titre : **« COACHE PAR LA DONNÉE, PAS AU FEELING »**
- Sous-titre : Sillance transforme les fichiers de tes athlètes en analyse décisionnelle — charge, durabilité, Hyrox — et t'encaisse automatiquement. En français.
- CTA : `Essayer la démo` · `Voir l'analyse`

**Variante B — le sillage / la relation :**
- Sur-titre : `LA PLATEFORME COACH-ATHLÈTE`
- Titre : **« PERSONNE NE PROGRESSE SEUL »**
- Sous-titre : Ton athlète avance dans ton sillage. Tu planifies, la donnée revient analysée, tu ajustes — et tu es payé sans y penser.
- CTA : `Essayer la démo` · `Comment ça marche`

**Variante C — le trou Strava / la douleur :**
- Sur-titre : `RÉCUPÈRE LA DATA DE TES ATHLÈTES`
- Titre : **« STRAVA T'A COUPÉ. SILLANCE TE REDONNE LA VUE. »**
- Sous-titre : Garmin, Coros, .FIT — toute la donnée de tes athlètes, analysée pour le coach. Plus Excel, plus de trous. Triathlon & Hyrox.
- CTA : `Essayer la démo` · `Reconnecter mes athlètes`

*Reco : tester A (moat) vs C (douleur Strava) en premier — ce sont les deux angles les plus tranchants pour un coach.*
