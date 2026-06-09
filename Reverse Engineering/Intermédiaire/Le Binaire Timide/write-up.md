# Le Binaire Timide

On nous donne un binaire nommé `crackme`. Il demande un code d'accès à 6 caractères, mais l'analyse statique classique ou dynamique montre un comportement très étrange : il refuse de s'exécuter correctement sous débuggeur (GDB).

1. **Anti-Debugging et Code Automodifiable (SMC)**
En ouvrant le binaire dans Ghidra ou avec `objdump`, on remarque plusieurs choses :
- Le programme fait appel à l'instruction `rdtsc` pour lire le compteur de cycles du processeur avant et après une petite boucle. S'il s'aperçoit que la boucle a mis trop de temps à s'exécuter (ce qui arrive forcément quand un humain fait du pas-à-pas dans GDB), il change la valeur d'un registre clé (de `0x42` à `0x99`).
- Le programme utilise le syscall `mprotect` pour rendre une zone mémoire exécutable.
- Il fait ensuite un XOR sur une fonction encodée avec la valeur décidée précédemment (`0x42` si tout va bien, `0x99` si on le débugge).
- Enfin, il appelle cette fonction déchiffrée en mémoire.

Si on le lance sous GDB, la fonction est mal déchiffrée et le programme plante ou rate.

2. **Déchiffrer la fonction de vérification**
L'objectif est d'extraire la fonction chiffrée depuis le binaire et de la déchiffrer avec la bonne clé (`0x42`) pour comprendre comment le mot de passe est validé.
On extrait les bytes de la fonction et on les XOR avec `0x42` (via un script Python par exemple). On obtient le shellcode de validation.
En le désassemblant, on découvre l'algorithme :
- Il vérifie la longueur (6 caractères).
- Il fait une boucle sur chaque caractère : `(caractere ^ (0x11 * (index + 1)))`.
- Il additionne tous ces résultats.
- Si la somme finale est égale à `0x1D3` (soit 467 en décimal), c'est gagné.

3. **Générer un mot de passe valide**
Puisque le programme vérifie seulement la "somme" des caractères manipulés, il existe de nombreuses combinaisons de mots de passe valides ! Il suffit d'écrire un petit script Python pour trouver 6 caractères imprimables qui satisfont l'équation.

En fournissant n'importe lequel de ces mots de passe valides sur l'instance distante (netcat), le serveur nous récompense en imprimant le flag !

**Flag:** `HTS{TH3_SHY_B1NARY}`
 