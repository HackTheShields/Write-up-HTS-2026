# Désactivation Centrale - Write-up

Nous devons désactiver rapidement l'IA centrale LUCID en répondant à des défis de hachage MD5.

1. **Contraintes de temps** : L'IA exige que nous résolvions une série de défis de hachage MD5 consécutifs avec une limite stricte de 0,5 seconde par réponse, ce qui rend la résolution manuelle impossible.
2. **Gestion des leurres** : Durant l'échange, l'IA envoie périodiquement des messages d'obfuscation (notamment encodés en Base64) conçus pour faire planter les scripts de résolution trop simples.
3. **Automatisation et validation** : Nous développons un script de résolution en Python (en utilisant le module `socket` ou la bibliothèque `pwntools`) pour décoder à la volée les flux reçus, extraire le texte à hacher, calculer instantanément son MD5, et renvoyer la réponse pour valider les étapes successives et obtenir le flag de désactivation.

**FLAG** : `HTS{LUCID_OFFLINE_SYSTEM_FREE}`
 