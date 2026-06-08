# Oxygène : 0% (Manish à l'aide !) - Write-up

Nous avons obtenu le condensat de hachage du mot de passe de Manish.

1. **Extraction du hash** : Nous récupérons le hash du compte de `manish` extrait de `/etc/shadow` lors de l'étape précédente.
2. **Attaque par dictionnaire** : Nous utilisons un outil de cassage (tel que `john` ou `hashcat`) avec la wordlist `rockyou.txt` pour retrouver le mot de passe en clair.
3. **Obtention du flag** : Le mot de passe identifié (`abygurl69`) nous permet de valider le challenge.

**FLAG** : `HTS{abygurl69}`
