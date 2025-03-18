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
    coeffs = P.coefficients()
    Q = []
    coeffs.reverse()
    Q.append(coeffs[0])
    for i in range(len(coeffs) - 1):
        Q.append(coeffs[i+1] + Q[i] * alpha)
    R = Q[-1]
    Q.pop()
    return Q, R
```

---

## 2. Manipulation des Matrices

### **Définition et Opérations**
```python
A = matrix([[1,2],[3,4]])  # Matrice 2×2
B = matrix(RR, [[1,2,3],[4,5,6]])  # Matrice sur ℝ
I = identity_matrix(3)  # Matrice identité 3×3

A[0,0]  # Accès à l'élément (1,1)
det(A)  # Déterminant de A
A.inverse()  # Inverse de A
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
    
    C = matrix(m, p)
    for i in range(m):
        for j in range(p):
            for k in range(n):
                C[i, j] += A[i, k] * B[k, j]
    return C
```

---

## 3. Images Matricielles avec SageMath

### **Affichage d'une Matrice sous forme d'Image**
```python
n = 10
M = Matrix(RR, n, n)
for i in range(n):
    for j in range(n):
        M[i, j] = (i + j)
matrix_plot(M, colorbar=True)
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
| Trouver l'inverse | `A.inverse()` |
| Afficher une matrice sous forme d'image | `matrix_plot(M)` |

## **En supplément**
| **Concept** | **Commande SageMath** |
|-------------|----------------|
| Plus grand commun diviseur étendu | `xgcd(P, Q)` |
| Plus petit commun multiple | `lcm(P, Q)` |
| Accéder à un élément précis | `A[i, j]` |
| Multiplication de matrices | `prod_Mat(A, B)` |
| Visualisation matricielle avancée | `matrix_plot(M, colorbar=True)` |

---

