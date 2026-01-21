# Guide étape par étape - Évaluation finale

## Étape 1 : Configuration de la base de données testdb2

### 1.1. Créer le script SQL (si non fourni)

Créez un fichier `testdb2.sql` avec le contenu suivant :

```sql
CREATE DATABASE IF NOT EXISTS testdb2;
USE testdb2;

CREATE TABLE IF NOT EXISTS users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL
);

CREATE TABLE IF NOT EXISTS tasks (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    user_id INT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);

-- Insérer des utilisateurs de test
INSERT INTO users (email, password) VALUES
('test@example.com', '1234'),
('alice@gmail.com', 'alice123');

-- Insérer des tâches de test
INSERT INTO tasks (title, user_id) VALUES
('Tâche 1 pour test@example.com', 1),
('Tâche 2 pour test@example.com', 1),
('Tâche 1 pour alice@gmail.com', 2);
```

### 1.2. Importer dans phpMyAdmin

1. Ouvrez phpMyAdmin dans votre navigateur (généralement `http://localhost/phpmyadmin`)
2. Cliquez sur l'onglet "Importer" dans le menu supérieur
3. Cliquez sur "Choisir un fichier" et sélectionnez `testdb2.sql`
4. Cliquez sur "Exécuter" en bas de la page
5. Vérifiez que la base de données `testdb2` apparaît dans la liste de gauche
6. Cliquez sur `testdb2` pour voir les tables `users` et `tasks`
7. **Prenez une capture d'écran** de phpMyAdmin montrant la base de données et ses tables

## Étape 2 : Configuration du fichier .env

### 2.1. Créer le fichier .env dans le dossier server

Créez un fichier `.env` dans le dossier `server/` avec le contenu suivant :

```
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
DB_NAME=testdb2
```

**Note :** Ajustez `DB_USER` et `DB_PASSWORD` selon votre configuration MySQL.

## Étape 3 : Personnaliser les titres avec votre nom

### 3.1. Modifier Login.jsx

Ouvrez `client/src/pages/Login.jsx` et remplacez `[Votre Prénom] [Votre Nom]` par votre vrai prénom et nom à la ligne 24.

### 3.2. Modifier Tasks.jsx

Ouvrez `client/src/pages/Tasks.jsx` et remplacez `[Votre Prénom] [Votre Nom]` par votre vrai prénom et nom à la ligne 26.

## Étape 4 : Installer les dépendances (si nécessaire)

### 4.1. Backend

```bash
cd server
npm install
```

### 4.2. Frontend

```bash
cd client
npm install
```

## Étape 5 : Lancer le backend

### 5.1. Démarrer le serveur

```bash
cd server
node server.js
```

Vous devriez voir :
```
✅ Connecté à MySQL
🚀 Backend lancé sur http://localhost:5000
```

### 5.2. Capture d'écran

**Prenez une capture d'écran** du terminal montrant le lancement du serveur.

## Étape 6 : Lancer le frontend

### 6.1. Ouvrir un nouveau terminal

Dans un **nouveau terminal**, exécutez :

```bash
cd client
npm run dev
```

Vous devriez voir quelque chose comme :
```
  VITE v7.x.x  ready in xxx ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

### 6.2. Ouvrir dans le navigateur

Ouvrez votre navigateur et allez à `http://localhost:5173` (ou le port indiqué).

### 6.3. Capture d'écran

**Prenez une capture d'écran** de la page de connexion dans le navigateur.

## Étape 7 : Tester la connexion avec plusieurs utilisateurs

### 7.1. Test avec test@example.com

1. Entrez l'email : `test@example.com`
2. Entrez le mot de passe : `1234`
3. Cliquez sur "Se connecter"
4. Vous devriez voir la page des tâches avec les tâches de cet utilisateur
5. **Prenez une capture d'écran** de la page des tâches

### 7.2. Test avec alice@gmail.com

1. Déconnectez-vous (vous pouvez fermer l'onglet et rouvrir l'application, ou vider le localStorage)
2. Entrez l'email : `alice@gmail.com`
3. Entrez le mot de passe : `alice123`
4. Cliquez sur "Se connecter"
5. Vérifiez que seules les tâches d'Alice sont affichées (différentes de celles de test@example.com)
6. **Prenez une capture d'écran** de la page des tâches

## Étape 8 : Vérification de l'isolation des données

### 8.1. Vérifier que chaque utilisateur voit uniquement ses tâches

- Connectez-vous avec `test@example.com` → Vous devriez voir uniquement les tâches avec `user_id = 1`
- Connectez-vous avec `alice@gmail.com` → Vous devriez voir uniquement les tâches avec `user_id = 2`

Si les tâches sont différentes pour chaque utilisateur, c'est correct ✅

## Résumé des captures d'écran à fournir

1. ✅ Capture d'écran de phpMyAdmin montrant la base de données `testdb2` et ses tables
2. ✅ Capture d'écran du terminal montrant le lancement du backend (`node server.js`)
3. ✅ Capture d'écran du navigateur montrant la page de connexion (avant connexion)
4. ✅ Capture d'écran du navigateur montrant la page des tâches après connexion réussie avec `test@example.com`
5. ✅ Capture d'écran du navigateur montrant la page des tâches après connexion réussie avec `alice@gmail.com`

## Dépannage

### Erreur de connexion MySQL
- Vérifiez que MySQL/MariaDB est démarré
- Vérifiez les identifiants dans le fichier `.env`
- Vérifiez que la base de données `testdb2` existe

### Erreur CORS
- Assurez-vous que le backend écoute sur le port 5000
- Vérifiez que le frontend pointe vers `http://localhost:5000` dans `api.js`

### Les tâches ne s'affichent pas
- Vérifiez la console du navigateur (F12) pour les erreurs
- Vérifiez que le backend reçoit bien les requêtes
- Vérifiez que les données existent dans la base de données
