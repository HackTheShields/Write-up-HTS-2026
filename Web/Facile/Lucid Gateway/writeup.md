# Lucid Gateway

Le challenge parle d'une passerelle mal configurée par un admin distrait. Le serveur est un Nginx et on nous laisse entendre que l'on peut accéder à sa configuration.

Quand on regarde le fonctionnement du site, on remarque un comportement bizarre ou on devine que le serveur est mal sécurisé au niveau de ses dossiers. L'indice indique que l'admin a mis le `root` sur `/etc/nginx`.

Les fichiers de conf Nginx se trouvent généralement dans `/etc/nginx/conf.d/` et le fichier principal s'appelle souvent `default.conf`. Puisque la racine pointe sur `/etc/nginx`, on peut simplement récupérer la configuration en accédant à :

`http://<ip>:5000/conf.d/default.conf`

Le fichier s'affiche en clair dans le navigateur et on trouve le flag en commentaire tout en bas :

```nginx
# Backup Flag pour accès urgence LUCID :
# HTS{LUC1D_S33s_Ev3ryth1ng_Ev3n_Y0ur_R00t_P4th}
```

**Flag:** `HTS{LUC1D_S33s_Ev3ryth1ng_Ev3n_Y0ur_R00t_P4th}`
