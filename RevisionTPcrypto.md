# Rappels sur le TP : SageMath et Cryptographie

## 1. Tables de Multiplication Modulo

### **Représentation graphique des tables modulo**
- **Objectif** : Représenter une table de multiplication modulo `n` sur un cercle.
- **Méthode** :
  1. Placer `n` points sur un cercle.
  2. Relier chaque point `i` au point `(i * a) % n`.

### **Fonctions utilisées :**
- `circle((0, 0), 1, color='black')` → Trace un cercle de rayon 1.
- `point((x, y), size=15, color='blue')` → Dessine un point sur le cercle.
- `line([pts[i], pts[(a * i) % n]], color='blue')` → Relie les points selon la règle de multiplication modulo.

## 2. Chaînes de caractères en Python

### **Manipulations de base :**
- `len(chaine)` → Donne la longueur d'une chaîne.
- `chaine[index]` → Accéder à un caractère spécifique.
- `chaine[a:b]` → Extraire une sous-chaîne.
- `chaine + autre_chaine` → Concaténer deux chaînes.
- `for char in chaine:` → Itérer sur les caractères d'une chaîne.
- `chaine.index(sous_chaine)` → Trouver l'index d'une sous-chaîne.

## 3. Chiffrement ROT13

### **Principe :**
- **ROT13** est un décalage de 13 lettres dans l'alphabet.
- L'encodage et le décodage sont identiques.
- **Exemple :** `TEST` devient `GRFG`.

### **Fonction principale :**
```python
def rot(m, i, alpha):
    return "".join(alpha[(alpha.index(c) + i) % len(alpha)] if c in alpha else c for c in m)
```

## 4. Algorithme RSA

### **Étapes du chiffrement RSA :**
1. **Choix de deux nombres premiers** `p, q`.
2. **Calcul du module** `n = p * q`.
3. **Calcul de φ(n)** : `φ(n) = (p-1) * (q-1)`.
4. **Choix de la clé publique** `e` tel que `1 < e < φ(n)` et `gcd(e, φ(n)) = 1`.
5. **Calcul de la clé privée** `d` tel que `d ≡ e⁻¹ mod φ(n)`.
6. **Chiffrement** : `C ≡ M^e mod n`.
7. **Déchiffrement** : `M ≡ C^d mod n`.

### **Fonctions SageMath utilisées :**
- **`gcd(a, b)`** : Calcule le plus grand commun diviseur entre `a` et `b`.
- **`inverse_mod(e, phin)`** : Trouve `d` tel que `d * e ≡ 1 (mod phin)`.
- **`power_mod(M, e, n)`** : Calcul de `M^e mod n`.
  - **Équivalent Python** : `pow(M, e, n)`.

### **Exemple d'application en SageMath :**
```python
p = 9901
q = 9433
n = p * q
phin = (p-1) * (q-1)
e = 65537
d = inverse_mod(e, phin)
M = 19070
C = power_mod(M, e, n)  # Chiffrement
M_dechiffre = power_mod(C, d, n)  # Déchiffrement
print(M_dechiffre == M)  # Vérification
```

### **Vérification de la signature RSA :**
```python
signature = power_mod(M, d, n)
verification = power_mod(signature, e, n)
print(verification == M)  # Doit être True
```

## **Résumé des principales fonctions :**
| Fonction | Description |
|----------|------------|
| `circle((0, 0), 1, color='black')` | Trace un cercle |
| `point((x, y), size=15, color='blue')` | Place un point sur le cercle |
| `line([pts[i], pts[(a * i) % n]], color='blue')` | Relie les points selon la multiplication modulo |
| `gcd(a, b)` | Calcule le PGCD de `a` et `b` |
| `inverse_mod(e, phin)` | Calcule `d` tel que `d * e ≡ 1 mod phin` |
| `power_mod(M, e, n)` | Calcule `M^e mod n` (équivalent à `pow(M, e, n)`) |
| `rot(m, 13, alpha13)` | Chiffre ou déchiffre un texte en ROT13 |

