# Le Poids du Silence

On nous fournit une grosse image `node.png`. L'énoncé parle d'un fichier caché qui n'est pas détectable par les outils stéganographiques classiques comme `binwalk`, `zsteg` ou `strings`.

Quand l'outil classique de stéganographie LSB (Least Significant Bit) ne donne rien, c'est souvent que les bits de poids faible ne sont pas modifiés de manière linéaire de bout en bout, mais avec un algorithme spécifique. 

L'auteur du challenge a utilisé une librairie Python très courante : `stegano`.
On peut écrire un petit script pour révéler la donnée cachée :
```python
from stegano import lsb
secret = lsb.reveal("node.png")
print(secret)
```

Le script nous recrache une longue chaîne de caractères. En y regardant de plus près, on remarque que c'est du Base64.
Si on décode cette chaîne Base64 (ex: `echo "..." | base64 -d > payload.zip`), on obtient une archive ZIP valide.
En extrayant ce `payload.zip`, on découvre un fichier `flag.txt` qui contient la solution tant attendue.

**Flag:** `HTS{L34ST_S1GN1F1C4NT_FL4G}`
