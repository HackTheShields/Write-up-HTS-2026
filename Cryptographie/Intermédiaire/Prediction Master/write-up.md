# Prediction Master

Ce service nous fournit 5 nombres générés aléatoirement et nous met au défi de prédire le 6ème. L'énoncé précise qu'il utilise "Math.random()", la fonction native de JavaScript/Node.js.

En réalité, `Math.random()` dans le moteur V8 (Chrome, Node.js) n'utilise pas un véritable générateur de nombres aléatoires, mais un générateur "pseudo-aléatoire" (PRNG) basé sur l'algorithme **XorShift128+**. 

Cet algorithme n'est pas "cryptographiquement sécurisé". Son état interne est conservé sur 128 bits (répartis dans deux variables, `state0` et `state1`). Si on observe suffisamment de sorties consécutives (généralement 5 suffisent pour du XorShift128+ sous V8), il est mathématiquement possible de résoudre le système d'équations pour retrouver l'état interne exact du générateur !

**Exploitation :**
1. On récupère les 5 premiers nombres donnés par le serveur.
2. On utilise un solveur mathématique comme **Z3 Theorem Prover** en Python, qui est très puissant pour résoudre des contraintes sur des bits.
3. En modélisant le comportement bit à bit (opérations logiques XOR, décalages) de XorShift128+ et en injectant les 5 valeurs en contraintes, Z3 retrouvera la valeur initiale exacte des registres `state0` et `state1`.
4. À partir de là, on peut simuler de notre côté le tour de boucle suivant pour calculer exactement le 6ème nombre avant même qu'il ne soit généré !

En soumettant cette prédiction parfaite au serveur, on obtient le flag.

**Flag:** `HTS{R4nD0m_1s_Pr3d1ct1ble}`
