# Application de Gestion de Tâches - Évaluation Finale

**Auteur :** Mouhamadou Bah  
**Cours :** Veille technologique [420-VT3-AG]  
**Session :** Automne 2025

## 📋 Description

Application web full-stack de gestion de tâches permettant aux utilisateurs de se connecter et de gérer leurs tâches personnelles. L'application garantit l'isolation des données : chaque utilisateur ne peut voir et gérer que ses propres tâches.

## 🛠️ Technologies utilisées

### Backend
- **Node.js** avec **Express.js**
- **MySQL** (base de données)
- **mysql2** (driver MySQL)
- **CORS** (gestion des requêtes cross-origin)
- **dotenv** (gestion des variables d'environnement)

### Frontend
- **React** (bibliothèque UI)
- **React Router** (routage)
- **Axios** (requêtes HTTP)
- **Vite** (build tool)

## 📁 Structure du projet

```
projetef/
├── client/              # Application React (Frontend)
│   ├── src/
│   │   ├── pages/      # Pages de l'application
│   │   │   ├── Login.jsx
│   │   │   └── Tasks.jsx
│   │   ├── api.js      # Configuration Axios
│   │   └── App.jsx     # Composant principal
│   └── package.json
├── server/              # API Express (Backend)
│   ├── routes/         # Routes API
│   │   ├── auth.js     # Authentification
│   │   └── tasks.js    # Gestion des tâches
│   ├── db.js           # Configuration MySQL
│   ├── server.js       # Point d'entrée du serveur
│   └── package.json
├── testdb2.sql         # Script SQL pour créer la base de données
└── README.md           # Ce fichier
```

## 🚀 Installation et configuration

### Prérequis
- Node.js (v14 ou supérieur)
- MySQL ou MariaDB
- npm ou yarn

### 1. Cloner le dépôt

```bash
git clone https://github.com/[votre-username]/mouhamadou-bah-evaluation-finale.git
cd mouhamadou-bah-evaluation-finale
```

### 2. Configuration de la base de données

1. Importez le script SQL dans phpMyAdmin ou MySQL :
   ```bash
   mysql -u root -p < testdb2.sql
   ```
   Ou importez `testdb2.sql` via phpMyAdmin.

2. Créez un fichier `.env` dans le dossier `server/` :
   ```env
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=votre_mot_de_passe
   DB_NAME=testdb2
   ```

### 3. Installation des dépendances

**Backend :**
```bash
cd server
npm install
```

**Frontend :**
```bash
cd client
npm install
```

## ▶️ Démarrage de l'application

### Lancer le backend

Dans un terminal :
```bash
cd server
node server.js
```

Le serveur démarre sur `http://localhost:5000`

### Lancer le frontend

Dans un autre terminal :
```bash
cd client
npm run dev
```

L'application est accessible sur `http://localhost:5173` (ou le port indiqué par Vite)

## 👤 Comptes de test

L'application inclut deux utilisateurs de test :

1. **test@example.com** / **1234**
2. **alice@gmail.com** / **alice123**

## 🔐 Fonctionnalités

- ✅ Authentification utilisateur (connexion)
- ✅ Gestion des tâches personnelles
- ✅ Isolation des données (chaque utilisateur voit uniquement ses tâches)
- ✅ Interface utilisateur moderne avec React
- ✅ API RESTful avec Express

## 📡 API Endpoints

### Authentification
- `POST /api/auth/login` - Connexion utilisateur
  ```json
  {
    "email": "test@example.com",
    "password": "1234"
  }
  ```

### Tâches
- `GET /api/tasks?user_id={id}` - Récupérer les tâches d'un utilisateur
- `POST /api/tasks` - Créer une nouvelle tâche
  ```json
  {
    "title": "Ma nouvelle tâche",
    "user_id": 1
  }
  ```

## 🧪 Tests

Pour tester l'application :

1. Connectez-vous avec `test@example.com` / `1234`
2. Vérifiez que seules les tâches de cet utilisateur sont affichées
3. Déconnectez-vous et connectez-vous avec `alice@gmail.com` / `alice123`
4. Vérifiez que les tâches affichées sont différentes (isolation des données)

## 📸 Captures d'écran

Les captures d'écran requises pour l'évaluation incluent :
- Capture d'écran de phpMyAdmin montrant la base de données `testdb2` et ses tables
- Capture d'écran du terminal montrant le lancement du backend
- Capture d'écran de la page de connexion dans le navigateur
- Capture d'écran de la page des tâches après connexion avec différents utilisateurs

## 📝 Notes importantes

- Le fichier `.env` ne doit **jamais** être commité dans le dépôt (il est dans `.gitignore`)
- Assurez-vous que MySQL est démarré avant de lancer le backend
- Les mots de passe sont stockés en clair dans cette version de démonstration (non recommandé pour la production)

## 👨‍💻 Auteur

**Mouhamadou Bah**

## 📄 Licence

Ce projet est réalisé dans le cadre d'une évaluation académique.
