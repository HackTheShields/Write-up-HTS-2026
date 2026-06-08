# Identity Nexus

Le portail nous assigne un badge temporaire de visiteur. Ce badge est stocké dans un cookie `session_token` et utilise le format classique des JWT (JSON Web Tokens).

Un JWT n'est pas chiffré (on peut le lire sur des sites comme jwt.io), mais il est signé. Le but est d'élever nos privilèges en modifiant notre rôle vers "admin", ce qui nécessite de re-signer le token modifié avec la bonne clé secrète.

L'énoncé donne un énorme indice : le secret est faible et lié au nom d'un des départements ("division Cortex"). 
Sur jwt.io :
1. On colle notre token de session.
2. Dans la section "PAYLOAD", on remplace `"role": "visitor"` par `"role": "admin"`.
3. Dans la section "VERIFY SIGNATURE", on entre le mot de passe deviné : `cortex`.

Le site génère instantanément notre nouveau token forgé avec la signature valide. On remplace notre cookie `session_token` par celui-ci via les outils de développement (Application > Cookies).

On recharge la page, le système nous reconnaît en tant qu'admin et affiche le flag.

**Flag:** `HTS{JwT_W34k_K3ys_Cr4ck_E4s1ly}`
