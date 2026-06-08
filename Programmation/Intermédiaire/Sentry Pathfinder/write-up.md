# Sentry Pathfinder

Le serveur de drone nous envoie des labyrinthes générés en ASCII (avec des murs `#` et des chemins vides `.`). On doit trouver le chemin du point de départ `S` au point d'arrivée `E` et envoyer les directions (Nord, Sud, Est, Ouest : `N, S, E, W`). Il y a 20 niveaux de plus en plus grands, avec un temps limite strict de 2 secondes par carte.

Il faut scripter la résolution avec un algorithme de Pathfinding.
L'approche classique :
1. Lire les lignes envoyées par le serveur pour reconstituer le labyrinthe sous forme de matrice (tableau 2D).
2. Trouver les coordonnées (x,y) des caractères `S` et `E`.
3. Lancer un algorithme de recherche de chemin comme **BFS (Breadth-First Search)** pour explorer les cases vides jusqu'à atteindre `E`.
4. À chaque pas, mémoriser la direction prise (`N`, `S`, `E`, `W`).
5. Renvoyer la séquence finale de directions au serveur (ex: `NNESSWW...`).

Le Breadth-First Search (BFS) est parfait pour ce cas car il garantit de trouver le chemin le plus court dans une grille non pondérée. En passant les 20 niveaux sans crasher, le drone nous donne l'accès root.

**Flag:** `HTS{P4thf1nd1ng_A1g0_G0d_M0d3_On}`
