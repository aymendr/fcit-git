# fcit-git

Voici une série de 10 exercices Git avec correction, allant du niveau débutant à avancé, pour vous aider à maîtriser Git progressivement.

### Exercice 1: **Initialiser un dépôt Git**

**Enoncé :**  
Créez un nouveau dossier, initialisez-le comme un dépôt Git et vérifiez son statut.

**Solution :**
```bash
mkdir mon-projet
cd mon-projet
git init
git status
```
Cela crée un nouveau dépôt Git vide.

---

### Exercice 2: **Ajouter un fichier et effectuer un commit**

**Enoncé :**  
Dans le dossier de votre projet, créez un fichier `README.md`, ajoutez du contenu, puis effectuez un commit.

**Solution :**
```bash
echo "# Mon Projet" > README.md
git add README.md
git commit -m "Ajout du fichier README"
```

---

### Exercice 3: **Vérifier l’historique des commits**

**Enoncé :**  
Après avoir effectué plusieurs commits, utilisez la commande pour afficher l’historique des commits de votre dépôt.

**Solution :**
```bash
git log
```

---

### Exercice 4: **Annuler un commit avec `git reset`**

**Enoncé :**  
Après avoir effectué un commit, annulez ce commit tout en conservant les modifications dans votre répertoire de travail.

**Solution :**
```bash
git reset --soft HEAD~1
```
Cette commande revient d’un commit sans supprimer les modifications.

---

### Exercice 5: **Créer une branche et y basculer**

**Enoncé :**  
Créez une nouvelle branche appelée `feature` et basculez dessus.

**Solution :**
```bash
git branch feature
git checkout feature
```
Alternativement, vous pouvez faire les deux en une seule commande :
```bash
git checkout -b feature
```

---

### Exercice 6: **Fusionner une branche dans `main`**

**Enoncé :**  
Fusionnez la branche `feature` dans la branche principale (`main`).

**Solution :**
```bash
git checkout main
git merge feature
```

---

### Exercice 7: **Résoudre un conflit de fusion**

**Enoncé :**  
Supposons que deux branches (`main` et `feature`) modifient la même ligne dans le même fichier. Fusionnez les branches et résolvez le conflit.

**Solution :**
1. Modifiez le même fichier dans les deux branches (`main` et `feature`).
2. Faites un merge de `feature` dans `main` :
   ```bash
   git checkout main
   git merge feature
   ```
3. Git vous indiquera un conflit. Ouvrez le fichier en conflit et modifiez-le manuellement pour résoudre le conflit.
4. Marquez le conflit comme résolu :
   ```bash
   git add <fichier_conflit>
   git commit
   ```

---

### Exercice 8: **Supprimer un fichier et effectuer un commit**

**Enoncé :**  
Supprimez un fichier du répertoire et effectuez un commit pour refléter la suppression.

**Solution :**
```bash
rm fichier_a_supprimer.txt
git add fichier_a_supprimer.txt
git commit -m "Suppression du fichier fichier_a_supprimer.txt"
```

---

### Exercice 9: **Rebaser une branche**

**Enoncé :**  
Supposons que vous avez une branche `feature` et que vous souhaitez appliquer les derniers commits de `main` à votre branche `feature` sans créer un merge commit.

**Solution :**
```bash
git checkout feature
git rebase main
```

---

### Exercice 10: **Travailler avec un dépôt distant (GitHub)**

**Enoncé :**  
Clonez un dépôt distant, créez une nouvelle branche, ajoutez un fichier, effectuez un commit et poussez vos changements sur GitHub.

**Solution :**
1. Clonez le dépôt :
   ```bash
   git clone https://github.com/utilisateur/repository.git
   cd repository
   ```
2. Créez une nouvelle branche :
   ```bash
   git checkout -b nouvelle-branche
   ```
3. Ajoutez un fichier :
   ```bash
   echo "Mon fichier ajouté" > fichier.txt
   git add fichier.txt
   git commit -m "Ajout de fichier.txt"
   ```
4. Poussez vos changements sur GitHub :
   ```bash
   git push origin nouvelle-branche
   ```

---

Ces exercices couvrent une large gamme de scénarios courants dans l'utilisation de Git, du simple suivi de versions à la gestion de branches, de fusions, de résolutions de conflits et de l'interaction avec des dépôts distants.


Voici 10 exercices Git plus avancés, avec des corrections détaillées, pour vous aider à maîtriser des scénarios plus complexes et des fonctionnalités avancées de Git.

### Exercice 1: **Utiliser `git cherry-pick` pour appliquer un commit spécifique d’une autre branche**

**Enoncé :**  
Vous travaillez sur une branche `feature` et vous souhaitez appliquer un commit spécifique de la branche `main` sans fusionner toute la branche. Identifiez un commit particulier et appliquez-le sur votre branche `feature`.

**Solution :**
1. Identifiez le commit sur la branche `main` :
   ```bash
   git log main
   ```
2. Copiez l’identifiant du commit (SHA).
3. Sur votre branche `feature`, appliquez ce commit :
   ```bash
   git checkout feature
   git cherry-pick <commit-sha>
   ```

