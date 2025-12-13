# Solutions détaillées – 10 exercices Git (progressifs)

---

## 🟢 Exercice 1 – Initialisation & premier commit

```bash
mkdir projet-git
cd projet-git
git init
echo "# Mon projet" > README.md
git status
git add README.md
git commit -m "Initial commit : ajout du README"
```

---

## 🟢 Exercice 2 – Suivi de fichiers & .gitignore

```bash
touch index.html app.js config.tmp
```

Créer `.gitignore` :

```bash
echo "config.tmp" > .gitignore
```

```bash
git add index.html app.js .gitignore
git commit -m "Ajout des fichiers applicatifs (config ignorée)"
```

---

## 🟡 Exercice 3 – Modifier le message du dernier commit

```bash
git commit --amend -m "Message corrigé du commit"
```

✔ Aucun nouveau commit créé

---

## 🟡 Exercice 4 – Annuler des changements

### Annuler un fichier non commit

```bash
git restore index.html
```

### Annuler un commit sans perdre les fichiers

```bash
git reset --soft HEAD~1
```

Les fichiers restent en staging

---

## 🟠 Exercice 5 – Feature branch

```bash
git checkout -b feature/login
echo "Login feature" >> app.js
git add app.js
git commit -m "Ajout de la feature login"

git checkout main
git merge feature/login
git branch -d feature/login
```

---

## 🟠 Exercice 6 – Résolution de conflit

```bash
git checkout -b branche-A
echo "Version A" >> app.js
git commit -am "Modif A"

git checkout main
git checkout -b branche-B
echo "Version B" >> app.js
git commit -am "Modif B"
```

```bash
git merge branche-A
# conflit
```

Résolution manuelle dans le fichier puis :

```bash
git add app.js
git commit -m "Résolution du conflit A/B"
```

---

## 🔵 Exercice 7 – Rebase interactif

```bash
git rebase -i HEAD~4
```

Actions possibles :

* `reword` : modifier message
* `squash` : fusionner commits

Résultat : historique propre

---

## 🔵 Exercice 8 – Cherry-pick

```bash
git log --oneline
# copier le hash
git checkout main
git cherry-pick <commit_hash>
```

✔ Uniquement le commit choisi est appliqué

---

## 🔴 Exercice 9 – Hotfix production

```bash
git checkout main
git checkout -b hotfix/critical-bug
```

Correction :

```bash
git commit -am "Hotfix : correction bug critique"
```

```bash
git checkout main
git merge hotfix/critical-bug

git checkout develop
git merge hotfix/critical-bug
```

---

## 🔴 Exercice 10 – Réorganisation avant release

Lister l'historique :

```bash
git log --oneline
```

```bash
git rebase -i HEAD~X
```

Actions typiques :

* `drop` : supprimer commits non désirés
* `squash` : fusionner commits liés
* `reword` : messages clairs

✔ Historique prêt pour release

---

## 🧠 Bonnes pratiques professionnelles

* Commits petits et cohérents
* Messages clairs (verbe à l’infinitif)
* Jamais de `rebase` sur une branche partagée
* Toujours relire `git status`

---

👉 Si tu veux :

* un **PDF imprimable**
* un **workshop Git en entreprise**
* des **exercices DevOps avancés**

Dis-le moi.
