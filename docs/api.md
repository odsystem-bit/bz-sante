# API BZ Santé

Ce document décrit l'API publique de BZ Santé. Il est en cours de rédaction et sera enrichi au fur et à mesure du développement.

> **Statut** : Version préliminaire. Les endpoints, formats et authentification sont susceptibles d'évoluer.

---

## Introduction

L'API BZ Santé permet aux applications mobiles, aux dashboards et aux systèmes partenaires d'interagir avec la plateforme. Elle repose sur une architecture RESTful avec authentification JWT.

---

## Authentification

> **À compléter** : méthode d'authentification détaillée.

```http
Authorization: Bearer {token}
```

---

## En-têtes communs

```http
Content-Type: application/json
Accept: application/json
Authorization: Bearer {token}
```

---

## Endpoints

### Authentification

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| POST | `/api/v1/auth/login` | Se connecter |
| POST | `/api/v1/auth/logout` | Se déconnecter |
| GET | `/api/v1/auth/me` | Profil connecté |

### Patients

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/v1/patients` | Lister les patients |
| POST | `/api/v1/patients` | Créer un patient |
| GET | `/api/v1/patients/{id}` | Détails d'un patient |
| PUT | `/api/v1/patients/{id}` | Mettre à jour un patient |

### Consultations

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/v1/consultations` | Lister les consultations |
| POST | `/api/v1/consultations` | Créer une consultation |
| GET | `/api/v1/consultations/{id}` | Détails d'une consultation |

### Synchronisation

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| POST | `/api/v1/sync` | Envoyer les données locales au serveur |
| GET | `/api/v1/sync` | Récupérer les données mises à jour depuis le serveur |

### Rapports

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/v1/reports` | Lister les rapports disponibles |
| GET | `/api/v1/reports/{id}` | Télécharger un rapport |

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
| 500 | Erreur serveur |

---

## Prochaines étapes

- [ ] Définir les schémas complets de requête et réponse
- [ ] Rédiger les spécifications d'authentification
- [ ] Documenter la logique de synchronisation offline-first
- [ ] Publier une collection Postman
