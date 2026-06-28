# Architecture BZ Santé

Ce document présente l'architecture générale de BZ Santé. Il est destiné aux investisseurs, incubateurs et développeurs souhaitant comprendre les fondations techniques du projet.

> **Statut** : En cours de documentation. Certaines sections contiennent des placeholders qui seront complétées au fur et à mesure du développement.

---

## Vue d'ensemble

BZ Santé est une plateforme de gestion des données sanitaires qui connecte les agents de terrain, les superviseurs de zone et les administrateurs. Elle repose sur une architecture hybride avec synchronisation offline-first.

```
┌─────────────────────────────────────────────────────────────┐
│                        Utilisateurs                         │
│  Agent de santé    Superviseur    Admin    Analyste       │
└──────────────────────┬────────────────────────────────────────┘
                       │
┌──────────────────────▼────────────────────────────────────────┐
│                     Interfaces                                  │
│  App Mobile Flutter    Dashboard Web    Panel Admin           │
└──────────────────────┬────────────────────────────────────────┘
                       │ HTTPS / Sync API
┌──────────────────────▼────────────────────────────────────────┐
│                      Backend API (Node.js)                    │
│  Auth · Patients · Consultations · Rapports · Analytics       │
└──────────────────────┬────────────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┬──────────────┐
        │              │              │              │
┌───────▼──────┐ ┌────▼─────┐ ┌──────▼──────┐ ┌──────▼──────┐
│  PostgreSQL  │ │  SQLite  │ │ File Storage│ │  Rapports   │
│  (central)   │ │ (mobile) │ │  (exports)  │ │ (PDF/Excel) │
└──────────────┘ └──────────┘ └─────────────┘ └─────────────┘
```

---

## Couches applicatives

### 1. Application mobile Flutter

- Saisie des patients, consultations, maternités et vaccinations
- Mode hors ligne avec stockage SQLite local
- Synchronisation automatique lors de la connexion
- Interface adaptée aux agents de santé avec faible connectivité

### 2. Dashboard web

- Vue d'ensemble des indicateurs de santé par zone
- Gestion des utilisateurs et des centres de santé
- Génération et consultation des rapports
- Supervision des activités en temps réel

### 3. Backend API

- **Framework** : Node.js + Express
- **Base de données** : PostgreSQL
- **Authentification** : JWT avec rôles
- **Synchronisation** : endpoint dédié pour la réconciliation mobile/serveur
- **Rapports** : génération de PDF et Excel

### 4. Stockage

- Données centralisées dans PostgreSQL
- Données locales dans SQLite sur mobile
- Fichiers d'export et rapports stockés sur disque ou cloud

---

## Modèle de sécurité

- Authentification JWT avec expiration
- Rôles et permissions granulaires
- Chiffrement des communications en HTTPS
- Données de santé protégées et journalisées
- Conformité aux principes de protection des données personnelles et de santé

---

## Scalabilité

- Synchronisation incrémentale pour limiter la charge réseau
- Mise en cache des données fréquemment consultées
- Architecture modulaire facilitant l'évolution
- Préparation au déploiement cloud

---

## Environnements

| Environnement | Usage | Statut |
| :--- | :--- | :--- |
| Local | Développement | Actif |
| Staging | Tests et recettes | À venir |
| Production | Déploiement public | À venir |

---

## Prochaines étapes documentaires

- [ ] Schéma détaillé de la base de données
- [ ] Diagrammes de séquence des flux de synchronisation
- [ ] Spécification des endpoints API
- [ ] Matrice des rôles et permissions
- [ ] Plan de déploiement et de formation
