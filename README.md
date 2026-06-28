<div align="center">
  <img src="assets/banner.svg" alt="BZ+ Banner" width="100%" />
</div>

<div align="center">
  <img src="assets/logo/logo-placeholder.svg" alt="BZ+ Logo" width="120" height="120" />
  <h1>BZ+ — Bureau de Zone Santé</h1>
  <p><strong>Système de saisie et de supervision des données sanitaires pour les Bureaux de Zone du Bénin</strong></p>
  <p>
    <img src="https://img.shields.io/badge/Status-En%20production%20%28v2.1.0%29-2A8A1A?style=flat-square" alt="Status" />
    <img src="https://img.shields.io/badge/Version-2.1.0-1D3C6E?style=flat-square" alt="Version" />
    <img src="https://img.shields.io/badge/License-MIT-F5A800?style=flat-square" alt="License" />
    <img src="https://img.shields.io/badge/Zone%20pilote-ATZ%20%28Allada-Toffo-Z%C3%A8%29-CC1A1A?style=flat-square" alt="Zone" />
  </p>
</div>

---

## Table des matières

- [Présentation](#présentation)
- [Le problème](#le-problème)
- [La solution](#la-solution)
- [Fonctionnalités principales](#fonctionnalités-principales)
- [Architecture générale](#architecture-générale)
- [Technologies utilisées](#technologies-utilisées)
- [Feuille de route](#feuille-de-route)
- [Captures d'écran](#captures-décran)
- [Démo](#démo)
- [Liens officiels](#liens-officiels)
- [Contact](#contact)

---

## Présentation

**BZ+** (Bureau de Zone Santé) est un système de gestion des données sanitaires conçu pour les Bureaux de Zone du Bénin. Il permet aux Centres de Santé (CS) de saisir leurs données quotidiennes et hebdomadaires, et aux Administrateurs de Zone de superviser, consulter et exporter ces données.

La version actuelle est déployée en production pour le **Bureau de Zone ATZ** (Zone Sanitaire Allada-Toffo-Zè, Département du ZOU) sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

Le système comprend :
- Un **site web** accessible depuis n'importe quel navigateur.
- Une **application mobile Android** (BZ+) pour la saisie sur le terrain.

---

## Le problème

Dans les zones sanitaires béninoises, la collecte des données sanitaires fait face à plusieurs défis :
- Saisie manuelle sur papier, lente et sujette aux erreurs.
- Difficulté de consolidation des données de plusieurs Centres de Santé.
- Retards dans la remontée des rapports mensuels et hebdomadaires.
- Manque de visibilité en temps réel pour les administrateurs de zone.
- Accès limité à internet dans certaines zones rurales.
- Besoin de formats d'export standardisés (Excel, PDF) pour les rapports ministériels.

---

## La solution

BZ+ propose un écosystème numérique adapté aux réalités du terrain :

- **Saisie multi-CS** : chaque Centre de Santé saisit ses données via le web ou l'application mobile.
- **Données SMI** : Santé Maternelle et Infantile (CPN, accouchements, enfants, planification familiale, etc.).
- **Données DPalu** : registre paludisme (dispensaire, maternité, ruptures de stock).
- **Surveillance CER** : Compte-rendu Épidémiologique de Routine hebdomadaire (28 maladies, flambées, décès).
- **Rapports mensuels** : C6, PNLP1, MNT, C15 — partiellement auto-calculés.
- **Tableau de bord admin** : supervision de l'activité des CS, alertes, statistiques et exports.
- **Formulaires personnalisés** : création de formulaires par l'admin et remplissage par les CS.
- **Application mobile hors-ligne** : saisie sans connexion avec synchronisation différée.
- **Super administration** : gestion multi-zones, multi-CS, administrateurs, configuration à distance.

---

## Fonctionnalités principales

### Pour les Centres de Santé (CS)
- Saisie journalière **SMI** et **DPalu**.
- Surveillance épidémiologique hebdomadaire **CER**.
- Rapports mensuels **C6, PNLP1, MNT, C15** avec pré-remplissage automatique.
- Consultation des saisies et résumé mensuel.
- Remplissage des formulaires personnalisés.
- Export des données en Excel et PDF.

### Pour les Administrateurs de Zone
- Tableau de bord de l'activité des CS.
- Statistiques et alertes (maladies, décès, flambées, paludisme).
- Suivi du remplissage des CER et rapports.
- Export des données brutes et des résumés.
- Gestion des codes d'accès des CS.
- Gestion des formulaires personnalisés.

### Pour les Super Administrateurs
- Gestion des zones sanitaires et des Centres de Santé.
- Gestion des administrateurs et des permissions.
- Configuration à distance de l'application mobile (feature flags, messages, contacts).
- Upload et déploiement des mises à jour APK.
- Sauvegarde de la base de données.
- Journal d'activité des administrateurs.

### Sécurité et déploiement
- Authentification par rôle avec sessions sécurisées.
- Codes d'accès à 6 chiffres pour les CS.
- HTTPS forcé en production.
- Rate limiting et protection CSRF.
- Base de données SQLite avec sauvegarde manuelle.
- Déploiement sur Hostinger via Node.js / PM2 / Nginx.

Pour plus de détails, consulter :
- [`docs/architecture.md`](docs/architecture.md)
- [`docs/features.md`](docs/features.md)
- [`docs/business-model.md`](docs/business-model.md)
- [`docs/api.md`](docs/api.md)
- [`docs/faq.md`](docs/faq.md)

---

## Architecture générale

BZ+ repose sur une architecture web + mobile légère et déployable sur des infrastructures mutualisées :

- **Backend** : Node.js / Express, EJS pour les vues, SQLite avec better-sqlite3.
- **Frontend web** : HTML/CSS/JS, Bootstrap, Chart.js pour les statistiques.
- **Application mobile** : Flutter (application Android BZ+).
- **Base de données** : SQLite avec structure fidèle aux registres Excel nationaux.
- **Authentification** : sessions Express, codes d'accès CS, mots de passe admin/super admin.
- **Sécurité** : Helmet, rate limiting, CSP, HTTPS forcé, tokens API avec expiration.
- **Exports** : Excel (xlsx) et PDF (pdfkit).
- **Déploiement** : Hostinger via PM2 et Nginx, accessible sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## Technologies utilisées

### Backend
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

### Frontend
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=for-the-badge&logo=chart.js&logoColor=white)

### Mobile
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

### Outils
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![PM2](https://img.shields.io/badge/PM2-2B037A?style=for-the-badge&logo=pm2&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)

---

## Feuille de route

| Phase | Objectif | Statut |
| :--- | :--- | :--- |
| **v1.0** | Prototype de saisie web pour un Bureau de Zone | Terminé |
| **v2.0** | Application mobile, saisie hors-ligne, formulaires personnalisés | Terminé |
| **v2.1** | Déploiement ATZ, tableau de bord admin, statistiques, exports | En production |
| **v2.2** | Multi-zone, synchronisation cloud, amélioration du hors-ligne | En cours |
| **v3.0** | Intégration DHIS2/SIGASI et export vers le Ministère de la Santé | À venir |

Consulter [`ROADMAP.md`](ROADMAP.md) pour le détail.

---

## Captures d'écran

> Les captures d'écran seront ajoutées progressivement dans le dossier [`assets/screenshots/`](assets/screenshots/).

<div align="center">
  <img src="assets/screenshots/placeholder.svg" alt="Tableau de bord BZ+ placeholder" width="80%" />
  <p><em>Tableau de bord BZ+ — placeholder</em></p>
</div>

---

## Démo

Le site de production est accessible sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## Liens officiels

- **Site web** : [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech)
- **Documentation** : [`docs/`](docs/)
- **Portfolio** : [stanislas-nouemou](https://github.com/odsystem-bit/stanislas-nouemou)
- **GitHub** : [bz-sante](https://github.com/odsystem-bit/bz-sante)

---

## Contact

Pour toute question, partenariat ou déploiement dans un autre Bureau de Zone :

- **Email** : [contact@odsysteme.tech](mailto:contact@odsysteme.tech)
- **LinkedIn** : [stanislas-nouemou](https://linkedin.com/in/)
- **GitHub** : [@odsystem-bit](https://github.com/odsystem-bit)

---

<div align="center">
  <sub>BZ+ — La saisie sanitaire des Bureaux de Zone, simplifiée et numérisée.</sub>
</div>
