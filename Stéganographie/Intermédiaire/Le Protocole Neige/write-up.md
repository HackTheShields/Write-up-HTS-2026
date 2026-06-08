# Le Protocole Neige

On nous fournit un fichier texte `report.txt` qui a l'air vide ou banal, et l'énoncé indique que la donnée a été dissimulée dans "le blanc" ou "la neige" de l'interception. 

"Neige" et "blanc" sont de gros indices orientant vers **SNOW**, un outil de stéganographie qui cache des données en rajoutant des espaces et des tabulations invisibles en fin de ligne (Whitespace steganography).
La description nous oriente aussi vers la compression ("Neige compressée").

Il suffit d'installer et d'utiliser l'outil `snow` (ou `stegsnow` selon les distributions) sous Linux :
```bash
snow -C report.txt
```
L'option `-C` demande à l'outil de décompresser la donnée cachée extraite. Le fichier n'ayant pas été protégé par un mot de passe, l'outil affichera directement le message dissimulé dans le vide du texte.

**Flag:** `HTS{1NV1S1BL3_1NK}`
