# Bits par bits - Write-up

Nous avons analysé l'exécutable `sentry_boot`.

1. **Fonctionnement du binaire** : Nous constatons que le flag est dessiné dans un framebuffer virtuel en mémoire globale avant d'être effacé au bout de 50 ms par un `memset`.
2. **Interception mémoire** : Nous lançons le programme sous GDB, plaçons un point d'arrêt sur la fonction `usleep` juste avant l'effacement, puis dumpons la zone mémoire du framebuffer ($800 \times 600 \times 4$ octets).
3. **Restitution visuelle** : Nous chargeons le fichier dump dans GIMP en tant que données brutes (800x600, RGBA 32-bit) pour lire le flag.

**FLAG** : `HTS{BITS_VS_BYTES}`
 