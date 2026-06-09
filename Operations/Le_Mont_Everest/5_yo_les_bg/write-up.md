# Yo les BG - Write-up

Nous arrivons sur une interface web proposant un formulaire de test de connectivité (ping).

1. **Injection de commande** : Le formulaire n'étant pas correctement sécurisé, nous pouvons injecter des commandes système via des caractères de liaison comme `|` ou `;` (par exemple : `127.0.0.1 | ls`).
2. **Lecture du flag** : Nous listons le répertoire courant, identifions la présence d'un fichier nommé `flag5.txt`, puis lisons son contenu à l'aide de la commande `cat`.

**FLAG** : `HTS{mais_nan_yuki}` 