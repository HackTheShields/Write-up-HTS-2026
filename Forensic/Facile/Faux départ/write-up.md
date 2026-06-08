# Faux départ - Write-up

Nous avons analysé l'image corrompue `crash_dump.png`.

1. **Identification de la corruption** : L'image ne peut pas être ouverte directement. Nous l'ouvrons dans un éditeur hexadécimal pour inspecter sa structure.
2. **Restauration des signatures** : Nous remarquons que les en-têtes du fichier ont été modifiés par les chaînes `ORION_V4` et `D3AD`. Nous les remplaçons respectivement par la signature magique PNG standard (`89 50 4E 47 0D 0A 1A 0A`) et l'identifiant du chunk `IHDR` (`49 48 44 52`).
3. **Lecture du flag** : Une fois les signatures restaurées et le fichier sauvegardé, l'image s'ouvre correctement et affiche le flag.

**FLAG** : `HTS{le_coup_de_la_panne}`