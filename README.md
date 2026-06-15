<div align="center">

# 🎬🍿 MenuCinema

### Quand le cinéma rencontre la restauration

[![Angular](https://img.shields.io/badge/Frontend-Angular%209-red)]()
[![Java](https://img.shields.io/badge/Backend-Java-blue)]()
[![Firebase](https://img.shields.io/badge/Auth-Firebase-orange)]()
[![TMDB](https://img.shields.io/badge/API-TMDB-green)]()
[![Jetty](https://img.shields.io/badge/Server-Jetty-yellow)]()

Projet réalisé dans le cadre de la **Licence 3 MIAGE - Université Grenoble Alpes**.

</div>

---

# 🎯 Présentation

**MenuCinema** est une application web permettant à un utilisateur de préparer sa séance de cinéma en combinant :

- 🎬 la consultation de films et séries ;
- 🍔 la commande de plats et menus ;
- 🛒 la gestion d'un panier unique ;
- 👤 la gestion d'un compte utilisateur ;
- 📄 la génération automatique de factures XML ;
- 📜 l'historique des commandes.

L'objectif du projet est de proposer une expérience unifiée où l'utilisateur peut sélectionner son contenu audiovisuel et son repas au sein d'une même plateforme.

---

# ✨ Fonctionnalités principales

## 🎬 Catalogue de films

- Recherche de films via l'API TMDB
- Consultation des détails d'un film
- Affichage des affiches et informations associées
- Ajout au panier

---

## 📺 Catalogue de séries

- Recherche de séries TV
- Consultation des détails
- Ajout au panier

---

## 🍽️ Gestion du menu de restauration

Le système embarque un catalogue de plats stockés côté serveur sous forme XML.

Fonctionnalités :

- Consultation du menu
- Catégorisation des plats
- Consultation des ingrédients
- Ajout au panier

---

## 🛒 Panier

Le panier permet de regrouper :

- films
- séries
- plats

Fonctionnalités :

- ajout d'éléments
- suppression
- modification des quantités
- calcul du montant total
- sauvegarde locale via `localStorage`

---

## 👤 Gestion utilisateur

Authentification via :

- Firebase Authentication
- Compte Google

Gestion des informations :

- nom
- prénom
- email
- téléphone
- adresse

---

## 📦 Commandes

Après validation du panier :

- création d'une commande
- enregistrement côté serveur
- association au compte utilisateur

---

## 📄 Génération de facture

Le système génère automatiquement :

- une facture XML
- téléchargeable depuis l'application

Les factures historiques restent consultables depuis l'espace utilisateur.

---

## 📜 Historique

Chaque utilisateur dispose de :

- la liste de ses commandes
- la date de commande
- les plats commandés
- les films/séries associés
- le téléchargement des anciennes factures

---

# 🏗️ Architecture du projet

```text
MenuCinema
│
├── clientMenuCinema/          Frontend Angular
│
└── serveur/                   Backend Java
```

---

## Frontend

Technologies utilisées :

| Technologie | Utilisation |
|------------|------------|
| Angular 9 | Interface utilisateur |
| TypeScript | Logique applicative |
| Bootstrap 4 | Mise en page |
| ng-bootstrap | Composants UI |
| Firebase | Authentification |
| TMDB API | Données films et séries |

---

## Backend

Technologies utilisées :

| Technologie | Utilisation |
|------------|------------|
| Java 8 | Logique métier |
| Jetty | Serveur HTTP embarqué |
| Maven | Gestion des dépendances |
| JDBC Oracle | Accès base de données |
| XML DOM / SAX | Gestion du catalogue et des factures |

---

# 🔄 Flux applicatif

```text
Utilisateur
      │
      ▼
Angular
      │
      ├────────► Firebase Authentication
      │
      ├────────► TMDB API
      │
      ▼
Serveur Java
      │
      ├────────► Base de données
      │
      ├────────► Gestion commandes
      │
      └────────► Génération factures XML
```

---

# 📂 Organisation du projet

## Frontend Angular

```text
src/app
│
├── carousel/
├── cart/
├── commande/
├── contact/
├── details/
├── formsignin/
├── login/
├── queryresult/
│
├── auth-client.service.ts
├── tmdb.service.ts
└── app-routing.module.ts
```

### Composants principaux

| Composant | Rôle |
|-----------|-------|
| Carousel | Affichage du contenu principal |
| Movie | Films |
| Serie | Séries |
| Plat | Menu de restauration |
| Cart | Panier |
| Commande | Historique |
| Details | Détails d'un élément |
| Login | Authentification |

---

## Backend Java

```text
src/main/java/l3m
│
├── PizzaServer.java
├── ClientAuthentificationServlet.java
├── PassageCommandeServlet.java
├── GetCommandesClientServlet.java
├── FactServlet.java
├── FactServletHisto.java
├── PlatsServlet.java
│
├── DAO/
├── LesClients/
├── LesCommandes/
└── LesCartes/
```

### Principaux services

| Servlet | Fonction |
|----------|----------|
| Authentification | Gestion utilisateur |
| PassageCommande | Création des commandes |
| GetCommandesClient | Historique |
| FactServlet | Génération facture |
| FactServletHisto | Factures archivées |
| PlatsServlet | Catalogue des plats |

---

# 🗃️ Stockage des données

Le projet combine plusieurs sources de données :

### Films / Séries

Source externe :

- The Movie Database (TMDB)

### Utilisateurs

- Firebase Authentication
- Base de données serveur

### Catalogue restauration

- Fichiers XML

### Factures

- Génération XML

---

# 🚀 Lancement du projet

## Frontend

```bash
cd clientMenuCinema

npm install

ng serve
```

Ou :

```bash
npm start
```

Application disponible sur :

```text
http://localhost:4200
```

---

## Backend

```bash
cd serveur

mvn clean install

mvn exec:java
```

Le serveur Jetty démarre alors automatiquement.

---

# 🔐 Authentification

L'application utilise :

- Firebase Authentication
- Connexion Google OAuth

Lors de la première connexion :

1. Création du profil utilisateur
2. Synchronisation avec le serveur métier
3. Récupération de l'historique de commandes

---

# 📚 Concepts techniques mis en œuvre

- Architecture client / serveur
- SPA Angular
- Services Angular
- Firebase Authentication
- Consommation d'API REST
- Persistance locale (`localStorage`)
- Gestion d'état utilisateur
- DAO Pattern
- JDBC
- XML DOM
- XML SAX
- Génération documentaire XML
- Maven
- Jetty Embedded

---

# 🎓 Contexte pédagogique

Ce projet a été réalisé dans le cadre du projet intégrateur de **Licence 3 MIAGE**.

L'objectif était de mettre en pratique :

- le développement web moderne ;
- les architectures distribuées ;
- l'intégration de services externes ;
- la gestion des données ;
- la conception logicielle complète d'une application métier.

---

<div align="center">

### 🍿 Bon film, bon repas et bon code !

**MenuCinema** — Projet intégrateur MIAGE

</div>