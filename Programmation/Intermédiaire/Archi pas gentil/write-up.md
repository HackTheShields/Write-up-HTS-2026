# Archi pas gentil - Write-up

Nous devons concevoir un interpréteur de machine virtuelle en moins d'une seconde pour résoudre un bytecode hexadécimal fourni lors d'une connexion réseau.

1. **Rétro-ingénierie du jeu d'instructions** : Nous analysons la spécification d'instructions du processeur propriétaire *Synapse V4* (comportant des opcodes comme `0x10` pour PUSH, `0x20` pour ADD, `0x40` pour JZ ou `0xFF` pour HALT).
2. **Développement de l'émulateur** : Nous écrivons un script Python (utilisant `socket` ou `pwntools`) pour parser la suite d'octets reçue, simuler la pile LIFO, l'accumulateur (ACC) et le pointeur d'instruction (IP) selon les règles de saut relatif.
3. **Résolution rapide** : Notre script interprète le bytecode reçu, calcule la valeur finale de l'accumulateur au moment de l'instruction `HALT`, et la renvoie immédiatement au serveur pour valider l'épreuve.

**FLAG** : `HTS{VMware>VirtualBox}`
 