# Le Poids du Silence

On nous fournit une grosse image `node.png`. L'énoncé parle d'un fichier caché qui n'est pas détectable par les outils stéganographiques classiques comme `binwalk`, `zsteg` ou `strings`.

Quand l'outil classique de stéganographie LSB (Least Significant Bit) ne donne rien, c'est souvent que les bits de poids faible ne sont pas modifiés de manière linéaire de bout en bout, mais avec un algorithme spécifique. 

L'auteur du challenge a utilisé une méthode d'encodage spécifique (générateur de nombres premiers, type Eratosthène), qui perturbe certains outils basiques, mais qui est parfaitement reconnue par un outil d'analyse stéganographique avancé comme **zsteg**.

Il suffit d'installer et de lancer `zsteg` sur l'image :
```bash
zsteg -a node.png
```

L'outil va analyser l'image sous tous les angles et finira par trouver une donnée cachée sous forme de longue chaîne en Base64.
Si on décode cette chaîne Base64 (`echo "..." | base64 -d > payload.zip`), on obtient une archive ZIP valide.
En extrayant ce `payload.zip`, on découvre un fichier `flag.txt` qui contient la solution tant attendue.

**Flag:** `HTS{ZST3G_F1NDS_3V3RYTH1NG}`
