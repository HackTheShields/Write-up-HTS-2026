# Core Meltdown

On nous donne un accès `nc` à un serveur, ainsi qu'un binaire Linux `reactor` à télécharger. 
En lançant le binaire ou en se connectant via netcat, on se rend compte qu'il s'agit d'un jeu des Tours de Hanoï en version ASCII art (avec 3 disques).

Il y a deux façons de résoudre ce challenge :

**Méthode 1 : Jouer le jeu (La voie prévue / "Legit")**
Puisqu'il n'y a que 3 disques, résoudre les Tours de Hanoï est très rapide à la main. Il suffit de déplacer les disques de la tour 1 à la tour 3 en respectant les règles (ne jamais mettre un grand disque sur un petit).
Une fois le puzzle résolu, le jeu nous affiche directement le flag de victoire.

**Méthode 2 : Reverse Engineering (La voie du Hacker)**
On peut ouvrir le binaire téléchargé dans un désassembleur/décompilateur comme Ghidra, IDA ou Cutter.
En cherchant les chaînes de caractères (strings) ou en regardant les fonctions, on trouve rapidement une fonction `print_flag` (ou similaire) appelée à la fin du jeu.
Le flag n'est pas stocké en clair pour éviter d'utiliser simplement la commande `strings`, il est stocké sous forme de tableau de caractères (bytes).
En regardant la décompilation de la fonction, on voit la construction du tableau :
`char f[] = {83, 72, 73, 69, 76, 68, 83, 123, 72, 52, ...}`
Il suffit de convertir ces codes décimaux ou hexadécimaux en caractères ASCII : `83`->`S`, `72`->`H`, `73`->`I`, etc.
Ce qui nous donne la chaîne de caractères.

**Flag:** `HTS{H4n0i_T0w3rs_Ov3rl04d}`
 