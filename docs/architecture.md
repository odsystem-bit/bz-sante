# Architecture BZ+ — Bureau de Zone Santé

Ce document présente l'architecture générale de **BZ+**, système de saisie et de supervision des données sanitaires des Bureaux de Zone, déployé en production sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## Vue d'ensemble

BZ+ est un système web + mobile de collecte des données sanitaires au niveau des Bureaux de Zone du Bénin. Il connecte les Centres de Santé (CS), les Administrateurs de Zone et les Super Administrateurs dans une architecture légère et déployable sur infrastructure mutualisée.

```
┌─────────────────────────────────────────────────────────────────┐
│                         Utilisateurs                             │
│  Super Admin    Admin de Zone    Centre de Santé (CS)           │
└───────────────────────┬─────────────────────────────────────────┘
                        │
        ┌───────────────┼───────────────┐
        │               │               │
┌───────▼──────┐ ┌──────▼──────┐ ┌─────▼──────┐
│  Site Web    │ │  API /      │ │  App Mobile│
│  (EJS/HTML)  │ │  Backend    │ │  (Flutter) │
│              │ │  (Node.js)  │ │            │
└───────┬──────┘ └──────┬──────┘ └─────┬──────┘
        │               │               │
        └───────────────┴───────────────┘
                        │
        ┌───────────────┼───────────────┐
        │               │               │
┌───────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
│   SQLite     │ │  File       │ │  Tokens    │
│  (sante.db)  │ │  Storage    │ │  API Mobile│
│              │ │  (exports)  │ │            │
└──────────────┘ └─────────────┘ └─────────────┘
```

---

## Couches applicatives

### 1. Site web BZ+

- **Moteur** : Node.js / Express avec EJS comme moteur de templates.
- **Frontend** : HTML5, CSS3, Bootstrap, JavaScript vanilla.
- **Visualisation** : Chart.js pour les statistiques et alertes.
- **Pages publiques** : accueil, connexion CS, connexion admin, connexion super admin.
- **Pages protégées** : saisie, consultation, tableau de bord, statistiques, formulaires, paramètres.

### 2. Backend API

- **Framework** : Node.js / Express.
- **Base de données** : SQLite (`better-sqlite3`) avec structure fidèle aux registres Excel nationaux.
- **Authentification** : sessions Express côté web, tokens API côté mobile.
- **Sécurité** : Helmet, rate limiting, CSP, HTTPS forcé, tokens avec expiration.
- **Exports** : Excel (xlsx) et PDF (pdfkit).

### 3. Application mobile BZ+ (Flutter)

- **Plateforme** : Android (APK).
- **Mode hors-ligne** : stockage local et synchronisation différée avec le backend.
- **Mise à jour OTA** : vérification de version et téléchargement d'APK depuis le backend.
- **Configuration distante** : feature flags et paramètres récupérés depuis le serveur.

### 4. Stockage

- **Base de données** : SQLite hébergée sur le serveur (`sante.db`).
- **Fichiers** : exports Excel/PDF, uploads APK, images de formulaires.
- **Sauvegarde** : export manuel de la base depuis le panneau Super Admin.

---

## Modèle de sécurité

- **Authentification par rôle** : Super Admin, Admin de Zone, Centre de Santé.
- **Codes d'accès CS** : codes à 6 chiffres générés automatiquement.
- **Mots de passe admin** : minimum 8 caractères, réinitialisation par Super Admin.
- **Sessions** : httpOnly, sameSite, expiration 8h, cookie personnalisé.
- **Rate limiting** : 10 tentatives de connexion par 15 minutes, 60 requêtes API par minute.
- **Blocs** : blocage après 5 tentatives échouées (30 minutes).
- **HTTPS forcé** : redirection automatique en production.
- **Headers de sécurité** : Helmet + CSP personnalisée.
- **Audit** : journal d'activité des administrateurs.

---

## Scalabilité

- **Modularité** : routes Express séparées par domaine (auth, saisie, admin, super admin, API mobile).
- **Légèreté** : SQLite suffisant pour les déploiements mono-zone, migrable vers PostgreSQL si besoin.
- **Déploiement** : Hostinger VPS avec Node.js, PM2 et Nginx.
- **Future intégration** : export DHIS2 / SIGASI pour les remontées ministérielles.

---

## Environnements

| Environnement | Usage | Statut |
| :--- | :--- | :--- |
| Local | Développement et tests | Actif |
| Production v2.1 | Bureau de Zone ATZ — [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech) | Actif |
| Staging | Tests multi-zones | À venir |
| Production v2.2 | Multi-zones + synchronisation cloud | En cours |

---

## Prochaines étapes documentaires

- [ ] Schéma détaillé de la base de données SQLite.
- [ ] Diagrammes de séquence des flux critiques (synchronisation mobile, exports).
- [ ] Spécification complète des endpoints API mobile.
- [ ] Matrice des rôles et permissions.
- [ ] Plan de déploiement multi-zone et de monitoring.
