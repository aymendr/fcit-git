# fcit-git

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
2. Modifiez le fichier "index.html" en ajoutant du texte de police <h1>
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


