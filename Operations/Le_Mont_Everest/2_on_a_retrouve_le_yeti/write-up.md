# On a retrouvé le Yeti - Write-up

Nous analysons les fichiers disponibles sur le serveur FTP.

1. **Récupération des fichiers** : Nous téléchargeons un fichier texte `.txt` en clair et une archive compressée `.zip`.
2. **Identification de l'attaque** : En inspectant le contenu de l'archive ZIP, nous constatons qu'elle contient le même fichier texte en clair. Nous faisons face à une attaque par texte clair connu (*Known Plaintext Attack*).
3. **Exploitation** : Nous utilisons l'outil `bkcrack` avec le fichier texte en clair pour dériver les clés de chiffrement de l'archive ZIP.
4. **Déchiffrement et obtention du flag** : Grâce aux clés identifiées, nous générons une nouvelle archive déchiffrée ou avec un mot de passe connu, nous permettant d'extraire le fichier et de lire le flag.

**FLAG** : `HTS{In0x_3t_S0n_Ch4p3au_D3_Pa1ll3}` 