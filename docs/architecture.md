# Architecture N'NAKI — BZ Santé

Ce document présente l'architecture générale de N'NAKI — BZ Santé, déployé en production sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## Vue d'ensemble

N'NAKI est une plateforme web souveraine de gestion de l'IA médicale et des données sanitaires du Bénin. Elle connecte le Ministère de la Santé, les directions départementales, les zones sanitaires, les experts médicaux et les établissements de santé.

```
┌────────────────────────────────────────────────────────────────┐
│                         Utilisateurs                            │
│  Ministère    Validateurs    Contributeurs    Réceptionnistes  │
└───────────────────────┬───────────────────────────────────────┘
                        │
┌───────────────────────▼───────────────────────────────────────┐
│                      Interfaces Web                            │
│  Portail N'NAKI · Dashboard IA · Gestion VIP · Statistiques   │
└───────────────────────┬───────────────────────────────────────┘
                        │ HTTPS
┌───────────────────────▼───────────────────────────────────────┐
│                   Backend API (roadmap v2.0)                   │
│  Auth · Hiérarchie · Contributions IA · VIP · Statistiques     │
└───────────────────────┬───────────────────────────────────────┘
                        │
        ┌───────────────┼───────────────┬───────────────┐
        │               │               │               │
┌───────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
│  PostgreSQL  │ │   Redis     │ │ File Storage│ │   DHIS2    │
│  (souverain) │ │   (cache)   │ │  (exports)  │ │  (export)  │
└──────────────┘ └─────────────┘ └─────────────┘ └─────────────┘
```

---

## Couches applicatives

### 1. Portail web N'NAKI

- HTML5, CSS3, JavaScript vanilla, Chart.js.
- Interface responsive organisée par modules fonctionnels.
- Accès adapté aux rôles (administration, validation, contribution, réception).

### 2. Backend API (v2.0)

- **Framework** : Node.js / NestJS (roadmap).
- **Base de données** : PostgreSQL hébergée au Bénin.
- **Authentification** : sessions sécurisées avec rôles.
- **Validation IA** : workflow de soumission et validation par pairs.
- **Exports** : DHIS2, PDF, Excel.

### 3. Stockage

- Données sanitaires hébergées en République du Bénin.
- localStorage utilisé pour la démonstration en v1.0.
- Fichiers d'export et rapports stockés localement.

---

## Modèle de sécurité

- Authentification par rôle avec contrôle d'accès.
- Codes d'accès VIP spécifiques par niveau (Président, Ministre, Député, Diplomate).
- Journalisation des accès et des tentatives échouées.
- Blocage automatique après tentatives répétées.
- Données de santé chiffrées et hébergées localement.
- Conformité aux principes de protection des données personnelles et de santé.

---

## Scalabilité

- Architecture modulaire facilitant l'évolution.
- Cache Redis pour les données fréquemment consultées.
- Préparation au déploiement cloud souverain.
- Export incrémental vers DHIS2.

---

## Environnements

| Environnement | Usage | Statut |
| :--- | :--- | :--- |
| Local | Développement | Actif |
| Production v1.0 | [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech) | Actif |
| Staging v2.0 | Tests et recettes | À venir |
| Production v2.0 | Backend API + base centralisée | À venir |

---

## Prochaines étapes documentaires

- [ ] Schéma détaillé de la base de données
- [ ] Diagrammes de séquence des flux critiques (validation IA, accès VIP)
- [ ] Spécification des endpoints API
- [ ] Matrice des rôles et permissions
- [ ] Plan de déploiement souverain et de monitoring
