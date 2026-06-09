# L'Automate Émoji d'Orion - Write-up

Nous devons inverser une chaîne de caractères lue caractère par caractère sur l'entrée standard en utilisant un interpréteur ésotérique basé sur une pile (Stack) et des émojis.

1. **Logique de la pile (LIFO)** : Étant donné le fonctionnement en dernier entré, premier sorti d'une pile, empiler successivement chaque lettre lue jusqu'au délimiteur de fin `0` puis les dépiler et les afficher une par une permet d'inverser naturellement la chaîne.
2. **Construction du script** : Nous écrivons le script optimal combinant l'initialisation du sentinel `0`, la boucle de lecture conditionnelle (`📥`, `❓`), le nettoyage et la boucle d'affichage (`📤`).
   Le code final est : `💎🍎📥🔄💎🍏🍏❓💎🍏🍎🍏⬅️🗑️🔄💎🍏🍎🍎❓📤💎🍏🍎🍏⬅️🗑️`
3. **Validation** : Nous transmettons ce script via une requête `POST` sur l'endpoint `/api/submit` pour obtenir le flag.

**FLAG** : `HTS{des_pommes_pour_nourrir_mon_automate}`
 