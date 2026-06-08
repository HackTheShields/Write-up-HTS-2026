# Protocol Chameleon

Ce serveur change de méthode d'encodage (Base64, Hexadécimal, ROT13, Inversion ou Binaire) à chaque message envoyé. Il y a 50 rounds à réussir en moins de 3 secondes chacun.

Le script à écrire en Python (via `socket` ou `pwntools`) doit agir comme un routeur polyvalent :
1. Lire la méthode annoncée (ex: `Type: base64`).
2. Lire les données (`Data: ...`).
3. Appliquer la fonction de décodage appropriée selon le type détecté (`base64.b64decode`, `bytes.fromhex`, `codecs.decode(..., 'rot_13')`, inverser la chaîne, ou convertir le binaire en ASCII).
4. Envoyer la réponse en clair.

Une fois la boucle automatisée réussie 50 fois de suite, le serveur lâche le flag.

**Flag:** `HTS{P0lym0rph1c_C0d3_Br34k3r_V2}`
