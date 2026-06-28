# FAQ BZ+ — Bureau de Zone Santé

## Général

### Qu'est-ce que BZ+ ?

**BZ+** (Bureau de Zone Santé) est un système de saisie et de supervision des données sanitaires conçu pour les Bureaux de Zone du Bénin. Il permet aux Centres de Santé (CS) de saisir leurs données quotidiennes et hebdomadaires, et aux Administrateurs de Zone de superviser, consulter et exporter ces données. Il est accessible sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

### Quel problème BZ+ résout-il ?

BZ+ résout la lenteur et les erreurs de la saisie papier, la difficulté de consolidation des données de plusieurs CS, les retards de remontée des rapports et le manque de visibilité en temps réel pour les administrateurs de zone.

### Qui peut utiliser BZ+ ?

- **Centre de Santé (CS)** : saisie des données SMI, DPalu, CER et rapports mensuels.
- **Administrateur de Zone** : supervision des CS, exports, statistiques et gestion des codes d'accès.
- **Super Administrateur** : gestion des zones, des CS, des administrateurs, configuration mobile et sauvegarde.

### BZ+ est-il déjà en ligne ?

Oui, la version 2.1 est en production pour le Bureau de Zone ATZ sur [bzsante.odsysteme.tech](https://bzsante.odsysteme.tech).

---

## Utilisation

### Comment se connecte un Centre de Santé ?

1. Ouvrez le site et cliquez sur **Accès Centre de Santé**.
2. Sélectionnez votre zone sanitaire.
3. Sélectionnez votre Centre de Santé.
4. Entrez le code d'accès à 6 chiffres fourni par votre administrateur.

### Quelles sont les données à saisir ?

- **SMI** : Santé Maternelle et Infantile (CPN, accouchements, enfants, planification familiale, etc.).
- **DPalu** : Registre Paludisme (dispensaire, maternité, ruptures de stock).
- **CER** : Surveillance épidémiologique hebdomadaire (28 maladies, décès, flambées, paludisme).
- **Rapports mensuels** : C6, PNLP1, MNT, C15.

### Comment corriger une saisie ?

Sélectionnez la même date et la même section. Les données existantes seront chargées et vous pourrez les modifier.

### L'application mobile fonctionne-t-elle sans internet ?

Oui, l'application BZ+ dispose d'un mode hors-ligne. Les saisies sont stockées localement et synchronisées automatiquement dès que la connexion revient. Le mode hors-ligne doit être activé par le Super Admin.

### Comment mettre à jour l'application mobile ?

Allez dans **Paramètres** → **Mise à jour** dans l'application. Si une nouvelle version est disponible, téléchargez et installez l'APK. Le Super Admin peut aussi publier une mise à jour depuis le panneau **Upload APK**.

---

## Sécurité et confidentialité

### Les données de santé sont-elles protégées ?

Oui, BZ+ applique :
- Le HTTPS forcé en production.
- La protection des sessions (httpOnly, sameSite).
- Le rate limiting et la protection CSRF.
- Les headers de sécurité via Helmet.
- Les codes d'accès CS et les mots de passe admin.
- Le blocage après 5 tentatives de connexion échouées.

### Où sont hébergées les données ?

La base de données SQLite est hébergée sur le serveur de production (Hostinger). Les sauvegardes sont disponibles depuis le panneau Super Admin.

### Qui a accès aux données ?

Seuls les utilisateurs autorisés selon leur rôle peuvent accéder aux données :
- Un CS ne voit que ses propres données.
- Un admin de zone voit les données de tous les CS de sa zone.
- Un Super Admin gère la structure et la configuration.

### Comment récupérer son code d'accès CS ?

Contactez votre administrateur de zone. Il peut voir et modifier votre code dans **Paramètres → Codes d'accès**.

---

## Support et contact

### Comment contacter l'équipe ?

Vous pouvez nous contacter via les coordonnées disponibles dans le [`README.md`](../README.md).

### Où trouver la documentation technique ?

La documentation est disponible dans le dossier [`docs/`](./) et dans le fichier [`DOCUMENTATION_UTILISATION.md`](https://github.com/odsystem-bit/bz-sante/blob/main/DOCUMENTATION_UTILISATION.md) du dépôt.

---

## Questions non listées ?

Ouvrez une issue sur GitHub ou contactez-nous directement. Nous enrichirons cette FAQ au fur et à mesure des retours.