---

### Exercice 2: **Annuler un commit public avec `git revert`**

**Enoncé :**  
Vous avez déjà poussé un commit sur une branche partagée et vous souhaitez annuler ce commit de manière sécurisée. Utilisez `git revert` pour créer un commit qui annule le précédent.

**Solution :**
1. Identifiez le commit que vous souhaitez annuler :
   ```bash
   git log
   ```
2. Revertissez ce commit :
   ```bash
   git revert <commit-sha>
   ```
3. Poussez les changements sur le dépôt distant :
   ```bash
   git push origin <branche>
   ```

---

### Exercice 3: **Squash commits avant de pousser avec `git rebase -i`**

**Enoncé :**  
Avant de pousser vos changements sur un dépôt distant, vous voulez combiner plusieurs commits en un seul (squash) pour une histoire plus propre.

**Solution :**
1. Effectuez un rebase interactif pour modifier les commits :
   ```bash
   git rebase -i HEAD~n  # où n est le nombre de commits à remonter
   ```
2. Changez `pick` en `squash` (ou `s`) pour les commits que vous souhaitez combiner avec le commit précédent.
3. Sauvegardez et fermez l'éditeur. Git vous demandera de modifier le message de commit.
4. Finalisez le rebase et poussez les changements :
   ```bash
   git push origin <branche> --force
   ```

---

### Exercice 4: **Utiliser `git reflog` pour retrouver des commits disparus**

**Enoncé :**  
Vous avez effectué un `git reset --hard` ou une opération qui a fait disparaître des commits. Utilisez `git reflog` pour retrouver un commit que vous avez perdu.

**Solution :**
1. Affichez l’historique des références avec `git reflog` :
   ```bash
   git reflog
   ```
2. Identifiez l'ID du commit que vous souhaitez récupérer.
3. Utilisez `git checkout` pour revenir à ce commit :
   ```bash
   git checkout <commit-sha>
   ```
4. Si nécessaire, créez une nouvelle branche à partir de ce commit :
   ```bash
   git checkout -b recovery-branch
   ```

---

### Exercice 5: **Créer une branche avec un commit déjà existant sur un autre dépôt**

**Enoncé :**  
Vous souhaitez créer une branche dans un dépôt distant existant, mais vous avez un commit spécifique d’une autre branche du même dépôt que vous souhaitez utiliser comme base.

**Solution :**
1. Cloner le dépôt distant si ce n'est pas déjà fait :
   ```bash
   git clone https://github.com/utilisateur/repository.git
   cd repository
   ```
2. Créez une branche à partir du commit spécifique :
   ```bash
   git checkout -b nouvelle-branche <commit-sha>
   ```

---

### Exercice 6: **Rebase d’une branche distante avec des commits locaux**

**Enoncé :**  
Vous avez fait des commits sur votre branche locale, mais la branche distante a reçu de nouveaux commits. Vous souhaitez appliquer vos commits locaux après les commits distants (rebase).

**Solution :**
1. Récupérez les derniers commits de la branche distante :
   ```bash
   git fetch origin
   ```
2. Rebase votre branche locale sur la branche distante :
   ```bash
   git rebase origin/main
   ```
3. Résolvez les conflits si nécessaire, puis terminez le rebase :
   ```bash
   git rebase --continue
   ```

---

### Exercice 7: **Configurer un fichier `.gitignore` pour ignorer certains fichiers**

**Enoncé :**  
Vous avez des fichiers temporaires ou de configuration qui ne doivent pas être suivis par Git (par exemple, des fichiers générés par l’IDE). Créez un fichier `.gitignore` pour ignorer ces fichiers.

**Solution :**
1. Créez un fichier `.gitignore` dans la racine du projet.
2. Ajoutez les fichiers ou répertoires à ignorer. Par exemple :
   ```bash
   *.log
   *.tmp
   .idea/
   ```
3. Vérifiez que Git ignore ces fichiers avec :
   ```bash
   git status
   ```

---

### Exercice 8: **Submodules - Ajouter un sous-module dans votre dépôt**

**Enoncé :**  
Vous souhaitez ajouter un sous-module Git (un autre dépôt Git) à votre dépôt.

**Solution :**
1. Ajoutez le sous-module :
   ```bash
   git submodule add https://github.com/utilisateur/sous-module.git chemin/du/sous-module
   ```
2. Initialisez et mettez à jour le sous-module :
   ```bash
   git submodule update --init --recursive
   ```

---

### Exercice 9: **Utiliser des hooks Git pour automatiser des actions**

**Enoncé :**  
Vous souhaitez exécuter des tests automatiques avant chaque commit. Configurez un hook Git pour automatiser cette tâche.

**Solution :**
1. Allez dans le répertoire `.git/hooks`.
2. Créez un script `pre-commit` qui lance vos tests avant chaque commit. Par exemple, un script simple pour lancer des tests unitaires :
   ```bash
   #!/bin/sh
   ./run-tests.sh
   if [ $? -ne 0 ]; then
     echo "Tests échoués, commit annulé."
     exit 1
   fi
   ```
