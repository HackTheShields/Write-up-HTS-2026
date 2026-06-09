# Le Hash Révélateur

Le scénario décrit un dev qui a malencontreusement pushé un secret, puis qui a tenté de l'effacer en réécrivant l'historique Git. On nous donne une archive `.zip` contenant le dépôt.

Même si le commit a été "supprimé" (via un rebase ou un reset), il traîne encore dans la base de données interne de Git. On appelle ça un "dangling commit".

1. **Trouver la piste**
Sur le site web de test, si on cherche des chemins cachés ou qu'on génère des erreurs, on peut tomber sur l'endpoint `/debug`.
Celui-ci expose plusieurs informations, dont un `buildId` (ex: `"buildId": "YTIzYmQw..."`) et potentiellement un header `X-Build-Hash`.
Le `buildId` est en Base64. Une fois décodé, on obtient un hash de commit Git.

2. **Fouiller l'historique**
On extrait l'archive fournie (`orion_verifier.zip`).
Dans ce dossier, on peut chercher ce commit fantôme.
Si on a trouvé le hash sur le site web, on peut l'inspecter directement :
```bash
git show <le_hash>
```

*(Alternativement, on pouvait aussi lister tout l'historique des modifications locales avec `git reflog` pour repérer un vieux commit d'ajout de mot de passe).*

La commande affiche le patch (les lignes ajoutées/retirées) du commit supprimé, révélant le flag en clair.

**Flag:** `HTS{G1T_R3V34LS_TH3_P4ST}`
 