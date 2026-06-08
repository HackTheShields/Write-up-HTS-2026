# Ghost Protocol

La description parle d'un système qui cache des documents aux bots d'indexation. Le premier réflexe dans ce genre de situation est d'aller consulter le fichier `robots.txt` à la racine du serveur.

En se rendant sur `http://<ip>:<port>/robots.txt`, on trouve ceci :

```text
User-agent: *
Disallow: /sector_007_backup/
```

Ce fichier demande aux moteurs de recherche de ne pas indexer le dossier `/sector_007_backup/`. Il suffit d'y accéder directement via l'URL pour tomber sur la page secrète qui contient le flag.

**Flag:** `HTS{R0b0ts_Txt_Is_N0t_A_S3cur1ty_M3asur3}`
