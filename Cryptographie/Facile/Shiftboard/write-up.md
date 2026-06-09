# Shiftboard - Write-up

Nous analysons le message chiffré fourni.

1. **Identification du chiffrement** : Nous constatons que le chiffrement correspond à un décalage de touches sur le clavier.
2. **Décryptage** : En décalant chaque caractère d'une touche vers la gauche sur un clavier de disposition AZERTY (le texte original ayant été décalé vers la droite), nous reconstituons le message en clair et le flag.

**FLAG** : `HTS{4C0d3c1Vi3r}` 