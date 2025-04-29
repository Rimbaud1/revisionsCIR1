# TP5 - SageMath : Espaces Vectoriels, Interpolation Polynomiale et Interpolation d'Hermite

## 1. Espaces vectoriels de polynômes

### ✨ Notions de base

- Un **espace vectoriel** est un ensemble sur lequel on peut faire des **somme de vecteurs** et **multiplication par un scalaire**.
- Ici, l'espace vectoriel considéré est celui des **polynômes de degré ≤ n**.
- Les applications linéaires sur cet espace peuvent être représentées par des **matrices**.

### 📒 Applications linéaires rencontrées

- **Interpolation classique** : Connaitre les valeurs du polynôme en plusieurs points donnés.
- **Interpolation d'Hermite** : Connaitre à la fois les valeurs du polynôme **et de sa dérivée** en certains points.

---

## 2. Construction des matrices d'application

### 📊 Matrice pour interpolation classique

On construit une matrice pour l'application qui à chaque polynôme associe les valeurs : \(P(1), P(2), P(3), P(4), P(5)\).

Chaque ligne correspond à l'évaluation des puissances de \(X\) au point concerné.

```python
A = matrix([
    [1, 1, 1, 1, 1],  # (1)^0, (1)^1, (1)^2, (1)^3, (1)^4
    [1, 2, 4, 8, 16], # (2)^0, (2)^1, (2)^2, (2)^3, (2)^4
    [1, 3, 9, 27, 81],
    [1, 4, 16, 64, 256],
    [1, 5, 25, 125, 625]
])
show(A)
```

**Idée :** chaque ligne = \([1, x, x^2, x^3, x^4]\) pour un certain \(x\).

---

### 📊 Matrice pour interpolation d'Hermite

Quand on impose à la fois des **valeurs** et des **dérivées** :

```python
MP = matrix([
    [1, 0, 0, 0],  # P(0) => constante
    [0, 1, 0, 0],  # P'(0) => coefficient de X
    [1, 1, 1, 1],  # P(1) => somme des puissances de 1
    [0, 1, 2, 3]   # P'(1) => dérivées : X donne 1, X^2 donne 2X, X^3 donne 3X^2
])
show(MP)
```

**Dérivée :** 
- Le terme constant disparaît.
- Le terme en \(X^k\) devient \(kX^{k-1}\).

---

## 3. Résolution par inversion de matrice

### 🔢 Idée principale

Si la matrice est **inversible** (ce qui signifie que son déterminant est non nul), alors l'application linéaire est **bijective**.

On peut alors résoudre facilement :

- Inverser la matrice.
- Multiplier l'inverse par le vecteur des conditions données (valeurs ou valeurs+dérivées).

### 🔄 Calcul de l'inverse et résolution

```python
A_inverse = ~A
coords_y = vector([4, -1, 2, 3, 1])  # valeurs cibles pour interpolation classique
f_inverse_coords_y = A_inverse * coords_y
show(f_inverse_coords_y)
```

```python
MP_inverse = ~MP
coords_y = vector([1, -2, 4, 2])  # valeurs pour Hermite
P_inverse_coords_y = MP_inverse * coords_y
show(P_inverse_coords_y)
```

**Remarque :** 
- `~A` est un raccourci pour `A.inverse()`.
- On applique ensuite un simple produit matrice-vecteur pour obtenir les coefficients du polynôme solution.

---

## 4. Visualisation graphique des résultats

### 🛍️ Tracer un polynôme seul

Tracer le graphe d'un polynôme sur un intervalle donné :

```python
plot_P = plot(36 - (649/12)*x + (217/8)*x^2 - (65/12)*x^3 + (3/8)*x^4, (x, 0.5, 5.5), color='blue', thickness=2)
show(plot_P)
```

- `plot(expression, (variable, debut, fin))` trace une courbe.
- `color` choisit la couleur de la courbe.
- `thickness` ajuste l'épaisseur du trait.

### 🌐 Tracer les points imposés

Pour afficher visuellement les points imposés :

```python
points_P = list_plot([(1,4), (2,-1), (3,2), (4,3), (5,1)], color='red', size=30)
show(points_P)
```

- `list_plot(liste_de_points)` dessine des points à partir d'une liste de coordonnées.
- `size` régle la taille des points.

### 🌟 Superposer polynôme et points

```python
show(plot_P + points_P)
```

- L'opérateur `+` superpose plusieurs graphiques.

### 🔺 Tracer polynôme avec tangentes (Hermite)

Tracer aussi les tangentes aux points imposés :

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

- `linestyle='--'` : pointillé pour symboliser une tangente.
- `gridlines=True` : affiche les lignes de la grille.

---

# 🎉 Recapitulatif Important 🎉

## 📊 Principes à retenir

- Interpolation classique : à partir de \(P(x_i) = y_i\).
- Interpolation d'Hermite : impose aussi les valeurs de \(P'(x_i)\).
- Une application linéaire est représentée par une **matrice**.
- Si la matrice est **inversible**, il y a **un unique polynôme** solution.
- La résolution est obtenue par un produit matrice inverse × vecteur de contraintes.

## 🔢 Commandes SageMath essentielles

| Commande | Fonction |
|:---|:---|
| `matrix([...])` | Créer une matrice |
| `show(A)` | Afficher la matrice ou un graphique |
| `~A` ou `A.inverse()` | Inverser une matrice |
| `A * vecteur` | Multiplier une matrice par un vecteur |
| `plot(expression, (variable, debut, fin), options)` | Tracer un polynôme |
| `list_plot([...], options)` | Tracer des points |
| `point((x,y), size, color)` | Tracer un point isolé |
| `linestyle='--'` | Tracer une ligne pointillée (tangentes) |
| `gridlines=True` | Afficher une grille |

---

**Cours révisé : Espaces vectoriels, Applications linéaires, Interpolation polynomiale, Interpolation d'Hermite.**

**Bonne révision ! 🌟**
