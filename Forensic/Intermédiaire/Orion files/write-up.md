# Orion files - Write-up

Nous avons analysé le document PDF `rapport_incident_secreur9.pdf`.

1. **Recherche de chaînes de caractères** : Une recherche textuelle rapide du motif `HTS{` dans le document révèle une première partie du flag.
2. **Extraction d'archive masquée** : En effectuant une analyse avec `binwalk`, nous découvrons qu'une archive ZIP est dissimulée à la fin du fichier PDF (fichier polyglotte).
3. **Attaque par force brute** : L'archive ZIP étant protégée par un mot de passe, nous extrayons le condensat de chiffrement avec `zip2john` et cassons le mot de passe (`superman123`) à l'aide de `john` et d'une liste de mots. L'extraction de l'archive révèle le flag complet.

**FLAG** : `HTS{P0lygl0t_F1l3s_4nd_B4d_R3d4ct10ns_L34d_T0_Th3_Truth}` 