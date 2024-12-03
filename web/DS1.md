
# Récapitulatif des Notions Clés pour Préparer le DS de Web Statique

## **1. Positionnement en CSS**

### Les différents types de positionnement :
- **static** (par défaut) : positionnement naturel des éléments sans modification.
- **relative** : déplace l'élément par rapport à sa position normale.
- **absolute** : positionne l'élément par rapport à son ancêtre positionné le plus proche.
- **fixed** : l'élément reste fixe par rapport à la fenêtre, même en cas de défilement.
- **sticky** : l'élément alterne entre `relative` et `fixed` selon le défilement.

### Propriétés importantes :
- `top`, `right`, `bottom`, `left` : pour définir la position exacte d’un élément.
- `z-index` : contrôle la superposition des éléments (plus la valeur est élevée, plus l'élément est devant).

---

## **2. CSS Grid Layout**

### Concepts de base :
- Utilisé pour organiser des éléments en grilles bidimensionnelles (lignes et colonnes).

### Propriétés principales :
- `display: grid;` : transforme un conteneur en grille.
- `grid-template-columns` et `grid-template-rows` : définissent la structure des colonnes et lignes.
  - Exemple : `grid-template-columns: 100px 1fr;` (1 colonne fixe, 1 colonne fluide).

### Positionnement des éléments :
- `grid-area` : place un élément dans une zone définie.
- `grid-template-areas` : organise les zones nommées.
  - Exemple :
    ```css
    grid-template-areas:
      "header header"
      "menu content"
      "footer footer";
    ```

### Unités utiles :
- **fr** : unité fractionnaire pour répartir l’espace disponible.
- **auto** : ajuste la taille automatiquement selon le contenu.

---

## **3. Flexbox**

### Concepts de base :
- Flexbox organise les éléments dans une seule dimension (ligne ou colonne).

### Propriétés importantes :
- `display: flex;` : active le mode flexbox.
- `flex-direction` : contrôle l'orientation (`row`, `column`, etc.).
- `justify-content` : contrôle l’alignement horizontal.
  - Valeurs : `flex-start`, `center`, `space-between`, `space-around`.
- `align-items` : contrôle l’alignement vertical.
  - Valeurs : `flex-start`, `center`, `stretch`.
- `flex-wrap` : permet le retour à la ligne des éléments si nécessaire.

### Exemple : Centrer un élément
```css
.conteneur {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

---

## **4. Animations CSS**

### Étapes clés pour créer une animation :
1. Définir les étapes avec `@keyframes`.
   - Exemple :
     ```css
     @keyframes exemple {
       0% { background-color: red; }
       100% { background-color: blue; }
     }
     ```
2. Appliquer l'animation à un élément :
   - `animation-name` : nom de l’animation.
   - `animation-duration` : durée totale (exemple : `10s`).
   - `animation-fill-mode` : contrôle l'état final (exemple : `forwards` pour conserver).

---

## **5. Sélecteurs CSS Avancés**

### Quelques sélecteurs utiles :
- **Généraux :**
  - `h1, p` : cible les balises `h1` et `p`.
  - `h1 ~ p` : cible tous les `p` suivant un `h1` (même parent).
  - `h1 + p` : cible uniquement le `p` directement après un `h1`.

- **Pseudo-classes :**
  - `:hover` : applique un style quand on survole un élément.
  - `:active` : applique un style pendant le clic.
  - `:nth-child(n)` : cible le `n`-ème enfant.

---

## **6. Media Queries**

### Permettent de créer des designs responsifs :
- Exemple : appliquer un style pour des écrans > 600px :
  ```css
  @media only screen and (min-width: 600px) {
    body {
      background-color: lightblue;
    }
  }
  ```

- Orientation spécifique :
  ```css
  @media (orientation: landscape) {
    body {
      font-size: 18px;
    }
  }
  ```

---

## **7. Divers**

### Unités CSS :
- `px` : pixels fixes.
- `%` : pourcentage relatif au parent.
- `vh`, `vw` : pourcentage de la hauteur/largeur de la fenêtre.

### Propriété `clear` :
- Utilisée pour empêcher les chevauchements avec des éléments flottants :
  ```css
  h2 {
    clear: right;
  }
  ```

### Propriété `gap` :
- Ajoute des espaces entre les éléments dans une grille ou un flex container.

---

## **8. Exemples Typiques**

### CSS Grid Exemple Complet :
```css
.conteneur {
  display: grid;
  grid-template-areas:
    "header header"
    "menu content"
    "footer footer";
  grid-template-columns: 1fr 2fr;
  gap: 10px;
}

.header { grid-area: header; }
.menu { grid-area: menu; }
.content { grid-area: content; }
.footer { grid-area: footer; }
```

### Flexbox Exemple Complet :
```css
.conteneur {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
```

---

