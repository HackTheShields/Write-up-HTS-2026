# Le jeu des 2 différences - Write-up

Nous avons analysé les images `vert_1.png` et `vert_2.png`.

1. **Superposition des images** : Nous utilisons l'outil `stegsolve` pour combiner et superposer les deux images d'apparence similaire.
2. **Extraction de la différence** : En appliquant un opérateur de différence de pixels (XOR ou Image Combiner dans StegSolve), le flag se dessine à l'écran. Des outils en ligne comme AperiSolve auraient également pu être employés.

**FLAG** : `HTS{0r4ng3_1s_th3_n3w_gr33n}` 