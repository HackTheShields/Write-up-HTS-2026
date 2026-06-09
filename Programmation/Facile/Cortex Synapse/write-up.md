# Cortex Synapse

Le supercalculateur Cortex nous inonde d'équations mathématiques basiques (additions, soustractions, multiplications) et nous donne 3 secondes pour répondre. Comme pour la plupart des challenges de programmation, il faut l'automatiser.

On peut faire un script Python avec la librairie `pwntools` ou `socket`.
Le but du script est de :
1. Se connecter au port avec `nc` programmatiquement.
2. Récupérer la ligne contenant l'équation.
3. Isoler l'opération (en ignorant le texte autour).
4. Utiliser la fonction `eval()` de Python pour calculer le résultat instantanément.
5. Renvoyer le résultat au serveur sous forme de chaîne de caractères.

En validant les 100 questions consécutives sans dépasser le délai de 3 secondes, Cortex nous valide l'accès et affiche le flag.

**Flag:** `HTS{ScR1pT1nG_M4sT3R_C0rT3X_0v3rL04D}`
 