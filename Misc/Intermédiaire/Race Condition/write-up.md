# Race Condition

Le portail valide et exécute des scripts Bash (fichiers `.sh`). Le script passe d'abord par un "Gardien" (vérification) puis est exécuté. Si le gardien détecte des commandes comme `cat`, `ls` ou `flag`, il rejette le script.

Ceci est une vulnérabilité classique nommée **TOCTOU** (Time-Of-Check to Time-Of-Use). Il y a un petit délai (une "course") entre le moment où le fichier est vérifié par le gardien et le moment où il est exécuté.

L'objectif est d'exploiter cette fenêtre de tir très courte :
1. On crée un script inoffensif (ex: `gentil.sh` contenant `echo "hello"`).
2. On crée un script malveillant (ex: `mechant.sh` contenant `cat /flag.txt`).

Puisqu'un script Python gère généralement mal la concurrence, on va inonder le serveur de requêtes simultanées en uploadant très rapidement le `gentil.sh` (pour passer la vérification) et le `mechant.sh` sous le **même nom de fichier distant**.
Si le timing est bon :
- Le serveur vérifie le fichier inoffensif et le valide.
- Juste après la validation, notre autre requête écrase le fichier avec le contenu du script malveillant.
- Le serveur exécute le fichier (pensant qu'il s'agit du script inoffensif validé à l'étape précédente).
- Le script `cat /flag.txt` est exécuté !

On peut automatiser cette attaque avec un petit script en Python (utilisant la librairie `requests` et le module `threading`) pour lancer plusieurs requêtes simultanées. Au bout de quelques tentatives, le serveur retournera le contenu du flag !

**Flag:** `HTS{W0N_TH3_R4C3}`
 