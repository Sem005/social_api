# Social API

API REST simple pour une application de reseau social, construite avec Node.js, Express et MongoDB.

Elle permet de gerer :

- l'inscription et la connexion des utilisateurs
- la consultation, la modification et la suppression de profils
- le suivi et le desabonnement entre utilisateurs
- la creation et la gestion de publications
- les likes et le fil d'actualite d'un utilisateur

## Stack technique

- Node.js
- Express
- MongoDB avec Mongoose
- Nodemon pour le lancement en developpement

## Prerequis

- Node.js
- npm
- une instance MongoDB accessible depuis l'application

## Installation

```bash
npm install
```

## Configuration

L'application lit ses variables d'environnement depuis un fichier `.env` place a la racine du projet.

Exemple :

```env
PORT=5000
MONGO_DB=mongodb://localhost:27017/social-api
```

Variables utilisees :

- `PORT` : port d'ecoute du serveur Express
- `MONGO_DB` : chaine de connexion MongoDB

## Demarrage

```bash
npm start
```

Le script `start` lance `nodemon index.js`.

Une fois le serveur demarre, l'API est accessible sur `http://localhost:<PORT>`.

## Scripts disponibles

- `npm start` : demarre le serveur en mode developpement avec redemarrage automatique

## Structure du projet

```text
.
|-- Controllers/
|-- Models/
|-- routes/
|-- index.js
|-- package.json
`-- README.md
```

- `Controllers/` : logique metier des routes
- `Models/` : schemas Mongoose des utilisateurs et des publications
- `routes/` : definition des endpoints de l'API
- `index.js` : point d'entree de l'application

## Routes principales

### Authentification

| Methode | Route | Description |
| --- | --- | --- |
| `POST` | `/auth/register` | Creer un utilisateur |
| `POST` | `/auth/login` | Connecter un utilisateur |

### Utilisateurs

| Methode | Route | Description |
| --- | --- | --- |
| `GET` | `/user/:id` | Recuperer un utilisateur |
| `PUT` | `/user/:id` | Mettre a jour un utilisateur |
| `DELETE` | `/user/:id` | Supprimer un utilisateur |
| `PUT` | `/user/:id/follow` | Suivre un utilisateur |
| `PUT` | `/user/:id/unfollow` | Ne plus suivre un utilisateur |

### Publications

| Methode | Route | Description |
| --- | --- | --- |
| `POST` | `/post` | Creer une publication |
| `GET` | `/post/:id` | Recuperer une publication |
| `PUT` | `/post/:id` | Mettre a jour une publication |
| `DELETE` | `/post/:id` | Supprimer une publication |
| `PUT` | `/post/:id/like` | Liker ou retirer son like |
| `GET` | `/post/:id/timeline` | Recuperer le fil d'actualite d'un utilisateur |

## Notes utiles

- Certaines routes attendent des identifiants dans le corps de la requete, par exemple `currentUserId`, `currentUserAdminStatus` ou `userId`.
- Le projet ne contient pas, a ce stade, de documentation Swagger ni de suite de tests automatisee.

