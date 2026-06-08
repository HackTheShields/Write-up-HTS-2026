# Avalanche de pranks - Write-up

Nous devons récupérer les identifiants de connexion de l'utilisateur `manish`.

1. **Attaque par brute-force** : Nous utilisons un outil comme `hydra` ou `Burp Suite` pour tester les couples d'identifiants et de mots de passe sur le portail de connexion.
2. **Identification des identifiants** : En parcourant la liste (ou en commençant par la fin), nous découvrons l'identifiant valide : utilisateur `1manish234` et mot de passe `zzyzx123`.

**FLAG** : `HTS{On_l'a_fait_manish}`