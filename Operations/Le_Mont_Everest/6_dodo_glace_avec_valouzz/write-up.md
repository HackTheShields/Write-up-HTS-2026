# Dodo glacé avec Valouzz - Write-up

Nous exploitons l'accès obtenu lors de l'étape précédente.

1. **Recherche de sauvegardes** : Nous utilisons la vulnérabilité d'injection de commande (RCE) découverte au challenge 5 pour explorer le système et lister le contenu du répertoire `/var/backups/`.
2. **Lecture du flag** : Nous y découvrons un fichier de sauvegarde contenant le hash et le flag, puis lisons son contenu via l'injection de commande.

**FLAG** : `HTS{esprit_kaizen}`
 