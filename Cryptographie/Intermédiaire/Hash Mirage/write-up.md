# Hash Mirage

Le challenge nous demande d'uploader un fichier qui possède le même hash MD5 qu'un fichier de référence ("fileA"), mais un hash SHA-256 différent pour prouver qu'il a été modifié.

Il s'agit d'une attaque par collision MD5. L'algorithme MD5 est cassé depuis longtemps et il est mathématiquement possible de générer deux fichiers distincts qui produiront exactement la même empreinte MD5.

La méthode la plus directe est d'utiliser un outil spécialisé pour forger ces collisions, comme **FastColl** ou **HashClash**.
- L'outil va prendre le fichier d'origine et générer deux variantes contenant des blocs de données poubelles (invisibles) différents.
- Ces blocs de bits sont précisément calculés pour que, bien que les fichiers soient différents octet par octet (ce que confirme inévitablement un SHA-256 différent), l'algorithme de hachage MD5 produise la même signature finale pour les deux fichiers.

En uploadant l'un des fichiers générés par cet outil sur le portail, le système validera la vérification d'intégrité MD5 tout en reconnaissant que le fichier est un "nouveau" fichier via son SHA-256.

**Flag:** `HTS{H4sh_M1r4g3_D3t3ct3d}`
