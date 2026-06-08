# L'Anti-Akinator - Write-up

Nous avons analysé l'image `akinator_corrompu.png`.

1. **Premières analyses** : L'utilisation de commandes classiques comme `strings` ou d'outils comme `zsteg` révèle des faux flags ou des leurres.
2. **Stéganographie par caractères invisibles** : Nous découvrons la présence de caractères de largeur nulle (*Zero-Width Characters*) dissimulés dans les chaînes de caractères de l'image.
3. **Extraction et décodage** : Nous utilisons un script Python (ou une bibliothèque telle que `zwsp-steg-py`) afin d'extraire ces caractères invisibles (`\u200B` et `\u200C`), de les convertir en binaire, puis en texte clair pour révéler le flag réel.

```python
import re

def decode_zwc(text):
    zw_0 = '\u200B'
    zw_1 = '\u200C'
    
    # Extract only ZWCs
    code = [c for c in text if c in (zw_0, zw_1)]
    if not code:
        return None
        
    binary = "".join(['1' if c == zw_1 else '0' for c in code])
    
    chars = []
    for i in range(0, len(binary), 8):
        byte = binary[i:i+8]
        if len(byte) == 8:
            chars.append(chr(int(byte, 2)))
    return "".join(chars)

if __name__ == "__main__":
    with open("akinator_corrompu.png", "rb") as f:
        data = f.read()
        
    try:
        text = data.decode('utf-8', errors='ignore')
    except Exception:
        text = str(data)
        
    print("[*] Analyzing strings for Zero-Width Characters...")
    flag = decode_zwc(text)
    
    if flag and "HTS{" in flag:
        print("\n[+] Extracted Real Flag via Zero-Width Steganography:")
        print(flag)
    else:
        print("\n[-] ZWC flag not found.")
```

**FLAG** : `HTS{je_l_avais_pas_vu_venir}`