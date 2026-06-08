# The Cake is a Lie - Write-up

Nous devons élever nos privilèges sur l'application web pour obtenir une habilitation superviseur.

1. **Analyse du cookie de session** : En nous enregistrant en tant qu'invité (*Guest*), nous obtenons un cookie `access_token` au format JSON Web Token (JWT).
2. **Attaque par brute-force sur la clé** : Nous extrayons le token et tentons de casser sa signature à l'aide de `john` ou `hashcat` avec un dictionnaire. Nous découvrons la clé secrète faible : `sentry123` (ou `cake`).
3. **Usurpation de rôle (Forgery)** : En utilisant ce secret, nous forgeons un nouveau JWT contenant la charge utile `{"user": "chell", "role": "admin"}`. En remplaçant notre cookie par ce nouveau token signé, nous accédons au tableau de bord administrateur et récupérons le flag.

**FLAG** : `HTS{W34k_S3cr3ts_Br34k_JWT}`
