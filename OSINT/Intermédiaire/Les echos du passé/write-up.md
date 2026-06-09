# Les échos du passé - Write-up

Nous débutons nos investigations à partir de l'adresse de messagerie `anna.duri@orion.local`.

1. **Recherche de la clé GPG** : Nous recherchons la clé GPG associée à cette adresse sur un serveur de clés public (comme *Ubuntu Keyserver*). Les informations de la clé nous renvoient vers un dépôt GitHub et un identifiant de commit spécifique.
2. **Récupération du commit fantôme** : En parcourant le dépôt GitHub, nous constatons que le commit indiqué dans la clé GPG n'apparaît plus dans l'historique public. En accédant manuellement à l'URL de ce commit orphelin (commit fantôme), nous récupérons une photographie.
3. **Extraction des métadonnées** : L'analyse des métadonnées de l'image révèle un bloc de données encodé en Base64 correspondant à une sauvegarde. Son décodage nous fournit un lien Pastebin.
4. **Consultation des archives** : Le lien Pastebin étant expiré ou inactif, nous interrogeons la *Wayback Machine* (Internet Archive) pour consulter la copie sauvegardée en février 2026 afin de lire le flag.

**FLAG** : `HTS{G0n3_But_N0t_F0rg0tt3n_4rch1v3s}` 