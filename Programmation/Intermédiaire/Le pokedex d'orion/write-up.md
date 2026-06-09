# Le Pokédex d'Orion - Write-up

Nous devons maximiser la force de combat (CP) cumulée de notre équipe de Pokémon sans dépasser la limite de poids autorisée de 50 kg.

1. **Analyse du problème** : Nous identifions qu'il s'agit du problème algorithmique classique du **Sac à dos 0/1 (Knapsack)**.
2. **Automatisation** : Nous écrivons un script Python qui initie une session de jeu via `/api/start` pour récupérer le jeton et la liste des 300 Pokémon générés (chacun avec son poids et ses CP).
3. **Résolution & Soumission** : Nous implémentons un algorithme de programmation dynamique pour calculer la valeur CP optimale en temps linéaire, puis soumettons le résultat à `/api/solve/<TOKEN>`. Le flag s'affiche alors sur l'interface web.

**FLAG** : `HTS{la_team_rocket_s_envole_vers_d_autres_cieux}`
 