# Le Test de Turing Inversé - Write-up

Nous devons prouver notre humanité en résolvant trois épreuves interactives consécutives sous une contrainte de temps stricte (timeout de 15 à 25 secondes).

1. **Épreuve 1 (Reconnaissance de texte)** : Le système affiche un mot bruité sous forme d'ASCII Art. Nous lisons visuellement la chaîne (parmi *CRASH*, *HUMAN*, *SHIELD* ou *ORION*) et la saisissons en majuscules.
2. **Épreuve 2 (Labyrinthe ASCII)** : Une grille 5x5 est présentée. Nous trouvons le chemin le plus court reliant le départ `S` (0,0) à la sortie `E` (4,4) et entrons la suite de mouvements en français (`H`=Haut, `B`=Bas, `G`=Gauche, `D`=Droite).
3. **Épreuve 3 (Charade)** : Nous résolvons la charade phonétique liée au lore d'Orion pour valider la dernière étape :
   - meuh + thé + a -> `météore`
   - un + terre + net -> `internet`
   - nu + clé + air -> `nucléaire`

**FLAG** : `HTS{bip_boup_je_suis_un_vrai_robot}`
 