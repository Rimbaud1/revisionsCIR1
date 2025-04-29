# SageMath - Espaces Vectoriels, Interpolation Polynomiale et Hermite

## 1. Espaces vectoriels de polynômes

### **Définition**
- \( V \) : espace vectoriel des polynômes de degré \( \leq n \).
- Une **application linéaire** sur \( V \) peut être représentée par une **matrice**.

### **Exemples :**
- Application \( f(P) = (P(1), P(2), P(3), P(4), P(5)) \) représentée par une matrice 5x5.
- Application \( P \mapsto (P(0), P'(0), P(1), P'(1)) \) pour l'interpolation d'Hermite.

---

## 2. Construction de matrices d'application

### **Interpolation classique :**

Pour \( f(P) = (P(1), P(2), P(3), P(4), P(5)) \), la matrice associée est :

```python
A = matrix([
    [1, 1, 1, 1, 1],
    [1, 2, 4, 8, 16],
    [1, 3, 9, 27, 81],
    [1, 4, 16, 64, 256],
    [1, 5, 25, 125, 625]
])
show(A)
```

Chaque ligne correspond aux puissances successives de \( X \) évaluées en 1,2,3,4,5.

---

### **Interpolation d'Hermite :**

Pour \( f(P) = (P(0), P'(0), P(1), P'(1)) \), la matrice est :

```python
MP = matrix([
    [1, 0, 0, 0],  # P(0)
    [0, 1, 0, 0],  # P'(0)
    [1, 1, 1, 1],  # P(1)
    [0, 1, 2, 3]   # P'(1)
])
show(MP)
```

Utilisation des dérivées : \( P'(X) \) est obtenue en multipliant les coefficients par leur degré.

---

## 3. Résolution par inversion de matrice

### **Principe :**
- Si la matrice est **inversible**, il existe **un unique polynôme** solution.
- Résolution : \( \text{coefficients de } P = A^{-1} \times \text{vecteur des valeurs imposées} \).

### **Exemples :**

```python
A_inverse = ~A
coords_y = vector([4, -1, 2, 3, 1])
f_inverse_coords_y = A_inverse * coords_y
show(f_inverse_coords_y)
```

Pour l'Hermite :

```python
MP_inverse = ~MP
coords_y = vector([1, -2, 4, 2])
P_inverse_coords_y = MP_inverse * coords_y
show(P_inverse_coords_y)
```

---

## 4. Visualisation graphique

### **Tracer un polynôme :**

```python
plot_P = plot(36 - (649/12)*x + (217/8)*x^2 - (65/12)*x^3 + (3/8)*x^4, (x, 0.5, 5.5), color='blue', thickness=2)
points_P = list_plot([(1,4), (2,-1), (3,2), (4,3), (5,1)], color='red', size=30)
show(plot_P + points_P)
```

### **Tracer un polynôme et ses tangentes :**

```python
P(x) = -6*x^3 + 11*x^2 - 2*x + 1
T0(x) = 1 - 2*x
T1(x) = 2*x + 2

courbe = plot(P, (x, -0.5, 1.5), color='blue')
pts = point((0,1), size=30, color='red') + point((1,4), size=30, color='red')
tg0 = plot(T0, (x, -0.5, 1.5), color='green', linestyle='--')
tg1 = plot(T1, (x, -0.5, 1.5), color='orange', linestyle='--')

show(courbe + pts + tg0 + tg1, gridlines=True)
```

---

## 🎉 Résumé des commandes utiles

| Concept | Commande |
|:---|:---|
| Créer une matrice | `matrix([...])` |
| Afficher une matrice | `show(A)` |
| Inverser une matrice | `~A` |
| Multiplier matrice × vecteur | `A * v` |
| Tracer un polynôme | `plot(P(x), (x, a, b))` |
| Tracer des points | `list_plot([...])` |
| Tracer des tangentes | `plot(T(x), (x, a, b), linestyle='--')` |

---

**Cours révisé : Espaces vectoriels, applications linéaires, interpolation polynomiale, interpolation d'Hermite.**

**Bonne révision ! 🌟**
