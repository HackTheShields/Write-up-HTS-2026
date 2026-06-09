# Le Fantôme dans le Commit

On nous donne une archive contenant un dépôt Git. Le descriptif nous indique qu'un fantôme (un secret supprimé) s'y cache.

1. **Recherche de commits cachés ou modifiés**
Si on tape `git log` pour voir l'historique de base, tout a l'air normal : on voit les commits "Initial project structure", "Add initial protocol documentation", etc. Il n'y a aucune trace d'un fichier suspect ou d'un flag.
Mais dans Git, l'historique peut être réécrit (via `rebase -i` ou `amend`). Les anciens commits ne disparaissent pas immédiatement, ils deviennent "inatteignables" (dangling commits).

2. **Utiliser Git Reflog**
Pour lister absolument toutes les actions faites localement, y compris les commits qui ont été retirés de l'arbre principal, on peut utiliser le journal de références :
```bash
git reflog
```
On va alors remarquer qu'un *rebase* a eu lieu dans l'historique, et on repérera le hash d'un vieux commit avec un message très explicite du type : `temp: Add credentials (REMOVE BEFORE PUSH)`.

3. **Lire le commit fantôme**
Une fois le hash de ce fameux commit retrouvé (ex: `a1b2c3d`), il suffit de regarder son contenu :
```bash
git show <hash_du_commit>
```

La commande affiche les différences introduites par ce vieux commit. On voit qu'un fichier nommé `credentials.txt.b64` avait été ajouté avant d'être supprimé plus tard.
Ce fichier contient une chaîne de caractères encodée en Base64.
Il ne reste plus qu'à copier cette chaîne et la décoder (`echo "..." | base64 -d`) pour récupérer le flag.

**Flag:** `HTS{G1T_N3V3R_F0RG3TS_R3B4S3}`
 