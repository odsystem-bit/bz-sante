<div align="center">
  <img src="assets/banner.svg" alt="N'NAKI Banner" width="100%" />
</div>

<div align="center">
  <img src="assets/logo/logo-placeholder.svg" alt="N'NAKI Logo" width="120" height="120" />
  <h1>N'NAKI — BZ Santé</h1>
  <p><strong>Plateforme souveraine d'IA médicale et de gestion sanitaire du Bénin</strong></p>
  <p>
    <img src="https://img.shields.io/badge/Status-En%20production%20%28v1.0%29-2A8A1A?style=flat-square" alt="Status" />
    <img src="https://img.shields.io/badge/Version-1.0.0-1D3C6E?style=flat-square" alt="Version" />
    <img src="https://img.shields.io/badge/License-MIT-F5A800?style=flat-square" alt="License" />
    <img src="https://img.shields.io/badge/Marché-Bénin-CC1A1A?style=flat-square" alt="Marché" />
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

**N'NAKI — BZ Santé** est le portail numérique du Ministère de la Santé du Bénin pour la gestion souveraine de l'IA médicale, des données sanitaires et de la hiérarchie administrative du système de santé.

Déployé en production sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech), la plateforme connecte les directions départementales, les zones sanitaires, les établissements de santé, les experts médicaux contributeurs et les patients VIP sous protocole ministériel.

---

## Le problème

Le système de santé béninois fait face à plusieurs défis :
- Données de santé fragmentées et non sécurisées.
- Absence d'IA médicale souveraine adaptée au contexte local.
- Difficulté à suivre la hiérarchie administrative (12 directions, 34 zones sanitaires, établissements).
- Gestion confidentielle des dossiers VIP (hautes personnalités, diplomates).
- Manque d'outils de statistiques nationales et d'alertes épidémiques en temps réel.
- Nécessité de préserver les données de santé des Béninois sur le territoire national.

---

## La solution

N'NAKI propose un écosystème numérique 100% souverain composé de :

- **Portail ministériel** : dashboard central du Ministère de la Santé.
- **IA médicale N'NAKI** : base de connaissances validée par des experts médicaux béninois.
- **Hiérarchie administrative** : gestion des directions départementales, zones sanitaires et établissements.
- **Gestion VIP** : dossiers confidentiels des hautes personnalités avec contrôle d'accès strict.
- **Statistiques nationales** : indicateurs sanitaires complets, alertes épidémiques et export DHIS2.
- **Langues locales** : intégration du Fon, Yoruba, Dendi et autres langues pour l'accessibilité.
- **Gouvernance médicale** : protocoles, règles et directives officielles pour l'IA.

---

## Fonctionnalités principales

- **Hiérarchie administrative** : 12 directions départementales, 34 zones sanitaires, établissements de santé.
- **IA médicale souveraine** : base de connaissances, validation par pairs, contribution d'experts.
- **Espace contributeurs** : inscription, soumission de contributions, suivi des paiements.
- **Patients VIP** : gestion confidentielle avec niveaux d'accès (Président, Ministre, Député, Diplomate).
- **Gouvernance médicale** : protocoles de traitement, directives officielles, règles de l'IA.
- **Statistiques nationales** : consultations, pathologies, indicateurs maternels, infantiles, vaccination.
- **Alertes épidémiques** : surveillance et notification des épidémies en temps réel.
- **Export DHIS2** : compatibilité avec le système d'information sanitaire national.
- **Langues locales** : contribution et gouvernance linguistique pour l'accessibilité.
- **Sécurité souveraine** : données hébergées au Bénin, chiffrement, audit logs.

Pour plus de détails, consulter :
- [`docs/architecture.md`](docs/architecture.md)
- [`docs/features.md`](docs/features.md)
- [`docs/business-model.md`](docs/business-model.md)
- [`docs/api.md`](docs/api.md)
- [`docs/faq.md`](docs/faq.md)

---

## Architecture générale

N'NAKI repose sur une architecture web moderne, 100% souveraine et hébergée au Bénin :

- **Portail web** : HTML5, CSS3, JavaScript vanilla, Chart.js.
- **Dashboards** : interfaces dédiées par rôle (ministère, validateurs, contributeurs, réceptionnistes).
- **Base de connaissances IA** : validation par pairs (3/4 validateurs) avant intégration.
- **Stockage** : données sanitaires hébergées au Bénin, localStorage pour la démo, backend à venir.
- **Authentification** : contrôle d'accès par rôle, codes d'accès VIP, audit logs.
- **Exports** : DHIS2, PDF, Excel pour les rapports nationaux.
- **Déploiement** : hébergement souverain, accessible via [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## Technologies utilisées

### Frontend
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=for-the-badge&logo=chart.js&logoColor=white)

### Backend
> Roadmap v2.0 : migration vers Node.js / NestJS avec base de données PostgreSQL hébergée au Bénin.

### Outils
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

---

## Feuille de route

| Phase | Objectif | Statut |
| :--- | :--- | :--- |
| **Phase 1** | Portail web, hiérarchie administrative, statistiques nationales | Terminé |
| **Phase 2** | IA médicale, espace contributeurs, validation par pairs | Terminé |
| **Phase 3** | Gestion VIP, gouvernance médicale, langues locales | Terminé |
| **Phase 4** | Backend API, base de données centralisée, authentification | En cours |
| **Phase 5** | Mobile app, intégration terrain, synchronisation offline | À venir |
| **Phase 6** | Expansion nationale et intégration ministérielle complète | À venir |

Consulter [`ROADMAP.md`](ROADMAP.md) pour le détail.

---

## Captures d'écran

> Les captures d'écran seront ajoutées progressivement dans le dossier [`assets/screenshots/`](assets/screenshots/).

<div align="center">
  <img src="assets/screenshots/placeholder.svg" alt="Dashboard N'NAKI placeholder" width="80%" />
  <p><em>Dashboard N'NAKI — placeholder</em></p>
</div>

---

## Démo

Le portail de production est accessible sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## Liens officiels

- **Site web** : [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech)
- **Documentation** : [`docs/`](docs/)
- **Portfolio** : [stanislas-nouemou](https://github.com/odsystem-bit/stanislas-nouemou)
- **GitHub** : [bz-sante](https://github.com/odsystem-bit/bz-sante)

---

## Contact

Pour toute question, partenariat ou opportunité d'investissement :

- **Email** : [contact@odsysteme.tech](mailto:contact@odsysteme.tech)
- **LinkedIn** : [stanislas-nouemou](https://linkedin.com/in/)
- **GitHub** : [@odsystem-bit](https://github.com/odsystem-bit)

---

<div align="center">
  <sub>N'NAKI — La santé publique béninoise, numérisée et souveraine.</sub>
</div>
