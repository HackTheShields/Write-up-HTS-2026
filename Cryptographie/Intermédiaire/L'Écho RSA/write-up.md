# L'Écho RSA

On nous fournit 4 fichiers : deux clés publiques (`agent1_pub.pem`, `agent2_pub.pem`) et deux messages chiffrés (`msg1.enc`, `msg2.enc`).

En examinant les clés publiques (par exemple avec `openssl rsa -pubin -in agent1_pub.pem -text`), on remarque quelque chose de très spécifique : les deux clés utilisent le **même Modulus (N)**, mais des exposants publics différents (ex: `e1 = 17` et `e2 = 65537`).

C'est une configuration vulnérable classique appelée **attaque sur le Module Commun (Common Modulus Attack)**.
Si le même message en clair `M` est chiffré deux fois pour deux destinataires différents partageant le même module `N` (et que les exposants `e1` et `e2` sont premiers entre eux, ce qui est le cas ici), on peut retrouver le message en clair sans avoir besoin de factoriser `N` ou de connaître les clés privées !

**L'astuce mathématique :**
Puisque `e1` et `e2` sont premiers entre eux, d'après l'identité de Bézout, il existe deux entiers `a` et `b` tels que `a*e1 + b*e2 = 1`.
On possède les textes chiffrés : `C1 = M^e1 mod N` et `C2 = M^e2 mod N`.
En utilisant nos coefficients de Bézout, il suffit de calculer : `(C1^a * C2^b) mod N`.
Mathématiquement, cela équivaut à `M^(a*e1 + b*e2) mod N`, ce qui donne exactement `M^1 mod N` = `M` (le message en clair).

Un petit script Python combinant l'algorithme d'Euclide étendu et des exponentiations modulaires permet d'appliquer la formule. Le message déchiffré révèlera directement le flag.

**Flag:** `HTS{S4M3_M0DULUS_TW1C3_TH3_FUN}`
