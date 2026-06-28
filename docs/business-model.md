# Business Model BZ+ — Bureau de Zone Santé

Ce document présente le modèle économique de **BZ+**, son marché cible, sa proposition de valeur et sa stratégie de déploiement.

---

## Vision

BZ+ vise à numériser la collecte des données sanitaires dans les Bureaux de Zone du Bénin. Le système simplifie la saisie quotidienne des Centres de Santé, renforce la supervision des zones sanitaires et accélère la remontée des rapports vers les autorités de santé.

---

## Marché cible

### Marché primaire

- **Bénin** : Bureaux de Zone, Zones Sanitaires, Centres de Santé (CS), directions départementales de la Santé.
- **Utilisateurs** : agents de santé dans les CS, administrateurs de zone, super administrateurs, autorités sanitaires.

### Segments cibles

- **Bureaux de Zone** : supervision et consolidation des données de leurs Centres de Santé.
- **Centres de Santé** : saisie rapide des données SMI, DPalu, CER et rapports mensuels.
- **Directions départementales / Ministère** : accès aux statistiques et rapports standardisés.
- **Organisations de santé** : collecte de données via formulaires personnalisés.

---

## Proposition de valeur

### Pour les Centres de Santé

- Saisie rapide des données sur web et mobile.
- Consultation et correction des saisies passées.
- Réduction des erreurs de transcription et des retards de rapport.
- Fonctionnement hors-ligne pour les zones mal connectées.

### Pour les Administrateurs de Zone

- Tableau de bord en temps réel de l'activité des CS.
- Alertes et statistiques épidémiologiques.
- Export Excel/PDF des données et rapports.
- Gestion centralisée des codes d'accès et formulaires.

### Pour les Super Administrateurs

- Gestion multi-zones et multi-CS.
- Configuration à distance de l'application mobile.
- Déploiement des mises à jour via upload APK.
- Sauvegarde de la base et journal d'activité.

### Pour les autorités sanitaires

- Données consolidées et standardisées.
- Formats d'export compatibles avec les outils ministériels (DHIS2 / SIGASI).
- Meilleure réactivité face aux alertes épidémiques.

---

## Modèle de revenus

| Source de revenu | Description | Statut |
| :--- | :--- | :--- |
| Abonnement par Bureau de Zone | Licence annuelle par zone sanitaire déployée | À définir |
| Mise en place et déploiement | Installation, configuration, import initial des CS | À définir |
| Formation et support | Accompagnement des agents de santé et administrateurs | À définir |
| Développements sur mesure | Formulaires personnalisés, intégrations spécifiques | À définir |
| Intégration DHIS2 / SIGASI | Connecteurs pour les remontées ministérielles | À venir |

---

## Stratégie de croissance

### Phase 1 : Prototype web (Terminé)

- Saisie web SMI et DPalu pour un Bureau de Zone.
- Structure de base SQLite et exports Excel.

### Phase 2 : Application mobile et hors-ligne (Terminé)

- Application Android BZ+.
- Mode hors-ligne avec synchronisation différée.
- Formulaires personnalisés.

### Phase 3 : Déploiement ATZ en production (En cours)

- Déploiement sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).
- Onboarding des CS de la Zone Sanitaire Allada-Toffo-Zè.
- Tableau de bord, statistiques, alertes et exports.

### Phase 4 : Expansion multi-zone

- Déploiement dans d'autres Bureaux de Zone du Bénin.
- Multi-tenant et base de données centralisée.

### Phase 5 : Intégration nationale

- Export DHIS2 / SIGASI.
- Tableaux de bord pour les directions départementales.

---

## Indicateurs clés (KPIs)

- Nombre de Centres de Santé actifs.
- Nombre de saisies SMI / DPalu par jour.
- Taux de remplissage des CER hebdomadaires.
- Nombre de formulaires publiés et de réponses.
- Taux d'utilisation de l'application mobile.
- Nombre de zones déployées.
- Temps de remontée des rapports mensuels.
- Taux de synchronisation réussie en mode hors-ligne.

---

## Projections financières

> Les projections détaillées seront ajoutées dans une version ultérieure du document.

- **Année 1** : consolidation du déploiement ATZ, onboarding de 30+ CS.
- **Année 2** : expansion vers 5-10 Bureaux de Zone supplémentaires.
- **Année 3** : couverture nationale et intégration aux systèmes ministériels.

---

## Besoins et partenariats

- **Investissement** : développement mobile, cloud, formation, support terrain.
- **Partenaires** : Ministère de la Santé, Bureaux de Zone, ONG santé, organisations internationales.
- **Programmes** : fonds d'innovation santé, incubateurs sociaux, coopérations techniques.
