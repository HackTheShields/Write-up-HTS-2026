# Crash de l'Aigle Orion - Write-up

Nous avons analysé l'image disque `blackbox_evil.img` du drone Orion.

1. **Analyse de la table d'allocation** : En inspectant le fichier brut, nous repérons l'entrée correspondant au fichier `FLIGHT_REC.LOG`. Nous constatons que son champ *Size* est nul (`0x00000000`).
2. **Récupération des données** : Comme indiqué dans la spécification technique de maintenance en cas de crash, nous lisons les données brutes à partir de l'offset du fichier jusqu'à rencontrer le marqueur de fin de secteur `EE 0F EE 0F`.
3. **Déchiffrement** : Le flag de chiffrement étant activé (`0x01`), nous déchiffrons les données en appliquant un XOR cyclique à l'aide de la clé dérivée de l'offset du fichier encodé sur 32-bits en Little Endian.

**FLAG** : `HTS{AI_C4nt_D3bug_Br0k3n_H3ad3rs}`
 