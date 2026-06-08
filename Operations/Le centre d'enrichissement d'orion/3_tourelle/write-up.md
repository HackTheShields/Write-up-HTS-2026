# Tourelle Défectueuse - Write-up

Nous disposons d'un dump mémoire `turret_dump.bin` issu d'une tourelle défectueuse.

1. **Inspection hexadécimale** : Nous ouvrons le dump dans un éditeur hexadécimal et repérons la structure d'une archive compressée. Nous constatons que les octets magiques d'en-tête sont corrompus (remplacés par `00 00`).
2. **Restauration de la signature** : Nous remplaçons les premiers octets par la signature standard ZIP `50 4B` (`PK`).
3. **Extraction** : L'archive ainsi réparée s'extrait correctement avec `unzip`, nous révélant le fichier `sentry_firmware.elf` et validant l'étape.

**FLAG** : `HTS{B1nw4lk_S33s_Ev3ryth1ng}`
