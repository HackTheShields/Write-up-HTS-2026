# Houston on a marché sur la lune - Write-up

Nous avons analysé le fichier audio `emergency_beacon.wav`.

1. **Identification du protocole** : La description du challenge fait référence à un protocole de transmission radio historique, le SSTV (Slow Scan Television).
2. **Décodage du signal** : Nous passons le signal audio dans un décodeur SSTV (comme l'outil en ligne *online sstv decoder*) pour reconstituer l'image transmise contenant le flag.

**FLAG** : `HTS{SSTV_1s_C00l}`