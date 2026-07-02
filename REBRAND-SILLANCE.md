# Rebrand PairForm → Sillance — note de passation devs

**Date : 02/07/2026.** Le produit s'appelle désormais **Sillance** (racine « sillage » — voir `SILLANCE-LE-NOM.md` pour la justification du nom).

## Ce qui a été fait

### Front-end (ce dépôt, `~/Downloads/files_extracted`)
- **Tout le texte de marque** « PairForm / PAIRFORM » → **Sillance / SILLANCE** (titres, `<title>`, footers, notifications, commentaires, wordmarks coupés par des balises `<b>`/`<span>`).
- **URLs** `pairform.app` → `sillance.app`.
- **Fichiers renommés** (via `git mv`, historique conservé) + toutes les références (`<script src>`, liens, imports, docs) mises à jour :
  - `pairform-client.js` → `sillance-client.js`
  - `pairform-integration.js` → `sillance-integration.js`
  - `pairform-fit.js` → `sillance-fit.js`
  - `pairform-club.html` → `sillance-club.html`
  - `pairform-demo.html` → `sillance-demo.html`
  - `pairform-review.html` → `sillance-review.html`
  - `pairform-logos*.html`, `pairform-logo-10-blanc.html` → `sillance-*`
  - `pairform-setup.sql` → `sillance-setup.sql`
  - `PAIRFORM-AI-ADDON-PLAN.md` → `SILLANCE-AI-ADDON-PLAN.md`
- **Logo** : nouvelle planche `sillance-logo.html` (4 concepts sur le thème « sillage », reco = concept 1). L'ancien logo « Orbit » est abandonné.
- Vérifs : `node --check` OK sur les 3 JS ; `<script src>` résolvent ; rendu headless OK.

### Back-end (`~/pairform-backend`, dépôt séparé)
- Tout le texte « PairForm » → « Sillance » (commentaires, docs, **noms de produits Stripe visibles par le client**).
- `web/pairform-*.js` renommés en `web/sillance-*.js` (+ refs DEPLOY.md / README.md).
- Valeurs techniques alignées : `STRAVA_VERIFY_TOKEN` → `sillance-strava`, `config.toml` project_id → `sillance`, emails de test `@sillance.test`.
- `node --check` OK ; TS/SQL non compilés (deno absent) — à valider au déploiement.

## Décisions ouvertes (pour Rowan / devs)
1. **Choix du concept de logo** parmi les 4 de `sillance-logo.html` (reco : concept 1 « sillage en V »), puis intégration en favicon + en-tête des apps.
2. **Nom du dépôt / dossier back-end** : le dossier `~/pairform-backend` n'a **pas** été renommé (chemins de dev). Une seule mention subsiste dans `sillance-demo.html` (lien vers `~/pairform-backend/DEPLOY.md`). À trancher au moment de créer les repos Git côté équipe.
3. **Domaines à acheter** (`.com/.io/.co/.fr/.app/.ai` libres) + **dépôt de marque INPI** (classes 9/41/42).
