# TP : SageMath et Traitement d'Images

## 1. Représentation binaire d'une image (lettre F)

```python
# Création d'une matrice 5x5 représentant la lettre F
M = matrix([[0, 1, 1, 1, 0],
            [0, 1, 0, 0, 0],
            [0, 1, 1, 0, 0],
            [0, 1, 0, 0, 0],
            [0, 1, 0, 0, 0]])
# Affichage de la matrice sous forme d'image
matrix_plot(M, colorbar=True)
```

**Commandes utilisées :**
- `matrix([...])` : crée une matrice.
- `matrix_plot(M)` : affiche la matrice comme une image en niveaux de gris.

---

## 2. Transformation matricielle : inversion verticale

```python
# Matrice de permutation inversant les lignes de haut en bas
A = matrix([[0,0,0,0,1],
            [0,0,0,1,0],
            [0,0,1,0,0],
            [0,1,0,0,0],
            [1,0,0,0,0]])
# Application à l'image pour la retourner verticalement
matrix_plot(A * M)
```

**Commandes utilisées :**
- Multiplication `A * M` : applique une transformation linéaire (ici, miroir vertical).
- `matrix([...])` : permet de définir une matrice de permutation.

---

## 3. Inversion des couleurs (effet négatif)

```python
# Création d'une matrice diagonale avec -1 pour inverser chaque ligne
B = diagonal_matrix([-1, -1, -1 , -1, -1])
F_blanc = B * M 
# Affichage de la nouvelle matrice avec inversion
matrix_plot(F_blanc).show()
```

**Commandes utilisées :**
- `diagonal_matrix([...])` : crée une matrice diagonale.
- Multiplication `B * M` : change les signes des lignes → effet d'inversion visuelle.

---

## 4. Chargement d'image réelle

```python
from matplotlib.pyplot import imread, imshow
# Chargement d'une image RGB
vice = imread("viceversa2.png")
# Affichage de l'image chargée
imshow(vice)
```

**Commandes utilisées :**
- `imread(...)` : lit une image en tant que tableau de valeurs RGB.
- `imshow(...)` : affiche l'image.

---

## 5. Informations sur l'image

```python
# Dimensions de l'image (hauteur, largeur, couches RGB)
vice.shape
# Valeurs RGB du pixel en position (100, 120)
print(vice[100,120])
```

**Commandes utilisées :**
- `.shape` : renvoie la taille de l’image (tuple).
- `image[i, j]` : donne les 3 valeurs RGB du pixel ciblé.

---

## 6. Transposition de l’image en niveaux de gris

```python
# On suppose que 'rouge' contient la couche rouge de l'image
vice_gris = rouge
# Transposition de la matrice pour inverser lignes et colonnes
vice_trans = vice_gris.transpose()
# Affichage de l'image transposée en niveaux de gris
figure(figsize=(5,5))
imshow(vice_trans,cmap='gray')
```

**Commandes utilisées :**
- `.transpose()` : retourne la matrice en miroir diagonal.
- `imshow(..., cmap='gray')` : affiche la couche en niveaux de gris.

---

## 7. Masquage de zones (yeux censurés)

```python
vice = imread("viceversa2.png")
# Masquage de 2 zones rectangulaires (yeux)
rouge[80:150, 300:400] = 0
rouge[300:400, 300:500] = 0
imshow(rouge,cmap='gray')
```

**Commandes utilisées :**
- Affectation d'une sous-matrice à 0 : supprime visuellement une zone.
- `imshow(..., cmap='gray')` : rend les pixels à 0 en noir.

---

## 8. Création d’un cadre noir autour de l’image

```python
vice = imread("viceversa2.png")
rouge = vice[:,:,0] # extraction de la couche rouge
# Ajout d’un cadre noir en modifiant les bords
rouge[0:20, 0:800] = 0
rouge[640:800, 0:800] = 0
rouge[0:700, 0:20] = 0
rouge[0:700, 780:800] = 0
imshow(rouge, cmap='gray')
```

**Commandes utilisées :**
- `image[:,:,0]` : sélectionne la couche rouge.
- Affectation de lignes/colonnes à 0 pour créer un cadre.

---

## 9. Zoom dans l’image (zone précise)

```python
vice = imread("viceversa2.png")
# Sélection d’un sous-rectangle (zoom)
zoom = vice[100:200,600:700,0] # couche rouge
imshow(zoom, cmap='gray')
```

**Commandes utilisées :**
- Slicing `image[a:b, c:d, 0]` : extraction d'une zone + couleur.
- `imshow(..., cmap='gray')` : visualise cette portion zoomée.

---

## 10. Application d’un masque circulaire

```python
vice = imread("viceversa2.png")
cercle = vice[:,:,0] # matrice de la composante rouge
# Suppression des pixels à l'extérieur d’un cercle centré en (331,400)
for i in range(663):
    for j in range(800):
        if (331 - i)**2 + (400 - j)**2 > 350**2:
            cercle[i, j] = 0
imshow(cercle, cmap='gray')
```

**Commandes utilisées :**
- Boucles imbriquées : balayage de tous les pixels.
- Condition sur un cercle : masque radial (équation d’un disque).

---

## Résumé des commandes utiles

| Commande                     | Effet                                                  |
| ----------------------------| ------------------------------------------------------ |
| `matrix([...])`             | Crée une matrice en SageMath                           |
| `matrix_plot(M)`            | Affiche une image à partir d'une matrice binaire       |
| `A * M`                     | Applique une transformation linéaire à l'image         |
| `diagonal_matrix([...])`    | Crée une matrice diagonale                            |
| `imread("fichier.png")`     | Charge une image (RGB)                                 |
| `imshow(image, cmap='gray')`| Affiche une image en niveaux de gris                   |
| `image.shape`               | Donne les dimensions (hauteur, largeur, canaux)        |
| `image[i, j]`               | Donne les valeurs RGB du pixel (i,j)                   |
| `image[:,:,0]`              | Accède à la couche rouge                               |
| `image.transpose()`         | Transpose une matrice image                            |
| Affectation de tranches     | Permet de modifier des zones spécifiques               |

---

🎯 Envoie ça à ChatGPT et demande lui : 
Pose moi 10 questions courtes sur ce cours et laisse moi répondre, tu me corrigeras ensuite et me donneras d'autres questions adaptés en fonction de mes difficultées.

