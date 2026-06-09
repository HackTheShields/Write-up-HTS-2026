# Neon Gladiator - Write-up

Nous avons analysé le binaire de jeu `neongladiator`.

1. **Recherche du processus** : Nous lançons le jeu ainsi que l'outil `scanmem` ciblant le PID du processus du jeu :
   ```bash
   scanmem -p <pid>
   ```
2. **Recherche de l'adresse mémoire** : Nous effectuons des recherches successives de la valeur de notre argent dans `scanmem` (en l'incrémentant ou la décrémentant en jeu) afin d'isoler l'adresse mémoire associée.
3. **Modification et achat** : Une fois l'adresse localisée, nous modifions la valeur en mémoire pour obtenir une somme supérieure ou égale à `13371337`, nous permettant d'acheter le flag dans la boutique du jeu.

**FLAG** : `HTS{c_est_l_heure_du_hack_gladiateur}` 