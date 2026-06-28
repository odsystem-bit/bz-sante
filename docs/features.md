# Fonctionnalités BZ+ — Bureau de Zone Santé

Ce document détaille les fonctionnalités de **BZ+**, système de saisie et de supervision des données sanitaires des Bureaux de Zone, déployé en production sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## 1. Saisie des données sanitaires

### 1.1 SMI — Santé Maternelle et Infantile (Registre C5)

Saisie journalière des indicateurs de maternité :
- **CPN** : Consultations Prénatales.
- **Grossesse** : Fer, déparasitant, facteurs de risque.
- **Paludisme Grossesse** : TPI/SP, MIILD.
- **Nutrition Grossesse** : État nutritionnel.
- **CPoN** : Consultations Post-Natales.
- **Accouchements** : Naissances, complications, décès.
- **Enfants** : Consultations d'enfants sains, vaccination.
- **Planification Familiale** : Méthodes contraceptives.

### 1.2 DPalu — Registre Paludisme

Saisie journalière du paludisme :
- **Dispensaire Simple** : cas masculins / féminins.
- **Dispensaire Grave** : cas masculins / féminins.
- **Maternité Simple FE** : femmes enceintes.
- **Maternité Grave FE** : femmes enceintes.
- **Ruptures de Stock** : stock de médicaments.

### 1.3 CER — Surveillance Épidémiologique (Hebdomadaire)

Compte-rendu Épidémiologique de Routine à remplir chaque semaine :
- **SIMR** : 28 maladies à déclaration obligatoire (cas et décès par âge et sexe).
- **Décès communautaires** : 6 indicateurs.
- **Flambées / Épidémies** : 4 indicateurs.
- **Paludisme** : 9 indicateurs spécifiques.

### 1.4 Rapports mensuels

Rapports mensuels partiellement auto-calculés :
- **C6** : Accouchements, CPN, Naissances.
- **PNLP1** : Paludisme simple et grave.
- **MNT** : Maladies Non Transmissibles.
- **C15** : Santé de la Reproduction des Adolescents.

---

## 2. Application mobile BZ+ (Android)

- Saisie SMI, DPalu, CER et rapports depuis le terrain.
- Mode **hors-ligne** avec stockage local et synchronisation différée.
- Indicateurs en ligne / hors-ligne / synchronisation en cours.
- Vérification des mises à jour OTA et téléchargement de l'APK.
- Formulaires personnalisés accessibles depuis l'app.

---

## 3. Tableau de bord administrateur

- Vue d'ensemble de tous les CS de la zone.
- Filtres par mois et année.
- Nombre de jours de saisie SMI / DPalu par CS.
- Statut de remplissage des sections (barre de progression).
- Date de dernière saisie et statut d'activité (vert / jaune / rouge).
- Tableau récapitulatif des sections complétées par CS.

---

## 4. Statistiques et alertes

- Statistiques CER globales de la zone.
- Top 15 maladies SIMR les plus déclarées.
- Maladies critiques avec décès signalés.
- Décès communautaires par catégorie.
- Flambées épidémiques en cours.
- Paludisme : répartition Simple / Grave.
- Évolution hebdomadaire SIMR et Paludisme.
- Classement des CS (top 10 plus actifs).
- CS sans données CER (alerte).
- Tendances mensuelles SMI et DPalu.
- Répartition par âge (<5 ans, ≥5 ans) et par sexe (M/F).

---

## 5. Gestion des formulaires personnalisés

### Types de champs supportés
- Texte court, zone de texte, nombre, email.
- Liste déroulante, choix unique, cases à cocher.
- Date, heure, image (upload max 5 Mo).

### Fonctionnalités
- Création, modification, duplication, publication, suppression.
- Lien public pour accès sans connexion.
- Limite de soumissions par répondant.
- Consultation des réponses et export Excel / PDF.

---

## 6. Super administration

- Gestion des zones sanitaires (ajout, renommage, suppression).
- Gestion des Centres de Santé (ajout, suppression, déplacement entre zones).
- Gestion des administrateurs de zone (ajout, permissions, désactivation, réinitialisation).
- Permissions : `data`, `forms`, `all`.
- Configuration à distance de l'application mobile (feature flags, nom, message de bienvenue, contacts, version minimale).
- Upload et déploiement des mises à jour APK.
- Sauvegarde de la base de données SQLite.
- Journal d'activité des administrateurs (50 dernières actions).
- Nettoyage des tokens API expirés.

---

## 7. Sécurité

- Authentification par rôle : Super Admin, Admin, CS.
- Codes d'accès à 6 chiffres pour les CS.
- Mots de passe admin / super admin (minimum 8 caractères).
- Blocage après 5 tentatives de connexion échouées (30 minutes).
- Sessions sécurisées (httpOnly, sameSite, HTTPS en production).
- Rate limiting sur les endpoints sensibles.
- Headers de sécurité via Helmet et CSP.
- Sauvegarde manuelle de la base de données.
- HTTPS forcé en production.

---

## 8. Exports

### Exports CS
- Données de consultation (Excel, PDF).
- Résumé mensuel (Excel, PDF).

### Exports Admin
- Données brutes SMI + DPalu (Excel).
- CER Surveillance (Excel, PDF).
- Résumé mensuel zone (Excel, PDF).
- Réponses formulaires (Excel, PDF).

---

## Matrice rôles / fonctionnalités

| Fonctionnalité | Super Admin | Admin de Zone | Centre de Santé |
| :--- | :--- | :--- | :--- |
| Saisir SMI / DPalu / CER | :x: | :x: | :white_check_mark: |
| Consulter ses propres données | :x: | :x: | :white_check_mark: |
| Voir les données de tous les CS | :x: | :white_check_mark: | :x: |
| Exporter les données zone | :x: | :white_check_mark: | :x: |
| Gérer les codes d'accès CS | :x: | :white_check_mark: | :x: |
| Créer / gérer les formulaires | :x: | :white_check_mark: | :x: (remplissage) |
| Gérer les zones et CS | :white_check_mark: | :x: | :x: |
| Gérer les administrateurs | :white_check_mark: | :x: | :x: |
| Configurer l'application mobile | :white_check_mark: | :x: | :x: |
| Sauvegarder la base | :white_check_mark: | :x: | :x: |

---

## Prochaines étapes

- [ ] Déploiement multi-zones (autres Bureaux de Zone du Bénin).
- [ ] Synchronisation cloud et base de données centralisée.
- [ ] Amélioration du mode hors-ligne (sync automatique, conflits).
- [ ] Intégration DHIS2 / SIGASI pour les remontées ministérielles.
- [ ] Notifications automatiques (alertes CER, rappels de saisie).
