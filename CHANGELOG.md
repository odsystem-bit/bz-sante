# Changelog

Tous les changements notables de ce projet seront documentés dans ce fichier.

Le format est basé sur [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/),
et ce projet adhère à [Semantic Versioning](https://semver.org/lang/fr/).

## [0.3.0] - 2026-06-28

### Corrigé
- Refonte complète de la documentation pour refléter la réalité du projet : **BZ+** (Bureau de Zone Santé) et non N'NAKI.
- `README.md` : présentation BZ+, site web + application mobile, saisie SMI/DPalu/CER, rapports mensuels, tableau de bord admin, super administration, exports.
- `docs/features.md` : fonctionnalités réelles (saisie CS, admin, super admin, formulaires, mobile hors-ligne, statistiques, exports).
- `docs/architecture.md` : architecture Node.js/Express, SQLite, EJS, Flutter, hébergement Hostinger.
- `docs/business-model.md` : modèle économique autour des Bureaux de Zone et du déploiement multi-zone.
- `docs/api.md` : endpoints web et API mobile (saisie, sync, formulaires, config, export).
- `docs/faq.md` : FAQ corrigée avec les questions réelles des utilisateurs BZ+.
- `ROADMAP.md` : v1.0 prototype, v2.0 mobile, v2.1 ATZ en production, v2.2 multi-zone, v3.0 intégration nationale.

## [0.2.0] - 2026-06-28

### Mis à jour
- README.md : passage au statut "En production (v1.0)", ajout du site [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech), de la marque N'NAKI et de la vision souveraine.
- `docs/architecture.md` : architecture N'NAKI v1.0 (portail web, HTML/CSS/JS, Chart.js) et v2.0 (NestJS, PostgreSQL, Redis, DHIS2).
- `docs/features.md` : fonctionnalités réelles (portail ministériel, hiérarchie, IA, contributeurs, VIP, gouvernance, statistiques, langues locales).
- `docs/business-model.md` : modèle de revenus et stratégie de croissance N'NAKI.
- `docs/api.md` : endpoints internes v1.0 et roadmap API publique v2.0.
- `docs/faq.md` : FAQ enrichie avec les informations de production.
- `ROADMAP.md` : v1.0 terminée, v1.x consolidation, v2.0 backend, v2.1 mobile, v2.2 expansion nationale.

## [0.1.0] - 2026-06-28

### Ajouté
- Structure initiale du dépôt public.
- README.md professionnel avec présentation, architecture, technologies et roadmap.
- Documentation complète dans le dossier `docs/`.
- Fichiers de gouvernance : LICENSE, .gitignore, CONTRIBUTING.md, ROADMAP.md, SECURITY.md, CODE_OF_CONDUCT.md.
- Dossiers `assets/`, `demo/` et `presentations/`.

[0.2.0]: https://github.com/odsystem-bit/bz-sante/releases/tag/v0.2.0
[0.1.0]: https://github.com/odsystem-bit/bz-sante/releases/tag/v0.1.0
