# Fonctionnalités BZ Santé

Ce document détaille les fonctionnalités principales de BZ Santé, organisées par module et par rôle utilisateur.

> **Statut** : En cours de documentation. Les placeholders seront remplacés par des spécifications détaillées.

---

## 1. Module Authentification

- Connexion par identifiant et mot de passe
- Rôles : agent de santé, superviseur, administrateur, analyste
- Gestion du profil utilisateur
- Récupération de mot de passe
- Authentification hors ligne limitée

## 2. Module Patients

- Création et gestion des dossiers patients
- Informations démographiques (nom, âge, sexe, adresse, contact)
- Historique des consultations
- Recherche de patients

## 3. Module Consultations

- Enregistrement d'une consultation
- Saisie des symptômes et du diagnostic
- Prescription et traitement
- Suivi des rendez-vous

## 4. Module Maternité

- Suivi des accouchements
- Gestion des mères et des nounés
- Indicateurs de mortalité maternelle et néonatale
- Historique des visites prénatales et postnatales

## 5. Module Vaccination

- Calendrier vaccinal national
- Enregistrement des doses administrées
- Rappels de vaccination
- Statistiques de couverture vaccinale

## 6. Module Statistiques et Rapports

- Tableaux de bord par zone et par centre
- Indicateurs clés de santé publique
- Rapports mensuels et annuels générés automatiquement
- Exports PDF et Excel

## 7. Module Synchronisation

- Saisie hors ligne sur mobile
- Synchronisation des données avec le serveur central
- Gestion des conflits de données
- File d'attente de synchronisation

## 8. Module Administration

- Gestion des centres de santé
- Gestion des zones de santé
- Gestion des utilisateurs et des rôles
- Configuration des types de consultations et vaccins

---

## Matrice rôles / fonctionnalités

| Fonctionnalité | Agent | Superviseur | Admin | Analyste |
| :--- | :--- | :--- | :--- | :--- |
| Saisir patients/consultations | :white_check_mark: | :x: | :x: | :x: |
| Voir les statistiques de sa zone | :x: | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| Générer des rapports | :x: | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| Gérer les utilisateurs | :x: | :x: | :white_check_mark: | :x: |
| Gérer les centres | :x: | :x: | :white_check_mark: | :x: |
| Voir les analytics globales | :x: | :x: | :white_check_mark: | :white_check_mark: |

---

## Prochaines étapes

- [ ] Spécifications détaillées de chaque module
- [ ] Maquettes et parcours utilisateurs
- [ ] Dictionnaire des données
- [ ] Tests d'acceptation par module
