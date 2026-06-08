# Salle de Test 01 - Write-up

Nous avons cherché à accéder au serveur de développement du centre.

1. **Inspection du code source** : Nous analysons le code HTML de la page d'accueil et découvrons un commentaire menant à l'URL `/api/v1/healthcheck`.
2. **Découverte du routage interne** : En visitant cette API, nous récupérons un JSON indiquant l'hôte interne `"dev-sentry-alpha.orion.int"`.
3. **Modification d'hôte** : Nous re-saisissons la requête en modifiant le header `Host` (ou en ajoutant l'entrée dans `/etc/hosts`) pour pointer vers `dev-sentry-alpha.orion.int`. La page d'accueil de ce nouvel hôte virtuel nous donne le flag.

**FLAG** : `HTS{V1rtual_H0sts_Ar3_N0t_S3cur3}`
