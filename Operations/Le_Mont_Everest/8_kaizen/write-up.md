# KAIZEN - Write-up

Nous sommes connectés en SSH en tant que l'utilisateur `Manish`.

1. **Analyse du binaire SUID** : Nous identifions le binaire `/usr/local/bin/chapeau_de_paille` possédant les permissions SUID de root. L'analyse du code source montre que la variable `key` (située juste après un buffer de 64 octets) doit être écrasée avec la valeur `0xcafebabe` pour ouvrir un shell privilégié.
2. **Exploitation (Buffer Overflow)** : Nous exploitons l'utilisation de `fgets` pour injecter 64 octets de padding suivis de la valeur cible `0xcafebabe` représentée en Little Endian (`\xbe\xba\xfe\xca`).
3. **Maintien du shell privilégie** : Nous chaînons l'entrée standard avec `cat` pour conserver l'accès au shell et pouvoir lire le fichier `/root/root_flag.txt` :
   ```bash
   (python3 -c 'import sys; sys.stdout.buffer.write(b"A"*64 + b"\xbe\xba\xfe\xca\n")'; cat) | /usr/local/bin/chapeau_de_paille
   ```

**FLAG** : `HTS{inoxtag_le_boss}`
