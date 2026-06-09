# Firmware ASHPD - Write-up

Nous analysons le fichier binaire `sentry_firmware.elf` extrait à l'étape précédente.

1. **Rétro-ingénierie du binaire** : Nous chargeons l'ELF dans Ghidra pour en inspecter le code décompilé.
2. **Identification de l'obfuscation** : Nous localisons la fonction de sécurité chargée de la vérification de la clé. Pour contourner la simple recherche via la commande `strings`, celle-ci reconstitue la clé dynamiquement en effectuant des opérations XOR successives en mémoire.
3. **Reconstitution de la clé** : Nous suivons l'arbre des opérations XOR et des constantes définies dans le code décompilé pour reconstituer manuellement (ou à l'aide d'un script Python) la chaîne décryptée.

**FLAG** : `HTS{APERTURE_GLADOS_X99}`
 