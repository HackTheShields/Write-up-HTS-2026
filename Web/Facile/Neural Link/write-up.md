# Neural Link

On a affaire à une page web avec un script obfusqué généré par l'IA "Cortex". 

En ouvrant le code source, on tombe sur un tableau contenant plusieurs chaînes de caractères en hexadécimal :

```javascript
var _0x5a21=["\x48\x54\x53\x7b\x4a\x34\x76\x34\x53\x63\x72\x31\x70\x37\x5f\x30\x62\x66\x75\x73\x63\x34\x74\x31\x30\x6e\x5f\x31\x73\x5f\x4e\x30\x74\x5f\x53\x33\x63\x75\x72\x31\x74\x79\x7d", ...];
```

La première chaîne commence par `\x48\x54\x53\x7b`, ce qui correspond à `HTS{` en ASCII. 
Puisque le navigateur sait lire ce format nativement, il suffit de copier toute cette chaîne et de la coller dans la console JavaScript (F12) puis d'appuyer sur Entrée.

La console l'interprète et affiche directement la chaîne en clair :

`"HTS{J4v4Scr1p7_0bfusc4t10n_1s_N0t_S3cur1ty}"`

On peut aussi la rentrer dans le formulaire pour vérifier que c'est bien la bonne clé neurale.

**Flag:** `HTS{J4v4Scr1p7_0bfusc4t10n_1s_N0t_S3cur1ty}`
 