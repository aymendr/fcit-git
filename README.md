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
2. Modifiez le fichier "index.html" en ajoutant une barre de navigation.
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

Ces exercices devraient vous aider à vous familiariser avec les concepts fondamentaux de Git. N'hésitez pas à les adapter ou à en créer de nouveaux en fonction de vos besoins spécifiques!
