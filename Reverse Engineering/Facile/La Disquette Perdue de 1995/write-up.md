# La Disquette Perdue de 1995 - Write-up

Nous avons analysé l'exécutable MS-DOS `keycheck.com`.

1. **Analyse du binaire** : Nous identifions une routine d'auto-déchiffrement de l'exécutable (*Self-Decrypting Code*) qui décode le code à l'offset 291 en effectuant un XOR cyclique avec la clé d'activation entrée par l'utilisateur.
2. **Attaque par texte clair connu** : Nous savons que si la clé est correcte, les instructions déchiffrées à l'offset 291 doivent exécuter l'affichage DOS standard (`mov ah, 09h; int 21h`) suivi de la chaîne `  [+] ACCESS GRANTED !`.
3. **Déchiffrement** : Nous appliquons un XOR entre les octets chiffrés à l'offset 291 et cette signature de texte clair connu (39 octets) afin de retrouver la clé originale.

**FLAG** : `HTS{retour_vers_le_futur_en_seize_bits}`
 