# Protocol Clear Skies

On doit interagir avec le panneau de contrôle d'un drone, mais l'accès est bloqué par une histoire de privilèges. 

Si on intercepte la requête vers le site (avec l'onglet Réseau/Network du navigateur ou via Burp Suite), on remarque une en-tête HTTP intéressante renvoyée par le serveur :

`X-Orion-Clearance: low`

Cela laisse penser que le système gère les droits via ce header. L'énoncé parle d'accéder aux "commandes de tir". On va donc forger une requête et envoyer cette même en-tête, mais avec une valeur plus élevée, comme `command`.

On peut le faire avec `curl` :
```bash
curl -H "X-Orion-Clearance: command" http://<ip>:<port>
```

Le serveur accepte l'élévation de privilèges et nous renvoie la page secrète du "Mission Feed", sur laquelle le flag est affiché en clair.

**Flag:** `HTS{H7tp_H3ad3rs_C0ntr0l_Tht_Dr0n3s}`
