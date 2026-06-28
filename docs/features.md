# Fonctionnalités N'NAKI — BZ Santé

Ce document détaille les fonctionnalités réelles de N'NAKI — BZ Santé, déployées en production sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## 1. Portail Ministériel N'NAKI

- Dashboard central du Ministère de la Santé du Bénin.
- Navigation par sections : Hiérarchie, IA Médicale, Contributeurs, Patients VIP, Gouvernance, Langues.
- Statistiques globales en temps réel : pathologies, contributeurs, validateurs, contributions.
- Badge de souveraineté : "100% Souverain — Données Bénin".

## 2. Hiérarchie Administrative

- Gestion des 12 directions départementales de la Santé.
- Gestion des 34 zones sanitaires du Bénin.
- Gestion des établissements de santé (CHU, hôpitaux de zone, cliniques, postes de santé).
- Cartographie et détails par département et zone.
- Liaison entre les niveaux administratifs et les données sanitaires.

## 3. IA Médicale N'NAKI

- Base de connaissances médicales souveraine.
- Espace contributeurs pour experts et médecins.
- Validation par pairs (3/4 validateurs) avant intégration.
- Administration des contributions et des validateurs.
- Scoring et historique des contributions.
- Paiements aux contributeurs validés.
- Gestion des 45+ pathologies en base.

## 4. Gestion des Patients VIP

- Dossiers médicaux confidentiels des hautes personnalités.
- Niveaux d'accès : Président, Ministre, Député, Diplomate.
- Codes d'accès spécifiques par niveau.
- Demandes d'accès avec justification et validation.
- Audit logs des consultations et des accès.
- Journal des tentatives échouées et blocage automatique.
- Gestion des codes globaux et temporaires.

## 5. Gouvernance Médicale

- Définition des protocoles de traitement.
- Directives officielles et règles pour l'IA.
- Validation des protocoles par les autorités sanitaires.
- Traçabilité des modifications et versions.

## 6. Statistiques Nationales et Indicateurs

- Tableaux de bord national par département.
- Indicateurs d'activité, épidémiologie, démographie.
- Indicateurs maternels, infantiles, mortalité.
- Suivi vaccinal par dose et par pathologie.
- Alertes épidémiques en temps réel.
- Graphiques et visualisations (Chart.js).
- Export DHIS2, PDF et Excel.
- Score de qualité des données.

## 7. Langues Locales

- Espace de contribution aux langues locales (Fon, Yoruba, Dendi, etc.).
- Gouvernance linguistique pour l'IA médicale.
- Traduction et validation des termes médicaux.
- Accessibilité pour les populations non francophones.

---

## Matrice rôles / fonctionnalités

| Fonctionnalité | Administrateur | Validateur | Contributeur | Réceptionniste | Analyste |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Gérer la hiérarchie administrative | :white_check_mark: | :x: | :x: | :x: | :x: |
| Valider les contributions IA | :white_check_mark: | :white_check_mark: | :x: | :x: | :x: |
| Soumettre des contributions IA | :x: | :white_check_mark: | :white_check_mark: | :x: | :x: |
| Gérer les patients VIP | :white_check_mark: | :x: | :x: | :white_check_mark: | :x: |
| Voir les statistiques nationales | :white_check_mark: | :x: | :x: | :x: | :white_check_mark: |
| Gérer la gouvernance médicale | :white_check_mark: | :white_check_mark: | :x: | :x: | :x: |
| Contribuer aux langues locales | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: | :x: |

---

## Prochaines étapes

- [ ] Backend API et base de données centralisée
- [ ] Authentification et gestion des rôles
- [ ] Application mobile pour la saisie terrain
- [ ] Intégration DHIS2 et systèmes ministériels
- [ ] Tests d'acceptation par les autorités sanitaires
