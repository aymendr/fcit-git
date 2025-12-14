1️⃣ Cherry-pick simple (1 commit)

👉 Prendre un commit précis d’une autre branche.

git checkout main
git cherry-pick a1b2c3d


✔️ Le commit a1b2c3d est copié dans main
✔️ Un nouvel hash est créé

2️⃣ Cherry-pick de plusieurs commits

👉 Appliquer plusieurs commits spécifiques

git cherry-pick a1b2c3d e4f5g6h


✔️ Les commits sont appliqués dans l’ordre donné

3️⃣ Cherry-pick d’une plage de commits

👉 Prendre une série de commits consécutifs

git cherry-pick a1b2c3d..d4e5f6g


📌 Attention :

a1b2c3d ❌ exclu

d4e5f6g ✅ inclus

4️⃣ Cherry-pick avec gestion de conflit

Si conflit 👇

git cherry-pick a1b2c3d


❌ Conflit détecté

Résolution :
git status
# corriger les fichiers
git add .
git cherry-pick --continue

Annuler le cherry-pick :
git cherry-pick --abort

5️⃣ Cherry-pick sans commit immédiat

👉 Appliquer les changements sans créer de commit

git cherry-pick -n a1b2c3d


Utile pour :

modifier le code

regrouper plusieurs commits en un seul

6️⃣ Cherry-pick depuis une branche distante

👉 Prendre un commit d’une autre branche

git cherry-pick feature/login


ou un commit précis :

git cherry-pick origin/feature/login~1

7️⃣ Cherry-pick et historique propre (-x)

👉 Ajouter une trace du commit d’origine

git cherry-pick -x a1b2c3d


📄 Message de commit :

(cherry picked from commit a1b2c3d)


✔️ Très recommandé en projet collaboratif

8️⃣ Cas réel : hotfix en production 🔥
git checkout main
git cherry-pick hotfix-branch~0
git push origin main


✔️ Correction rapide
✔️ Pas besoin de merger toute la branche

9️⃣ Cherry-pick après un rebase raté

👉 Récupérer uniquement les bons commits

git cherry-pick <good_commit_1> <good_commit_2>

🔟 Mauvaises pratiques à éviter ❌

🚫 Cherry-pick trop de commits → préfère merge ou rebase
🚫 Cherry-pick sur des branches très divergentes
🚫 Oublier -x en équipe

🧠 Résumé rapide
Situation	Solution
1 commit	git cherry-pick <hash>
Plusieurs commits	git cherry-pick h1 h2
Série de commits	git cherry-pick a..b
Conflit	--continue / --abort
Sans commit	-n
Traçabilité	-x

Si tu veux, je peux te proposer :

📘 10 exercices pratiques sur cherry-pick

🧩 scénarios avancés (prod / release / hotfix)

📄 PDF prêt à partager pour un workshop Git

Dis-moi 👍
