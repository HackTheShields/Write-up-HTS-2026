# Get rotated - Write-up

Nous avons analysé l'image `deformed.png`.

1. **Analyse visuelle** : Nous constatons que l'image contient du bruit visuel. Cependant, le flag est directement lisible en clair en haut à gauche de l'image.
2. **Méthode attendue** : L'image a été chiffrée de manière réversible avec un XOR sur les positions `(x ^ y) % 256`. Nous aurions pu la restaurer en ré-appliquant cette opération sur chaque pixel.

**FLAG** : `HTS{r0t4t3d_sh4rk_x0r}` 