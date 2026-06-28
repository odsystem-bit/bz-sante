# API BZ+ — Bureau de Zone Santé

Ce document décrit les endpoints web et l'API mobile de **BZ+**, utilisés par le site web et l'application Android pour la saisie et la synchronisation des données sanitaires.

---

## Introduction

BZ+ fonctionne comme une application web monolithique Node.js / Express avec une API dédiée à l'application mobile. L'API mobile utilise des tokens pour l'authentification et supporte le mode hors-ligne avec synchronisation différée.

---

## Authentification web

Le site web utilise des sessions Express sécurisées :
- Connexion CS par zone + CS + code d'accès à 6 chiffres.
- Connexion admin par nom d'utilisateur et mot de passe.
- Connexion super admin par URL `/super/login` et credentials dédiés.

## Authentification API mobile

L'application mobile s'authentifie par token. Les tokens expirent après 30 jours d'inactivité.

```http
Authorization: Bearer {token}
```

---

## En-têtes communs API

```http
Content-Type: application/json
Accept: application/json
Authorization: Bearer {token}
```

---

## Endpoints API mobile

### Authentification

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| POST | `/api/mobile/auth/login` | Connexion CS (zone + CS + code) |
| POST | `/api/mobile/auth/logout` | Déconnexion et révocation du token |
| GET | `/api/mobile/auth/me` | Profil et CS connecté |
| POST | `/api/mobile/auth/refresh` | Rafraîchissement du token |

### Configuration et zones

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/mobile/config` | Configuration à distance (feature flags, nom, contacts) |
| GET | `/api/mobile/zones` | Liste des zones sanitaires |
| GET | `/api/mobile/zones/{id}/centres` | Centres de Santé d'une zone |
| GET | `/api/mobile/app-version` | Version minimale et lien APK |

### Saisie des données

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| POST | `/api/mobile/saisies/smi` | Enregistrer une saisie SMI |
| POST | `/api/mobile/saisies/dpalu` | Enregistrer une saisie DPalu |
| POST | `/api/mobile/saisies/cer` | Enregistrer un CER hebdomadaire |
| POST | `/api/mobile/saisies/rapports` | Enregistrer un rapport mensuel |
| POST | `/api/mobile/saisies/sync` | Synchronisation batch (mode hors-ligne) |
| GET | `/api/mobile/saisies/{type}` | Consulter ses saisies |

### Formulaires

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/mobile/formulaires` | Liste des formulaires publiés |
| POST | `/api/mobile/formulaires/{id}/reponses` | Soumettre une réponse |
| GET | `/api/mobile/formulaires/mes-reponses` | Réponses du CS connecté |

### Export et résumé

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/mobile/resume-mensuel` | Résumé mensuel du CS |
| GET | `/api/mobile/export/excel` | Export Excel des données du CS |
| GET | `/api/mobile/export/pdf` | Export PDF des données du CS |

---

## Endpoints web principaux

### Espace CS
- `GET /cs/login` — Connexion Centre de Santé.
- `POST /cs/saisie/smi` — Saisie SMI.
- `POST /cs/saisie/dpalu` — Saisie DPalu.
- `POST /cs/saisie/cer` — Saisie CER.
- `GET /cs/consulter` — Consultation des données.
- `GET /cs/resume` — Résumé mensuel.
- `GET /cs/formulaires` — Formulaires personnalisés.

### Espace Admin
- `GET /admin/login` — Connexion administrateur.
- `GET /admin/dashboard` — Tableau de bord de la zone.
- `GET /admin/statistiques` — Statistiques et alertes.
- `GET /admin/cer` — Surveillance CER.
- `GET /admin/rapports` — Rapports mensuels.
- `GET /admin/resume` — Résumé mensuel zone.
- `GET /admin/exporter` — Export des données brutes.
- `GET /admin/parametres` — Codes d'accès et formulaires.

### Espace Super Admin
- `GET /super/login` — Connexion Super Admin.
- `GET /super/zones` — Gestion des zones.
- `GET /super/centres` — Gestion des CS.
- `GET /super/admins` — Gestion des administrateurs.
- `GET /super/config` — Configuration à distance.
- `GET /super/apk` — Upload APK.
- `GET /super/backup` — Sauvegarde de la base.
- `GET /super/logs` — Journal d'activité.

---

## Codes de réponse

| Code | Signification |
| :--- | :--- |
| 200 | Succès |
| 201 | Ressource créée |
| 400 | Requête invalide |
| 401 | Non authentifié |
| 403 | Non autorisé |
| 404 | Ressource non trouvée |
| 422 | Erreur de validation |
| 429 | Trop de requêtes (rate limiting) |
| 500 | Erreur serveur |

---

## Prochaines étapes

- [ ] Documenter les schémas complets de requête et réponse de l'API mobile.
- [ ] Publier une collection Postman pour l'API mobile.
- [ ] Spécifier le flux de synchronisation hors-ligne (conflits, retry).
- [ ] Documenter les endpoints d'export DHIS2 / SIGASI.
