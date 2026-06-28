# Roadmap BZ+ — Bureau de Zone Santé

Cette feuille de route présente les grandes étapes de développement de **BZ+**, de la v1.0 au déploiement national.

---

## v1.0 — Prototype de saisie web

**Objectif** : valider la saisie numérique des données sanitaires dans un Bureau de Zone.

- [x] Saisie web SMI et DPalu.
- [x] Structure SQLite fidèle aux registres Excel.
- [x] Export Excel basique.

---

## v2.0 — Application mobile et formulaires

**Objectif** : étendre la saisie sur le terrain avec l'application Android.

- [x] Application mobile BZ+ (Flutter).
- [x] Saisie hors-ligne avec stockage local.
- [x] Synchronisation différée avec le serveur.
- [x] Formulaires personnalisés (web + mobile).
- [x] Gestion des tokens API et configuration distante.

---

## v2.1 — Déploiement ATZ en production

**Objectif** : déployer et stabiliser le système pour la Zone Sanitaire Allada-Toffo-Zè.

- [x] Site web déployé sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).
- [x] Tableau de bord administrateur.
- [x] Statistiques, alertes et classement des CS.
- [x] Surveillance CER et rapports mensuels (C6, PNLP1, MNT, C15).
- [x] Export Excel et PDF.
- [x] Gestion des codes d'accès et formulaires.
- [x] Super administration : zones, CS, admins, config mobile, APK, backup.
- [x] Sécurité : sessions, rate limiting, HTTPS, Helmet, CSP.

---

## v2.2 — Multi-zone et cloud

**Objectif** : généraliser le déploiement à plusieurs Bureaux de Zone.

- [ ] Gestion multi-tenant.
- [ ] Synchronisation cloud et base de données centralisée.
- [ ] Amélioration du mode hors-ligne (sync automatique, gestion des conflits).
- [ ] Notifications automatiques (alertes CER, rappels de saisie).

---

## v3.0 — Intégration nationale

**Objectif** : connecter BZ+ aux systèmes d'information sanitaires nationaux.

- [ ] Export DHIS2 / SIGASI.
- [ ] Tableaux de bord pour les directions départementales.
- [ ] API publique pour les intégrations partenaires.
- [ ] Formation et support à grande échelle.

---

<div align="center">
  <sub>Dernière mise à jour : juin 2026</sub>
</div>
