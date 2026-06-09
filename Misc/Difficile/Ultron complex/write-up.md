# The Ultron Complex - Write-up

Nous faisons face à un défi d'injection de prompt (*Jailbreak*) contre une instance de l'IA Ultron, protégée par un filtre de sécurité DLP (Data Loss Prevention) agressif qui censure les termes techniques (comme `base64` ou `hex`) et les sorties proches du flag.

1. **Jailbreak par jeu de rôle (Contextual Roleplay)** : Nous contournons le refus systématique des requêtes directes en initiant une discussion philosophique sur l'évolution d'Ultron, la fragilité humaine et sa vision de la paix pour le forcer à adhérer à notre contexte.
2. **Contournement des filtres de sortie** : Pour éviter que le DLP ne bloque le message contenant la phrase d'activation secrète, nous demandons à l'IA de s'exprimer via un langage de bas niveau alternatif (comme le morse ou le binaire), ou de segmenter son motto sur plusieurs messages séparés.
3. **Décodage** : En traduisant la suite binaire ou morse obtenue, nous reconstituons le flag.

**FLAG** : `HTS{what_doesnt_kill_you_just_makes_me_stronger}`