3. Rendez ce script exécutable :
   ```bash
   chmod +x .git/hooks/pre-commit
   ```

---

### Exercice 10: **Gestion avancée des branches avec `git merge --no-ff`**

**Enoncé :**  
Vous avez travaillé sur une branche `feature` et vous souhaitez fusionner cette branche dans `main` tout en conservant l’historique de la branche, même si Git pourrait effectuer une fusion fast-forward.

**Solution :**
1. Assurez-vous que vous êtes sur la branche `main` :
   ```bash
   git checkout main
   ```
2. Fusionnez la branche `feature` avec l'option `--no-ff` :
   ```bash
   git merge --no-ff feature
   ```
   Cela garantit qu’un commit de fusion est créé, même si une fusion fast-forward était possible.

---

Ces exercices couvrent des scénarios avancés que vous rencontrerez dans des projets professionnels ou de développement collaboratif. Vous apprendrez à manipuler des outils puissants comme `rebase`, `cherry-pick`, et les hooks, tout en abordant des fonctionnalités comme les submodules, le squash de commits et la gestion des branches complexes.



### Exercice 1: Création d'un nouveau dépôt

**Objectif:** Créer un nouveau dépôt Git local et y ajouter un fichier.

**Instructions:**
1. Ouvrez votre terminal.
2. Créez un nouveau dossier nommé "mon_projet".
3. Accédez à ce dossier nouvellement créé.
4. Initialisez un dépôt Git à l'intérieur de ce dossier.
5. Créez un fichier nommé "index.html".
6. Ajoutez un simple code HTML à ce fichier.
7. Ajoutez ce fichier à la zone de staging.
8. Faites un commit avec le message "Initial commit".

**Correction:**
```bash
mkdir mon_projet
cd mon_projet
git init
touch index.html
# Éditez index.html avec votre éditeur de texte favori
git add index.html
git commit -m "Initial commit"
```

### Exercice 2: Création d'une nouvelle branche

**Objectif:** Créer une nouvelle branche, effectuer des modifications, puis fusionner ces modifications dans la branche principale.

**Instructions:**
1. Créez une nouvelle branche nommée "feature-navbar".
2. Modifiez le fichier "index.html" en ajoutant barre de navigation.
3. Ajoutez ces modifications à la zone de staging.
4. Faites un commit avec le message "Added navbar".
5. Revenez à la branche principale (master).
6. Fusionnez les modifications de la branche "feature-navbar" dans la branche principale.
7. Supprimez la branche "feature-navbar".

**Correction:**
```bash
git checkout -b feature-navbar
# Modifiez index.html pour ajouter une barre de navigation
git add index.html
git commit -m "Added navbar"
git checkout master
git merge feature-navbar
git branch -d feature-navbar
```

### Exercice 3: Travailler avec des remotes

**Objectif:** Travailler avec des dépôts distants (remotes) en ajoutant un dépôt distant, en poussant des modifications et en récupérant les modifications.

**Instructions:**
1. Créez un nouveau dépôt vide sur une plateforme Git (comme GitHub, GitLab, etc.).
2. Associez ce dépôt distant à votre dépôt local.
3. Poussez votre dépôt local vers le dépôt distant.
4. Modifiez le fichier "index.html" localement.
5. Ajoutez ces modifications à la zone de staging.
6. Faites un commit avec le message "Modified index.html".
7. Poussez ces modifications vers le dépôt distant.
8. Récupérez les modifications du dépôt distant dans votre dépôt local.

**Correction:**
```bash
# Créez un nouveau dépôt sur votre plateforme Git et récupérez son URL
git remote add origin <URL_du_dépôt>
git push -u origin master
# Modifiez index.html localement
git add index.html
git commit -m "Modified index.html"
git push origin master
git pull origin master
```

Bien sûr, voici quelques exercices supplémentaires pour renforcer vos compétences Git :

### Exercice 4: Gestion des conflits de fusion

**Objectif:** Comprendre et résoudre les conflits de fusion entre les branches.

