# L'Ombre d'Orion - Write-up

Nous avons analysé le Core Dump `orion_agent.core`.

1. **Réparation de l'en-tête ELF** : Nous constatons que la signature du fichier commence par `\x7fHTS`. Nous remplaçons ces octets par la signature standard `\x7fELF` (hex `7F 45 4C 46`) pour restaurer la validité du Core Dump.
2. **Extraction des métadonnées du système** : À l'aide de `readelf -n`, nous analysons la note `NT_PRSTATUS` pour récupérer :
   - Le PID (offset 40) : `4829`
   - L'Uptime (offset 56) : `1716942000`
3. **Génération de la clé** : Nous calculons la graine cryptographique via `PID ^ Uptime = 1716938349`. Nous dérivons la clé de chiffrement en calculant le SHA-256 de la chaîne de caractères correspondante.
4. **Déchiffrement RC4** : Nous localisons le segment Heap dans le Core Dump, ignorons les 128 octets d'en-tête `"HEAP_DUMP_ORION_AGENT"` et appliquons le déchiffrement RC4 avec la clé dérivée pour révéler le flag.

**FLAG** : `HTS{qui_a_eteint_mon_elfe_de_maison}`
