# L'image qui parle

Ce challenge web/misc nous met face à un système d'upload de mémos strict : il n'accepte que du texte sans balises suspectes (comme `{{ }}`) ou des images PNG valides.

Le but est d'exploiter une vulnérabilité d'injection de template (SSTI - Server-Side Template Injection) via Jinja2 ou similaire, trahie par l'interdiction de `{{ }}`. Cependant, le filtre de texte nous bloque si on l'envoie en texte brut. L'astuce est de contourner cette restriction en cachant le payload d'injection dans les métadonnées (EXIF) d'une image PNG !

1. **Création de l'image malveillante**
On prend une image PNG valide, puis on utilise un outil comme `exiftool` pour modifier ses métadonnées (par exemple, le champ "Comment" ou "Artist") et y insérer notre payload.
```bash
exiftool -Comment="{{ config }}" image.png
```
*(On peut aussi utiliser d'autres payloads selon l'environnement pour lire un fichier ou exécuter une commande).*

2. **Upload et Exploitation**
On uploade cette image PNG modifiée. Le filtre PIL-9000 vérifiera qu'il s'agit bien d'une vraie image (ce qui est le cas) et l'acceptera sans lire nos métadonnées malveillantes.

3. **Exécution du payload**
Lorsqu'on consulte notre mémo via `/view`, le serveur extrait et affiche les métadonnées de l'image dans son rendu. Si ce rendu utilise un moteur de template vulnérable, notre payload `{{ config }}` sera évalué, révélant ainsi les variables d'environnement ou la configuration du serveur où se trouve le flag !

**Flag:** `HTS{N0T_JUST_4N_1M4G3}`