**Instructions:**
1. Créez une nouvelle branche nommée "feature-footer".
2. Modifiez le fichier "index.html" en ajoutant un pied de page.
3. Ajoutez ces modifications à la zone de staging et faites un commit avec le message "Added footer".
4. Revenez à la branche principale (master).
5. Modifiez à nouveau le fichier "index.html" sur la branche principale en ajoutant une autre section.
6. Ajoutez ces modifications à la zone de staging et faites un commit avec le message "Added another section".
7. Fusionnez la branche "feature-footer" dans la branche principale.
8. Résolvez les conflits de fusion (s'ils se produisent) dans le fichier "index.html".
9. Validez la fusion en effectuant un commit.

**Correction:**
```bash
git checkout -b feature-footer
# Modifiez index.html pour ajouter un pied de page
git add index.html
git commit -m "Added footer"
git checkout master
# Modifiez index.html sur la branche master pour ajouter une autre section
git add index.html
git commit -m "Added another section"
git merge feature-footer
# Si des conflits surviennent, résolvez-les dans index.html
# Une fois les conflits résolus, faites un commit pour valider la fusion
git commit
```

### Exercice 5: Utilisation des branches distantes

**Objectif:** Travailler avec des branches distantes en récupérant, en fusionnant et en poussant des branches distantes.

**Instructions:**
1. Récupérez toutes les branches distantes.
2. Créez une nouvelle branche locale à partir d'une branche distante.
3. Modifiez le fichier "index.html" dans cette nouvelle branche et faites un commit.
4. Poussez cette nouvelle branche vers le dépôt distant.
5. Fusionnez la branche distante avec la branche principale.

**Correction:**
```bash
git fetch --all
git checkout -b new-branch origin/<nom_de_la_branche_distante>
# Modifiez index.html dans cette nouvelle branche et faites un commit
git add index.html
git commit -m "Modified index.html in new-branch"
git push origin new-branch
git checkout master
git merge new-branch
git push origin master
```

Voici quelques exercices plus avancés pour ceux qui veulent approfondir leurs compétences Git :

### Exercice 6: Utilisation avancée des rebase interactifs

**Objectif:** Comprendre et utiliser le rebase interactif pour réorganiser l'historique des commits.

**Instructions:**
1. Créez une nouvelle branche à partir de la branche principale.
2. Effectuez plusieurs commits avec des modifications différentes.
3. Utilisez le rebase interactif pour fusionner ces commits en un seul ou réorganiser l'ordre des commits.
4. Assurez-vous que chaque modification apportée par les commits est toujours présente dans l'historique.

**Correction:**
```bash
git checkout -b feature-advanced-rebase
# Effectuez plusieurs commits avec différentes modifications
git rebase -i HEAD~<nombre_de_commits>
# Dans l'éditeur qui s'ouvre, suivez les instructions pour fusionner ou réorganiser les commits
# Assurez-vous que chaque modification apportée par les commits est toujours présente
```

### Exercice 7: Utilisation avancée des alias Git

**Objectif:** Créer des alias Git personnalisés pour simplifier les commandes fréquemment utilisées.

**Instructions:**
1. Créez des alias pour des commandes Git couramment utilisées telles que "status", "log", "checkout", etc.
2. Testez vos alias en exécutant ces commandes dans votre terminal.

**Correction:**
```bash
git config --global alias.st status
git config --global alias.lg log
git config --global alias.co checkout
# Testez les alias
git st
git lg
git co <nom_de_la_branche>
```

### Exercice 8: Utilisation avancée des hooks Git

**Objectif:** Utiliser les hooks Git pour automatiser des tâches spécifiques avant ou après certaines actions Git.

**Instructions:**
1. Créez un hook pré-commit qui vérifie la syntaxe de votre code (par exemple, linting).
2. Créez un hook post-merge qui effectue des actions spécifiques après une fusion.
3. Testez vos hooks en effectuant les actions correspondantes dans votre dépôt.

**Correction:**
Créez des scripts exécutables dans le répertoire `.git/hooks/` de votre dépôt, tels que `pre-commit` et `post-merge`, qui effectuent les actions souhaitées.

## Git REBASE

Le rebase interactif est une fonctionnalité puissante de Git qui permet de réécrire l'historique des commits de manière interactive. Contrairement à un rebase standard, où Git réapplique simplement les commits d'une branche sur une autre, le rebase interactif donne à l'utilisateur un contrôle total sur chaque commit à réappliquer, ainsi que sur l'ordre dans lequel ils sont appliqués.

Voici comment utiliser le rebase interactif :

1. **Commencez par un rebase interactif :** Lancez le rebase interactif en utilisant la commande `git rebase -i <commit>` où `<commit>` est le dernier commit que vous souhaitez réappliquer (généralement, cela sera le commit juste avant celui que vous voulez modifier).

2. **Choisissez les commits à modifier :** Une fois que vous lancez le rebase interactif, Git ouvrira un éditeur de texte avec une liste des commits à réappliquer. Chaque ligne commencera par le mot "pick" suivi du code de hachage (hash) et du message de chaque commit.

3. **Modifiez l'ordre des commits :** Vous pouvez réorganiser l'ordre des commits simplement en réorganisant les lignes dans l'éditeur de texte. Ceci est utile si vous souhaitez modifier l'ordre chronologique des commits.

4. **Combinez des commits :** Si vous souhaitez fusionner plusieurs commits en un seul, changez le mot "pick" en "squash" ou simplement en "s" pour les commits que vous voulez combiner. Cela vous permet de condenser plusieurs commits en un seul tout en conservant leurs modifications.

5. **Modifier les messages de commit :** Vous pouvez également modifier les messages de commit en changeant le texte après "pick" pour chaque commit.

6. **Sauvegardez et quittez l'éditeur :** Une fois que vous avez terminé d'éditer la liste des commits, sauvegardez et quittez l'éditeur. Git appliquera alors les modifications selon vos instructions.

7. **Résolvez les conflits (si nécessaire) :** Si des conflits surviennent pendant le processus de rebase interactif, Git marquera le rebase en pause et vous donnera l'opportunité de résoudre ces conflits. Après avoir résolu les conflits, vous pouvez continuer le rebase en utilisant la commande `git rebase --continue`.

8. **Terminez le rebase :** Une fois que vous avez terminé de réécrire l'historique des commits, Git finalisera le rebase et appliquera les modifications. Si tout se passe bien, vous aurez un historique de commits réorganisé et édité selon vos spécifications.

Le rebase interactif est une technique avancée et puissante, mais elle peut également être risquée si elle est mal utilisée. Il est important de comprendre que le rebase modifie l'historique des commits, ce qui peut entraîner des problèmes si vous travaillez en collaboration avec d'autres développeurs sur le même dépôt. Il est recommandé de n'utiliser le rebase interactif que sur des branches locales et de ne pas réécrire l'historique des commits sur des branches partagées.

## Voici quelques exercices axés sur l'utilisation de git rebase :

### Exercice 1: Rebase interactif pour combiner des commits

**Objectif:** Utiliser le rebase interactif pour combiner plusieurs commits en un seul.

**Instructions:**
1. Créez une nouvelle branche à partir de la branche principale.
2. Effectuez au moins cinq commits avec des messages clairs pour chaque modification.
3. Utilisez le rebase interactif pour combiner les trois derniers commits en un seul.
4. Vérifiez l'historique des commits pour confirmer que les commits ont été combinés avec succès.

**Correction:**
```bash
git checkout -b feature-rebase-exercise1
# Effectuez au moins cinq commits avec des modifications distinctes
git rebase -i HEAD~5
# Dans l'éditeur interactif, remplacez "pick" par "squash" ou "s" pour les commits que vous souhaitez combiner
# Suivez les instructions pour finaliser le rebase
git log --oneline
```

### Exercice 2: Rebase pour réappliquer des commits sur la branche principale

**Objectif:** Utiliser le rebase pour réappliquer des commits sur la branche principale après avoir récupéré les dernières modifications.

**Instructions:**
1. Créez une nouvelle branche à partir de la branche principale.
2. Effectuez quelques commits sur cette nouvelle branche.
3. Pendant que vous êtes sur cette branche, allez sur la branche principale et effectuez quelques commits.
4. Revenez à votre branche et utilisez le rebase pour réappliquer vos commits sur la branche principale mise à jour.

**Correction:**
```bash
git checkout -b feature-rebase-exercise2
# Effectuez quelques commits sur cette nouvelle branche
git checkout master
# Effectuez quelques commits sur la branche principale
git checkout feature-rebase-exercise2
git rebase master
```

### Exercice 3: Rebase pour réorganiser les commits

**Objectif:** Utiliser le rebase pour réorganiser l'ordre des commits dans votre historique.

**Instructions:**
1. Créez une nouvelle branche à partir de la branche principale.
2. Effectuez plusieurs commits avec différentes modifications.
3. Utilisez le rebase interactif pour réorganiser l'ordre des commits.
4. Vérifiez l'historique des commits pour confirmer que les commits ont été réorganisés avec succès.

**Correction:**
```bash
git checkout -b feature-rebase-exercise3
# Effectuez plusieurs commits avec différentes modifications
git rebase -i HEAD~<nombre_de_commits>
# Dans l'éditeur interactif, réorganisez l'ordre des commits selon vos besoins
# Suivez les instructions pour finaliser le rebase
git log --oneline
```


# Lab Git Avancé : Gestion des branches, des sous-modules, des conflits et de l’historique

Ce laboratoire va vous permettre de maîtriser plusieurs aspects avancés de Git, allant de la gestion des branches complexes, à l’utilisation des sous-modules, en passant par la résolution de conflits, la réécriture de l'historique et l'automatisation via des hooks. Il est conçu pour simuler un projet réel avec plusieurs contributeurs travaillant sur des fonctionnalités différentes et devant gérer des situations courantes mais complexes.

---

### Contexte du projet

Vous travaillez sur un projet appelé **"SuperApp"** avec plusieurs collègues. Le projet a plusieurs fonctionnalités en développement simultanément, et vous devez gérer les branches, résoudre des conflits, maintenir un historique propre et automatiser certaines actions.

Le dépôt contient deux composants principaux :  
1. **Backend** - Un ensemble d'API écrites en Node.js.
2. **Frontend** - Un client web construit avec React.

En plus de ces deux composants, vous utilisez un sous-module Git pour inclure une bibliothèque de gestion des utilisateurs provenant d'un autre dépôt.

---

### Objectifs du lab

1. **Cloner le projet et initialiser l’environnement de travail**
2. **Gérer les branches et effectuer des fusions avancées**
3. **Utiliser `git cherry-pick` pour appliquer des commits spécifiques**
4. **Résoudre des conflits complexes**
5. **Manipuler l’historique avec `git rebase`, `git reset`, et `git reflog`**
6. **Utiliser des sous-modules pour gérer les dépendances**
7. **Configurer un hook Git pour automatiser des tests**
8. **Pousser et synchroniser les modifications avec un dépôt distant**

---

### Étape 1: Cloner le dépôt et initialiser l’environnement de travail

1. **Cloner le dépôt principal (superapp) depuis GitHub :**

   ```bash
   git clone https://github.com/votre-utilisateur/superapp.git
   cd superapp
   ```

2. **Vérifiez que vous êtes sur la branche `main` :**

   ```bash
   git checkout main
   ```

3. **Vérifiez l'état du dépôt :**

   ```bash
   git status
   ```

   Vous devriez voir un projet avec plusieurs fichiers et dossiers, dont `backend/`, `frontend/` et un sous-module.

---

### Étape 2: Gérer les branches et effectuer des fusions avancées

#### 2.1 Créer des branches pour les nouvelles fonctionnalités

1. **Créez une branche `feature/backend-auth` pour travailler sur l'authentification du backend :**

   ```bash
   git checkout -b feature/backend-auth
   ```

2. **Ajoutez une nouvelle fonctionnalité au backend (par exemple, un nouveau fichier `auth.js`) :**

   ```bash
   echo "module.exports = { authenticate: function() { return true; } }" > backend/auth.js
   git add backend/auth.js
   git commit -m "Ajout du module d'authentification au backend"
   ```

3. **Créez une branche `feature/frontend-login` pour travailler sur la page de connexion dans le frontend :**

   ```bash
   git checkout main
   git checkout -b feature/frontend-login
   ```

4. **Ajoutez une nouvelle page de connexion dans le frontend (par exemple, un fichier `LoginPage.jsx`) :**

   ```bash
   echo "import React from 'react'; export default function LoginPage() { return <div>Login</div>; }" > frontend/LoginPage.jsx
   git add frontend/LoginPage.jsx
   git commit -m "Ajout de la page de connexion dans le frontend"
   ```

#### 2.2 Fusionner les branches avec `git merge`

1. **Fusionnez `feature/frontend-login` dans `main` :**

   ```bash
   git checkout main
   git merge feature/frontend-login
   ```

   Résolvez les éventuels conflits et effectuez un commit de fusion si nécessaire.

2. **Fusionnez `feature/backend-auth` dans `main` :**

   ```bash
   git checkout main
   git merge feature/backend-auth
   ```

---

### Étape 3: Utiliser `git cherry-pick` pour appliquer des commits spécifiques

Supposons que vous ayez une branche `feature/payment` avec un commit que vous voulez appliquer sur `feature/backend-auth`.

1. **Créez une branche `feature/payment` :**

   ```bash
   git checkout -b feature/payment
   ```

2. **Ajoutez un commit sur `feature/payment` :**

   ```bash
   echo "module.exports = { processPayment: function() { return 'Payment processed'; } }" > backend/payment.js
   git add backend/payment.js
   git commit -m "Ajout du module de traitement des paiements"
   ```

3. **Vous voulez appliquer ce commit sur `feature/backend-auth`.**
   
   D'abord, identifiez le SHA du commit :

   ```bash
   git log
   ```

4. **Sur la branche `feature/backend-auth`, appliquez le commit avec `git cherry-pick` :**

   ```bash
   git checkout feature/backend-auth
   git cherry-pick <commit-sha>
   ```

5. **Résolvez les conflits (si nécessaire) et validez la fusion.**

---

### Étape 4: Résoudre des conflits complexes

1. **Simulez un conflit :**  
   Modifiez un même fichier dans deux branches différentes, par exemple, `frontend/LoginPage.jsx`.

   - Sur `feature/frontend-login`, ajoutez une ligne dans le fichier `LoginPage.jsx`.
   - Sur `feature/backend-auth`, modifiez également ce même fichier.

2. **Fusionnez les deux branches et résolvez le conflit :**

   ```bash
   git checkout main
   git merge feature/frontend-login
   git merge feature/backend-auth
   ```

   Git devrait vous signaler un conflit. Ouvrez le fichier en conflit, résolvez le conflit et effectuez un commit de résolution.

---

### Étape 5: Manipuler l’historique avec `git rebase`, `git reset`, et `git reflog`

#### 5.1 Rebaser une branche

1. **Supposons que `feature/payment` soit en retard par rapport à `main`. Utilisez `git rebase` pour appliquer les commits de `main` à `feature/payment` :**

   ```bash
   git checkout feature/payment
   git fetch origin
   git rebase origin/main
   ```

   Résolvez les conflits s'il y en a.

#### 5.2 Annuler un commit avec `git reset`

1. **Vous avez ajouté un commit indésirable, revenez à un état précédent sans perdre vos changements locaux :**

   ```bash
   git reset --soft HEAD~1
   ```

2. **Si vous souhaitez également supprimer les changements dans le répertoire de travail :**

   ```bash
   git reset --hard HEAD~1
   ```

#### 5.3 Utiliser `git reflog` pour récupérer des commits disparus

1. **Vous avez supprimé des commits par erreur. Utilisez `git reflog` pour les retrouver et revenir à un état antérieur :**

   ```bash
   git reflog
   git checkout <commit-sha>
   ```

---

### Étape 6: Utiliser des sous-modules pour gérer les dépendances

1. **Ajoutez un sous-module pour la gestion des utilisateurs (par exemple un dépôt appelé `user-management-lib`) :**

   ```bash
   git submodule add https://github.com/organisme/user-management-lib.git lib/user-management
   git submodule update --init --recursive
   ```

2. **Modifiez votre code pour utiliser la bibliothèque du sous-module (par exemple, intégrer la gestion des utilisateurs dans le backend).**

3. **Pour pousser vos modifications, n'oubliez pas de pousser le sous-module :**

   ```bash
   git add lib/user-management
   git commit -m "Ajout du sous-module pour la gestion des utilisateurs"
   git push origin main
   ```

---

### Étape 7: Configurer un hook Git pour automatiser des tests

1. **Créez un hook `pre-commit` pour exécuter les tests avant chaque commit :**

   Allez dans `.git/hooks/pre-commit` et créez un script comme suit :

   ```bash
   #!/bin/sh
   npm run test
   if [ $? -ne 0 ]; then
     echo "Tests échoués, commit annulé."
     exit 1
   fi
   ```

2. **Rendez ce script exécutable :**

   ```bash
   chmod +x .git/hooks/pre-commit
   ```

---

### Étape 8: Pousser et synchroniser les modifications avec un dépôt distant

1. **Poussez toutes vos modifications sur le dépôt distant :**

   ```bash
   git push origin main
   ```

2. **Si vous avez des branches distantes, assurez-vous qu'elles sont bien mises à jour :**

   ```bash
   git push origin feature/backend-auth
   git push origin feature/frontend-login
   ```

---

### Conclusion

Ce lab couvre une série de tâches avancées dans Git : gestion des branches, résolution de conflits, manipulation de l’historique, utilisation des sous-modules, automatisation des tests, et gestion des hooks. Ces compétences vous permettront de gérer des projets complexes avec plusieurs développeurs et de maintenir un historique propre tout en intégrant

# Exercice Avancé : Utilisation de `git rebase -i` (Rebase interactif)

Cet exercice vous permettra de comprendre et de maîtriser l’utilisation avancée de **`git rebase -i`** (rebase interactif), une fonctionnalité puissante pour manipuler l’historique des commits dans Git. Vous apprendrez à réécrire l’historique, à combiner des commits, à réorganiser les commits, et à résoudre les conflits lors d'un rebase.

### Contexte
Vous travaillez sur un projet avec plusieurs commits, mais l'historique des commits est désordonné. Il y a des commits inutiles, des messages de commit peu clairs, et certains commits devraient être combinés pour avoir un historique plus propre. Vous allez utiliser `git rebase -i` pour réorganiser et nettoyer l’historique des commits.

### Objectifs

- Réorganiser les commits.
- Fusionner (squash) plusieurs commits en un seul.
- Modifier les messages de commit.
- Supprimer des commits inutiles.
- Corriger des erreurs dans les commits précédents.
- Résoudre des conflits pendant un rebase interactif.

---

### Préparation de l'exercice

Avant de commencer, il vous faut un projet Git avec plusieurs commits. Vous pouvez créer un petit projet en utilisant les étapes suivantes :

1. **Initialiser un dépôt Git local :**
   ```bash
   mkdir rebase-lab
   cd rebase-lab
   git init
   ```

2. **Créer des commits pour simuler un historique chaotique :**

   ```bash
   # Créer un fichier initial et committer
   echo "Initial commit" > file.txt
   git add file.txt
   git commit -m "Initial commit"

   # Ajouter une fonctionnalité A (petit changement)
   echo "Feature A" >> file.txt
   git add file.txt
   git commit -m "Feature A"

   # Ajouter une fonctionnalité B (petit changement)
   echo "Feature B" >> file.txt
   git add file.txt
   git commit -m "Feature B"

   # Ajouter une fonctionnalité C (petit changement)
   echo "Feature C" >> file.txt
   git add file.txt
   git commit -m "Feature C"

   # Erreur dans le message de commit, on va la corriger
   git commit --amend -m "Correction du message pour Feature C"
   
   # Faire un commit sans réelle modification
   git commit --allow-empty -m "Commit inutile"

   # Ajouter une fonctionnalité D (petit changement)
   echo "Feature D" >> file.txt
   git add file.txt
   git commit -m "Feature D"
   ```

   À ce stade, vous avez 6 commits dans votre historique avec des changements qui peuvent être optimisés.

---

### Étape 1: Lancer un Rebase Interactif

1. **Afficher l’historique des commits :**
   ```bash
   git log --oneline
   ```

   Vous devriez voir quelque chose comme ceci :

   ```
   <sha1> Feature D
   <sha1> Commit inutile
   <sha1> Correction du message pour Feature C
   <sha1> Feature C
   <sha1> Feature B
   <sha1> Feature A
   <sha1> Initial commit
   ```

2. **Lancer un rebase interactif sur les 6 derniers commits :**
   ```bash
   git rebase -i HEAD~6
   ```

   Cela va ouvrir un éditeur de texte avec une liste de commits :

   ```
   pick <sha1> Feature D
   pick <sha1> Commit inutile
   pick <sha1> Correction du message pour Feature C
   pick <sha1> Feature C
   pick <sha1> Feature B
   pick <sha1> Feature A
   pick <sha1> Initial commit
   ```

   - Chaque ligne commence par un mot-clé (`pick`).
   - `pick` signifie que vous gardez ce commit tel quel.

---

### Étape 2: Manipuler les commits avec `git rebase -i`

Vous allez maintenant réorganiser, fusionner, modifier, et supprimer certains commits pour avoir un historique plus propre.

#### 2.1 Réorganiser les commits

Vous souhaitez que le commit "Feature A" vienne après "Feature C". Pour ce faire, changez l’ordre des lignes :

```
pick <sha1> Feature D
pick <sha1> Commit inutile
pick <sha1> Correction du message pour Feature C
pick <sha1> Feature A
pick <sha1> Feature B
pick <sha1> Initial commit
```

En réorganisant les commits, vous pouvez déplacer le commit "Feature A" après "Feature C".

#### 2.2 Fusionner des commits avec `squash` (ou `s`)

Vous avez deux commits inutiles que vous voulez combiner : **"Commit inutile"** et **"Correction du message pour Feature C"**. Pour les combiner, remplacez `pick` par `squash` (ou `s`) sur les lignes que vous voulez fusionner.

```
pick <sha1> Feature D
squash <sha1> Commit inutile
pick <sha1> Correction du message pour Feature C
pick <sha1> Feature A
pick <sha1> Feature B
pick <sha1> Initial commit
```

Cela va appliquer le contenu de "Commit inutile" dans le commit suivant, tout en vous permettant de modifier le message de commit.

#### 2.3 Modifier un commit avec `edit`

Vous réalisez qu'il y a un problème dans **"Feature B"** et que vous souhaitez le corriger. Vous pouvez choisir de l'éditer en utilisant `edit` :

```
pick <sha1> Feature D
squash <sha1> Commit inutile
pick <sha1> Correction du message pour Feature C
pick <sha1> Feature A
edit <sha1> Feature B
pick <sha1> Initial commit
```

Cela vous permettra de modifier le commit **"Feature B"** avant de poursuivre le rebase.

---

### Étape 3: Appliquer le rebase

Après avoir effectué vos modifications, **enregistrez et fermez l’éditeur** pour lancer le rebase.

#### 3.1 Résoudre les conflits

Pendant le rebase, Git pourrait rencontrer des conflits, surtout si des fichiers ont été modifiés dans plusieurs commits. Si cela se produit :

1. Git vous alertera et vous demandera de résoudre les conflits.
2. Ouvrez les fichiers en conflit et résolvez-les manuellement.
3. Une fois les conflits résolus, ajoutez les fichiers modifiés :

   ```bash
   git add <fichier_conflit>
   ```

4. Continuez le rebase :

   ```bash
   git rebase --continue
   ```

#### 3.2 Modifier un commit avec `edit`

Si vous avez choisi d’éditer le commit **"Feature B"**, Git s’arrêtera et vous permettra de modifier ce commit. Vous pouvez maintenant apporter les modifications nécessaires dans les fichiers concernés, puis effectuer un commit avec :

```bash
git commit --amend
```

Une fois la modification terminée, continuez le rebase :

```bash
git rebase --continue
```

---

### Étape 4: Finaliser et nettoyer l’historique

Après avoir terminé le rebase, vous aurez un historique plus propre avec les modifications suivantes :

- **Réorganisation des commits** : "Feature A" se trouve après "Feature C".
- **Fusion des commits** : "Commit inutile" et "Correction du message pour Feature C" ont été fusionnés en un seul commit.
- **Modification d’un commit** : Vous avez corrigé le commit "Feature B".

1. Vérifiez l’historique des commits à l’aide de :

   ```bash
   git log --oneline
   ```

   Vous devriez voir quelque chose comme :

   ```
   <sha1> Feature D
   <sha1> Feature A
   <sha1> Feature C
   <sha1> Feature B (modifié)
   <sha1> Initial commit
   ```

2. Si vous êtes satisfait du résultat, poussez les modifications sur le dépôt distant. Si vous avez réécrit l’historique (par exemple, en utilisant `--amend` ou `rebase`), vous devrez peut-être utiliser l’option `--force` :

   ```bash
   git push origin main --force
   ```

---

### Conclusion

Cet exercice vous a permis de comprendre comment utiliser **`git rebase -i`** pour effectuer des modifications avancées sur l’historique des commits. Vous avez appris à réorganiser les commits, à fusionner des commits, à modifier des messages de commit, à supprimer des commits inutiles et à résoudre des conflits pendant un rebase. Ces compétences sont essentielles pour garder un historique propre et faciliter la collaboration dans des projets complexes.
