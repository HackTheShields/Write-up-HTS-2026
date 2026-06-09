# Eclipse

On arrive sur une page web avec un rendu 3D, mais l'écran est complètement noir. Le texte précise que le monolithe est là mais que l'éclairage est au minimum. 

Le site utilise la librairie Three.js, tout le code s'exécute côté client, on a donc la main sur la scène 3D via la console du navigateur.

En ouvrant la console (F12), on peut inspecter les variables globales. On y trouve `light` et `scene`.

Pour voir ce qu'il se passe, on augmente simplement l'intensité de la lumière :
```javascript
light.intensity = 10;
```

L'écran s'illumine. On peut désormais observer le monolithe 3D et lire le flag qui est inscrit dessus en vert fluo. 
*(Une autre solution consiste à modifier le `material` de l'objet pour utiliser un `MeshBasicMaterial` insensible à la lumière).*

**Flag:** `HTS{Sh4d0ws_C4nt_b3_Scr1pt3d}`
 