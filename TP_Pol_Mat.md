# SageMath - Polynômes, Matrices et Images Matricielles

## 1. Manipulation des Polynômes

### **Déclaration d'un polynôme**
```python
PolyZ.<X> = ZZ[]  # Polynôme sur ℤ
PolyQ.<X> = QQ[]  # Polynôme sur ℚ
PolyR.<X> = RR[]  # Polynôme sur ℝ
PolyC.<X> = CC[]  # Polynôme sur ℂ
```

### **Opérations sur les Polynômes**
```python
P.degree()  # Degré du polynôme
P.roots()   # Racines du polynôme
P.variables()  # Variables utilisées
P.variable_name()  # Nom de la variable
P.coefficients()  # Liste des coefficients

gcd(P, Q)  # PGCD de P et Q
xgcd(P, Q)  # Algorithme d'Euclide étendu pour P et Q
lcm(P, Q)  # PPCM de P et Q
```

### **Division de Ruffini**
```python
def ruffini(P, alpha):
    """Implémente la division d'un polynôme P par (X - alpha)"""
    coeffs = P.coefficients()  # Récupère les coefficients du polynôme
    Q = []  # Liste pour stocker le quotient
    coeffs.reverse()  # Mettre les coefficients dans l'ordre croissant
    Q.append(coeffs[0])  # Initialisation du premier élément
    
    for i in range(len(coeffs) - 1):  # Boucle pour appliquer la méthode de Ruffini
        Q.append(coeffs[i+1] + Q[i] * alpha)
    
    R = Q[-1]  # Le dernier élément est le reste
    Q.pop()  # On retire le dernier élément qui est le reste
    return Q, R  # Retourne le quotient et le reste
```

**Idée Générale :**
- Applique la **méthode de Ruffini** pour diviser `P(X)` par `(X - α)`.
- Produit un **quotient** `Q(X)` et un **reste** `R`.
- Utilise une boucle pour calculer les nouveaux coefficients successifs.

---

## 2. Manipulation des Matrices

### **Définition et Opérations**
```python
A = matrix([[1,2],[3,4]])  # Matrice 2×2
B = matrix(RR, [[1,2,3],[4,5,6]])  # Matrice sur ℝ
I = identity_matrix(3)  # Matrice identité 3×3

A[0,0]  # Accès à l'élément (1,1)
det(A)  # Déterminant de A

# Différentes méthodes pour obtenir l'inverse d'une matrice
A.inverse()  # Inverse de A
A^-1  # Utilisation de l'exponentiation pour l'inverse
~A  # Autre notation pour l'inverse
```

### **Construction de Matrices Particulières**
#### **Matrice diagonale**
```python
A = diagonal_matrix([1, 2, 3, 4, 5, 6, 7])
show(A)
```
#### **Matrice avec 1 sur la première colonne**
```python
B = matrix(4, 7)
for i in range(4):
    B[i, 0] = 1
show(B)
```
#### **Matrice C personnalisée**
```python
C = matrix([[2, 1, -1, -1, -1],
            [2, 2, -1, -1, -1],
            [2, 3, -1, -1, -1]])
show(C)
```

### **Multiplication de Matrices**
```python
def prod_Mat(A, B):
    """Produit matriciel de A et B avec vérification des dimensions"""
    m, n = A.nrows(), A.ncols()
    n2, p = B.nrows(), B.ncols()
    
    if n != n2:
        print("Erreur : Multiplication impossible")
        return None
    
    C = matrix(m, p)  # Création de la matrice résultat remplie de zéros
    for i in range(m):
        for j in range(p):
            for k in range(n):
                C[i, j] += A[i, k] * B[k, j]  # Produit matriciel classique
    return C
```

**Idée Générale :**
- Vérifie que le **nombre de colonnes de `A` correspond au nombre de lignes de `B`**.
- Effectue une **somme pondérée** des éléments de `A` et `B`.
- Retourne une nouvelle matrice `C` contenant le résultat du produit matriciel.

---

## 3. Images Matricielles avec SageMath

### **Affichage d'une Matrice sous forme d'Image**
```python
n = 10
M = Matrix(RR, n, n)
for i in range(n):
    for j in range(n):
        M[i, j] = (i + j)  # Remplissage de la matrice
matrix_plot(M, colorbar=True)  # Affichage sous forme d'image
```

---

## **À vraiment retenir**
| **Concept** | **Commande SageMath** |
|-------------|----------------|
| Définir un polynôme | `PolyZ.<X> = ZZ[]` |
| Trouver les racines | `P.roots()` |
| PGCD de deux polynômes | `gcd(P, Q)` |
| Définir une matrice | `matrix(n, p, [...])` |
| Créer une matrice identité | `identity_matrix(n)` |
| Calculer le déterminant | `det(A)` ou `A.det()` |
| Trouver l'inverse | `A.inverse()`, `A^-1`, `~A` |
| Afficher une matrice sous forme d'image | `matrix_plot(M)` |

## **En supplément**
| **Concept** | **Commande SageMath** |
|-------------|----------------|
| Plus grand commun diviseur étendu | `xgcd(P, Q)` |
| Plus petit commun multiple | `lcm(P, Q)` |
| Accéder à un élément précis | `A[i, j]` |
| Multiplication de matrices | `prod_Mat(A, B)` |
| Visualisation matricielle avancée | `matrix_plot(M, colorbar=True)` |


