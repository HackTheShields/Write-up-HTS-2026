# Enigma - Write-up

Nous avons analysé le fichier de modélisation 3D `enigma_source.stl`.

1. **Visualisation 3D** : Nous ouvrons le fichier STL à l'aide d'un logiciel de modélisation 3D comme Blender.
2. **Alignement du mécanisme** : Nous constatons la présence d'une roue rotative comportant plusieurs caractères. Nous faisons pivoter la roue de manière à aligner la phrase clé `ORION_MASTER_OVERRIDE_CODE_123` sur une seule et même ligne.
3. **Révélation du flag** : Une fois la clé d'activation correctement alignée, le flag se dévoile en clair en arrière-plan du modèle.

**FLAG** : `HTS{M3CH4N1C4L_CRYPT0_1S_S4F3}`