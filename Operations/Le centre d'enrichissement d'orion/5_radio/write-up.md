# La Radio 85.2 FM - Write-up

Nous analysons le fichier chiffré `radio_85_2_fm.enc` intercepté sur les ondes du centre.

1. **Étude du chiffrement** : Nous identifions que le flux a été obscurci par un chiffrement par flot (*Stream Cipher*) dont la suite pseudo-aléatoire est générée par un générateur congruentiel linéaire (LCG).
2. **Récupération des paramètres** : Nous utilisons la clé secrète récupérée lors de l'analyse du firmware (Challenge 4) comme graine d'initialisation (seed) du générateur.
3. **Déchiffrement** : Nous écrivons un script Python reproduisant l'algorithme LCG pour générer le flux d'octets de clé et appliquer un XOR inverse sur le fichier chiffré afin de retrouver le message original contenant le flag.

**FLAG** : `HTS{Str3am_C1ph3rs_Need_R4nd0m_IVs}`
 