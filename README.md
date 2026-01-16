# Waves

> Un prototype de réseau social moderne inspiré de X, permettant de partager des publications, suivre d'autres utilisateurs et communiquer en temps réel.

Il s'agit de mon premier projet d'apprentissage de React.

## Table des matières

- [Caractéristiques](#caractéristiques)

- [Stack technologique](#stack-technologique)
- [Installation](#installation)
- [Usage](#usage)
- [Fonctionnalités](#fonctionnalités)
- [Architecture](#architecture)
- [Gestion des erreurs](#gestion-des-erreurs)

## Caractéristiques

✨ **Fonctionnalités principales** :

- 📝 Publication de waves (messages)
- 👥 Système d'abonnement/suivi
- 💬 Messagerie en temps réel
- ❤️ Système de likes et réponses
- 🖼️ Support des images et emojis
- 🌓 Thème clair/sombre avec persistance
- 📱 Interface entièrement responsive (mobile-first)
- 🔐 Authentification Firebase (email/password et Google)
- 🌍 Support multilingue (i18n)

## Stack technologique

### Frontend

- **React** 18.2+ - Bibliothèque UI
- **React Router** 7.6+ - Routage
- **TailwindCSS** 4.1+ - Styling
- **Vite** 6.3+ - Build tool
- **Framer Motion** - Animations

### Gestion des données

- **Firebase** 11.9+ - Backend & Real-time Database
- **TanStack Query** 5.83+ - Gestion du cache et des requêtes

### Formulaires et validation

- **React Hook Form** 7.58+ - Gestion des formulaires
- **React Modal** 3.16+ - Modales

### UI & UX

- **React Icons** 5.5+ - Icônes
- **Lucide React** 0.525+ - Icônes modernes
- **Emoji Picker React** 4.13+ - Sélecteur d'emojis
- **React Medium Image Zoom** 5.3+ - Zoom d'images
- **React Spinners** 0.17+ - Loaders
- **React Toastify** 11.0+ - Notifications
- **React Responsive** 10.0+ - Responsive queries

### Internationalisation

- **i18next** 25.3+ - Framework i18n
- **react-i18next** 15.6+ - Intégration React

## Installation

### Prérequis

- Node.js 16+ et npm 7+
- Git

### Étapes

1. **Cloner le dépôt**

```bash
git clone <repository-url>
cd project-w
```

2. **Installer les dépendances**

```bash
npm install
```

3. **Configuration Firebase**
   - Créer un fichier `.env.local` à la racine du projet
   - Ajouter vos identifiants Firebase :

```env
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_DATABASE_URL=your_database_url
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_messaging_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

## Usage

### Développement

```bash
npm run dev
```

L'application sera accessible sur `http://localhost:5173`

### Build production

```bash
npm run build
```

### Preview production

```bash
npm run preview
```

### Linting

```bash
npm run lint
```

## Fonctionnalités

### 🔐 Authentification

#### Inscription

- Email + mot de passe (minimum 8 caractères)
- Authentification Google
- Validation en temps réel

#### Connexion

- Email/mot de passe
- Google Sign-In
- Mot de passe oublié

> **Note** : Un compte Google est prioritaire. Si un utilisateur s'inscrit via email puis se connecte via Google avec la même adresse, l'authentification par mot de passe sera écrasée.

### 👤 Profil utilisateur

**Informations modifiables** :

- Pseudo (obligatoire à la première connexion)
- Prénom et nom
- Date de naissance
- Ville et pays
- Photo de profil

**Fonctionnalités** :

- Modification du mot de passe
- Prévisualisation de la photo de profil avant validation
- Upload des images sur serveur (gestion automatique des anciennes photos)
- Image de profil par défaut si aucune sélectionnée

### 🏠 Page d'accueil

#### Section publication

- Rédaction de waves
- Ajout d'emojis via sélecteur intégré
- Upload d'images

#### Fil d'actualités

- Affichage chronologique de toutes les waves
- Actions par wave :
  - ❤️ Like/Unlike (indisponible pour votre propre wave)
  - 💬 Répondre avec formulaire inline
  - 👁️ Voir les réponses
  - ❌ Supprimer (auteur uniquement)

> **Comportement** : L'ouverture du formulaire de réponse ou des réponses ferme l'autre section (exclusivité)

### 👥 Abonnements

- Vue des abonnés
- Vue des abonnements
- Accès rapide aux profils via pseudo

### 💬 Messagerie

**Fonctionnalités** :

- Conversations avec autres utilisateurs
- Affichage des derniers messages
- Notifications visuelles pour nouveaux messages non lus
- Upload d'images dans les messages
- Validation via Enter ou bouton
- Auto-scroll au dernier message

### 🔍 Recherche

- Recherche d'utilisateurs par pseudo
- Recherche par prénom/nom
- Insensible à la casse
- Résultats en temps réel
- Accès direct au profil

### 🎨 Thème

- Basculement clair/sombre
- Persistance des préférences dans le navigateur
- Application globale

### 🚨 Pages spéciales

- **Page d'erreur** : Pour les URLs invalides avec bouton retour
- **Modal de bienvenue** : Demande du pseudo à la première connexion

## Architecture

### Structure du projet

```
src/
├── assets/
│   ├── fonts/          # Polices personnalisées
│   └── images/         # Images statiques
├── components/         # Composants réutilisables
│   └── layout/         # Composants de mise en page
├── contexts/           # Contextes React (thème, utilisateur)
├── hooks/              # Hooks personnalisés
│   ├── messages/       # Gestion des messages
│   ├── users/          # Gestion des utilisateurs
│   ├── utilities/      # Hooks utilitaires
│   └── waves/          # Gestion des waves
├── pages/              # Pages principales
├── utilities/          # Fonctions utilitaires
└── main.jsx            # Point d'entrée
```

### Gestion de l'état

- **Contextes** : Thème, utilisateur connecté
- **TanStack Query** : Cache des données, requêtes API
- **React Hook Form** : État des formulaires

### Backend

- **Firebase Realtime Database** : Stockage des données
- **Firebase Authentication** : Gestion des utilisateurs
- **PHP** (`backend/`) : Proxy et gestion des uploads d'images

## Gestion des erreurs

- **Toasts** : Notifications d'erreur/succès utilisateur
- **Page d'erreur** : Gestion des routes invalides
- **Validations** : En temps réel dans les formulaires
- **Messages explicites** : Feedback clair pour chaque action

---

**Version** : 0.0.0  
**Licence** : À définir  
**Auteur** : Romain
