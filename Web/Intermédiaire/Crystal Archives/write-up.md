# Crystal Archives

Le challenge présente une barre de recherche pour consulter les "blueprints" d'armes. L'énoncé mentionne aussi que l'admin a stocké ses identifiants dans une table `users`. On est clairement sur une injection SQL.

La recherche est vulnérable aux injections UNION. En testant le nombre de colonnes retournées par la requête originelle, on se rend compte qu'il y en a 4 (ex: ID, nom, description, danger).

On va forger une requête pour extraire les données de la table `users`. L'utilisateur ciblé est `k.voss`.

Payload à entrer dans la barre de recherche :
`' UNION SELECT id, username, password, 1 FROM users -- `

Cette payload va :
- `'` : fermer la chaîne de recherche en cours.
- `UNION SELECT ...` : ajouter le résultat de notre propre requête (4 colonnes, le `1` sert juste de remplissage).
- `-- ` : commenter la suite de la requête prévue par le serveur.

Les résultats s'affichent à l'écran, et le mot de passe de `k.voss` apparaît directement dans la colonne de description.

**Flag:** `HTS{Un10n_S3l3c7_1s_P0w3rful}`
 