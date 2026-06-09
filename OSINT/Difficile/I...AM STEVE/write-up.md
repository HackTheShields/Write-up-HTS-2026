# I...AM STEVE - Write-up

Nous disposons d'une vidéo, d'une image et d'une archive ZIP protégée.

1. **Recherche de la seed du monde** :
   - Nous analysons la vidéo pour repérer les structures du jeu (comme les villages) ainsi que leurs coordonnées exactes.
   - À l'aide d'un outil de recherche de seed comme `Cubiome Viewer`, nous saisissons les coordonnées observées des structures (avec une marge de $\pm 100$ blocs) et combinons cette recherche avec les biomes visibles dans la vidéo et sur l'image (*grove*, *ocean*, *frozen peaks*, *cherry grove*).
   - Nous lançons la recherche sur 48 bits pour retrouver la seed du monde : `50362068243`.
2. **Accès et exploration en jeu** :
   - La seed trouvée nous permet d'ouvrir l'archive ZIP protégée, qui contient un fichier de profil Modrinth (`.mrpack`).
   - Après installation, nous lançons le jeu pour retrouver l'emplacement du panneau montré dans la vidéo.
3. **Méthode alternative (NBT)** :
   - Nous pouvons également utiliser un éditeur de fichiers NBT (tel que `NBTExplorer`) pour inspecter directement les données du monde et extraire le texte du panneau (contenant le flag) sans avoir à explorer le jeu.

**FLAG** : `HTS{Herobrine_is_real}`