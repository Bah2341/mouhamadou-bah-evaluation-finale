# Guide : Créer le dépôt GitHub et pousser le code

## Étape 1 : Créer le dépôt sur GitHub

1. Allez sur [GitHub.com](https://github.com) et connectez-vous à votre compte
2. Cliquez sur le bouton **"+"** en haut à droite, puis sélectionnez **"New repository"**
3. Configurez le dépôt :
   - **Repository name :** `mouhamadou-bah-evaluation-finale`
   - **Description :** `Application de gestion de tâches - Évaluation finale 420-VT3-AG`
   - **Visibilité :** Sélectionnez **Public** (comme demandé)
   - **NE COCHEZ PAS** "Add a README file" (nous en avons déjà un)
   - **NE COCHEZ PAS** "Add .gitignore" (nous en avons déjà un)
   - **NE COCHEZ PAS** "Choose a license"
4. Cliquez sur **"Create repository"**

## Étape 2 : Initialiser Git dans votre projet (si pas déjà fait)

Ouvrez un terminal dans le dossier racine du projet (`projetef`) et exécutez :

```bash
# Vérifier si Git est déjà initialisé
git status

# Si vous obtenez une erreur "not a git repository", initialisez Git :
git init
```

## Étape 3 : Ajouter tous les fichiers au dépôt

```bash
# Ajouter tous les fichiers (sauf ceux dans .gitignore)
git add .

# Vérifier les fichiers qui seront commités
git status
```

**Important :** Vérifiez que les fichiers suivants NE sont PAS dans la liste :
- `node_modules/` (dans client/ et server/)
- `.env` (dans server/)
- `dist/` ou `build/`

## Étape 4 : Créer le premier commit

```bash
git commit -m "Initial commit - Application de gestion de tâches"
```

## Étape 5 : Connecter le dépôt local au dépôt GitHub

```bash
# Remplacez [votre-username] par votre nom d'utilisateur GitHub
git remote add origin https://github.com/[votre-username]/mouhamadou-bah-evaluation-finale.git

# Vérifier que la connexion est établie
git remote -v
```

**Note :** Si vous utilisez SSH au lieu de HTTPS, utilisez :
```bash
git remote add origin git@github.com:[votre-username]/mouhamadou-bah-evaluation-finale.git
```

## Étape 6 : Pousser le code vers GitHub

```bash
# Pousser le code vers la branche main (ou master selon votre configuration)
git branch -M main
git push -u origin main
```

**Si vous êtes invité à vous authentifier :**
- Pour HTTPS : Utilisez un **Personal Access Token** (pas votre mot de passe)
  - Allez dans GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
  - Créez un nouveau token avec les permissions `repo`
  - Utilisez ce token comme mot de passe
- Pour SSH : Assurez-vous que votre clé SSH est configurée sur GitHub

## Étape 7 : Vérifier sur GitHub

1. Rafraîchissez la page de votre dépôt sur GitHub
2. Vous devriez voir :
   - Le fichier `README.md` affiché en bas de la page
   - Tous vos fichiers dans l'onglet "Code"
   - Le commit "Initial commit" dans l'onglet "Commits"

## Étape 8 : Prendre la capture d'écran

Prenez une capture d'écran de votre dépôt GitHub montrant :
- ✅ Le README.md visible en bas de la page
- ✅ Les commits visibles (onglet "Commits" ou historique)
- ✅ La structure des fichiers dans l'onglet "Code"

**Conseil :** Prenez la capture d'écran de manière à voir :
- L'URL du dépôt (ex: `github.com/[username]/mouhamadou-bah-evaluation-finale`)
- Le README affiché
- Au moins un commit dans l'historique

## Étape 9 : Copier le lien du dépôt

1. Cliquez sur le bouton vert **"Code"** sur la page de votre dépôt
2. Copiez l'URL HTTPS (ex: `https://github.com/[username]/mouhamadou-bah-evaluation-finale.git`)
3. Collez ce lien dans votre document Word d'évaluation

## Commandes Git utiles (référence)

```bash
# Voir l'état des fichiers
git status

# Voir l'historique des commits
git log

# Ajouter un fichier spécifique
git add nom-du-fichier

# Créer un nouveau commit
git commit -m "Description du changement"

# Pousser les changements vers GitHub
git push

# Récupérer les changements depuis GitHub
git pull
```

## Dépannage

### Erreur : "remote origin already exists"
```bash
# Supprimer l'ancienne connexion
git remote remove origin
# Puis refaire l'étape 5
```

### Erreur : "failed to push some refs"
```bash
# Récupérer d'abord les changements (si le dépôt n'était pas vide)
git pull origin main --allow-unrelated-histories
# Puis pousser
git push -u origin main
```

### Erreur d'authentification
- Vérifiez que vous utilisez un Personal Access Token (pas votre mot de passe)
- Ou configurez SSH pour GitHub

## Structure finale attendue sur GitHub

Votre dépôt devrait contenir :
```
mouhamadou-bah-evaluation-finale/
├── .gitignore
├── README.md
├── GUIDE_ETAPES.md
├── GUIDE_GITHUB.md
├── testdb2.sql
├── client/
│   ├── src/
│   ├── package.json
│   └── ...
└── server/
    ├── routes/
    ├── package.json
    └── ...
```

**Note :** Les dossiers `node_modules/` et le fichier `.env` ne doivent **PAS** apparaître sur GitHub (grâce au `.gitignore`).
