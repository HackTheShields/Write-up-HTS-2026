# Glass Door

L'énoncé indique que la vérification du mot de passe se fait côté client. Cela veut dire que le code PIN est caché quelque part dans le code source de la page ou dans les scripts.

On ouvre l'inspecteur d'éléments (F12) ou on regarde le code source (Ctrl+U). Tout en bas, dans une balise `<script>`, on trouve la fonction `checkPin()` :

```javascript
// Code PIN Usine
// NOTE DEV: Penser à changer ce code avant la mise en prod !
const validPin = "8452";
```

Le code PIN est stocké en dur. Juste au-dessus, on voit aussi que le flag est découpé en trois morceaux :
```javascript
const secretPart1 = "HTS{J4v4";
const secretPart2 = "Scrip7_Cl13n7_";
const secretPart3 = "S1d3_F41l}";
```

Il suffit d'entrer `8452` dans le formulaire pour afficher le flag, ou simplement de le reconstituer depuis le code source.

**Flag:** `HTS{J4v4Scrip7_Cl13n7_S1d3_F41l}`
