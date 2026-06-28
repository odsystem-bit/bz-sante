# API N'NAKI — BZ Santé

Ce document décrit l'API interne de N'NAKI v1.0 et la roadmap de l'API publique v2.0.

---

## Introduction

N'NAKI v1.0 est un portail web avec données gérées côté client (localStorage). L'API publique v2.0 permettra aux applications mobiles, aux dashboards et aux systèmes partenaires (DHIS2) d'interagir avec la plateforme.

---

## Authentification v1.0

La v1.0 utilise un contrôle d'accès basé sur les rôles et les codes d'accès. L'authentification formelle sera intégrée en v2.0.

## Authentification v2.0 (publique)

L'API publique utilisera des tokens Bearer avec gestion des rôles.

```http
Authorization: Bearer {token}
```

---

## En-têtes communs v2.0

```http
Content-Type: application/json
Accept: application/json
Authorization: Bearer {token}
```

---

## Endpoints v2.0 (roadmap)

### Authentification

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| POST | `/api/v1/auth/login` | Se connecter |
| POST | `/api/v1/auth/logout` | Se déconnecter |
| GET | `/api/v1/auth/me` | Profil connecté |

### Hiérarchie administrative

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/v1/departments` | Lister les directions départementales |
| GET | `/api/v1/departments/{id}` | Détails d'une direction |
| GET | `/api/v1/zones` | Lister les zones sanitaires |
| GET | `/api/v1/establishments` | Lister les établissements |

### Contributions IA

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/v1/contributions` | Lister les contributions |
| POST | `/api/v1/contributions` | Soumettre une contribution |
| POST | `/api/v1/contributions/{id}/validate` | Valider une contribution |
| POST | `/api/v1/contributions/{id}/reject` | Rejeter une contribution |

### Patients VIP

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/v1/vip-patients` | Lister les patients VIP |
| POST | `/api/v1/vip-patients` | Créer un patient VIP |
| POST | `/api/v1/vip-access-requests` | Demander un accès VIP |
| POST | `/api/v1/vip-access-requests/{id}/approve` | Approuver une demande |
| GET | `/api/v1/vip-access-logs` | Journal des accès VIP |

### Statistiques

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/v1/statistics/national` | Statistiques nationales |
| GET | `/api/v1/statistics/departments/{id}` | Statistiques par département |
| GET | `/api/v1/indicators` | Indicateurs sanitaires |
| GET | `/api/v1/alerts` | Alertes épidémiques |

### Export

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/v1/exports/dhis2` | Export au format DHIS2 |
| GET | `/api/v1/exports/pdf` | Export PDF |
| GET | `/api/v1/exports/excel` | Export Excel |

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
- [ ] Documenter les flux de validation IA par pairs
- [ ] Documenter le workflow d'accès VIP
- [ ] Publier une collection Postman
