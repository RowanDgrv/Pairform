# Sillance — ce qu'il te reste à faire (version simple)

## Où on en est
Le site **marche déjà en démo** (tu peux cliquer partout, tout s'affiche).
Pour le lancer **pour de vrai** (vrais comptes utilisateurs, vrais paiements),
il manque **3 comptes** que toi seul peux créer (parce qu'il faut ton identité
et ta carte). **Tout le reste (le code, les branchements, les textes légaux,
les tests), c'est moi qui le fais.**

---

## CE QUE TOI TU FAIS — 3 choses, dans l'ordre

### 1️⃣ La base de données → **Supabase** (gratuit, 5 min) — À FAIRE EN PREMIER
C'est le « classeur » qui stocke les utilisateurs, les clubs, les séances.
1. Va sur **supabase.com** → bouton **« Start your project »** → connecte-toi (Google ou GitHub).
2. Clique **« New project »**.
   - Nom : `sillance`
   - Database Password : clique **Generate** puis **NOTE-LE quelque part**.
   - Region : choisis **Europe** (West EU / Ireland ou Frankfurt).
   - Clique **Create new project**, attends ~2 min.
3. En haut à gauche : **Settings** (roue ⚙️) → **API**.
4. Copie **2 valeurs** : « **Project URL** » et « **anon public** ».
5. **Colle-les-moi ici.** → Je m'occupe de tout brancher.

### 2️⃣ Le statut pour être payé → **Auto-entrepreneur** (gratuit)
Obligatoire pour encaisser de l'argent légalement.
- Va sur **autoentrepreneur.urssaf.fr** → « Créer mon auto-entreprise ».
- ~15 min, gratuit. (Tu peux le faire cette semaine, pas urgent aujourd'hui.)

### 3️⃣ Les paiements → **Stripe** (gratuit à créer)
- Va sur **stripe.com** → « Sign up » → remplis les infos de ton auto-entreprise.
- La vérification prend quelques jours (commence-la après le 1️⃣).
- Quand c'est prêt, tu me donnes les clés → je branche.

---

## CE QUE MOI JE FAIS (tu n'as rien à toucher)
- Brancher la base, mettre en ligne les fonctions, connecter les paiements.
- Écrire les **textes légaux** (mentions, conditions de vente, confidentialité, cookies).
- Tester que tout marche, que personne ne voit les données d'un autre.
- La page d'accueil, la grille, les filtres : **déjà faits et en ligne.**

---

## 👉 MAINTENANT, fais juste le 1️⃣ (Supabase) et colle-moi les 2 valeurs.
Le reste attend. On avance **une étape à la fois.**
