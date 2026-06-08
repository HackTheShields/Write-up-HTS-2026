# Cerberus Gate

Le serveur nous envoie un algorithme de hachage (md5, sha1, ou sha256) et un hash, puis nous donne 2 secondes pour renvoyer le mot de passe en clair. Puisqu'il faut le faire 50 fois de suite, il est impossible de le faire à la main.

Il faut écrire un script (généralement en Python avec `pwntools` ou la librairie `socket`) pour automatiser la connexion.
Le script doit :
1. Lire le type de hash et la valeur demandée par le serveur.
2. Parcourir la `wordlist.txt` fournie.
3. Hacher chaque mot de la liste avec l'algorithme demandé jusqu'à trouver une correspondance.
4. Envoyer le mot trouvé au serveur.
5. Boucler cela 50 fois.

Une fois les 50 rounds passés avec succès, le serveur nous affiche le flag.

**Flag:** `HTS{Scr1pt1ng_Is_F4st3r_Th4n_Hum4ns}`
