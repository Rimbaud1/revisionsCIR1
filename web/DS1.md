
# Récapitulatif Complet pour le DS de Web Statique

## **1. Les bases du HTML**

### Structure minimale d'une page HTML
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ma Page</title>
</head>
<body>
  <header>
    <h1>Bienvenue</h1>
  </header>
  <main>
    <p>Ceci est un exemple de contenu.</p>
  </main>
  <footer>
    <p>© 2024 Mon Site</p>
  </footer>
</body>
</html>
```

### Balises importantes :
- **Structuration** : `<header>`, `<main>`, `<footer>`, `<section>`, `<article>`.
- **Texte** : `<p>`, `<h1>` à `<h6>`, `<span>`, `<strong>`, `<em>`.
- **Liens et médias** : `<a>`, `<img>`, `<video>`, `<audio>`.
- **Listes** : `<ul>` (non ordonnée), `<ol>` (ordonnée), `<li>` (élément de liste).
- **Formulaires** : `<form>`, `<input>`, `<textarea>`, `<button>`, `<label>`.

---

## **2. Les bases du CSS**

### Inclure du CSS
- **Interne** : directement dans un fichier HTML.
```html
<style>
  body {
    background-color: lightblue;
  }
</style>
```
- **Externe** : via un fichier `.css`.
```html
<link rel="stylesheet" href="styles.css">
```
- **En ligne** : dans une balise HTML (à éviter).
```html
<p style="color: red;">Texte rouge</p>
```

### Sélecteurs CSS
- **De base** :
  - `h1` : tous les éléments `<h1>`.
  - `.class` : éléments avec une classe spécifique.
  - `#id` : élément avec un identifiant spécifique.
- **Combinés** :
  - `div p` : tous les `<p>` dans un `<div>`.
  - `h1 + p` : le `<p>` immédiatement après un `<h1>`.
  - `h1 ~ p` : tous les `<p>` après un `<h1>` (même parent).

---

## **3. Positionnement en CSS**

### Types de positionnement
- **static** : position naturelle.
- **relative** : déplacement relatif à la position normale.
- **absolute** : par rapport à l’ancêtre positionné.
- **fixed** : reste fixe, même lors du défilement.
- **sticky** : bascule entre `relative` et `fixed`.

### Exemples
1. **Position absolue** :
```css
.boite {
  position: absolute;
  top: 50px;
  left: 100px;
}
```
2. **Position fixe** :
```css
.entete {
  position: fixed;
  top: 0;
  width: 100%;
}
```

---

## **4. CSS Grid**

### Grilles en 2D
- Déclaration de base :
```css
.conteneur {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  grid-template-rows: auto 1fr auto;
  gap: 10px; /* Espacement */
}
```
- Nommer les zones :
```css
grid-template-areas:
  "header header header"
  "menu content aside"
  "footer footer footer";
```

### Positionner les éléments
```css
.header {
  grid-area: header;
}
```

---

## **5. Flexbox**

### Organisation en 1D
- Déclaration de base :
```css
.conteneur {
  display: flex;
  flex-direction: row; /* Orientation horizontale */
  justify-content: space-between; /* Espacement horizontal */
  align-items: center; /* Alignement vertical */
}
```

### Exemples avancés
1. **Flex-wrap** :
```css
.conteneur {
  flex-wrap: wrap;
}
```
2. **Alignement individuel** :
```css
.element {
  align-self: flex-end;
}
```

---

## **6. Animations CSS**

### Étapes d’une animation
1. Déclarer les étapes :
```css
@keyframes changerCouleur {
  0% { background-color: red; }
  50% { background-color: green; }
  100% { background-color: blue; }
}
```
2. Lier à un élément :
```css
.boite {
  animation: changerCouleur 10s linear forwards;
}
```

---

## **7. Media Queries**

### Exemple
```css
@media only screen and (min-width: 600px) {
  body {
    background-color: lightgreen;
  }
}
```

---

## **8. Bonnes pratiques**

### Structure du code
- Toujours valider le HTML/CSS avec des validateurs en ligne.
- Utiliser des classes au lieu d’identifiants (`#id`) pour styliser plusieurs éléments.

### Responsivité
- Utiliser des unités relatives comme `%`, `em`, `rem`, `vh`, et `vw`.
- Privilégier des mises en page fluides avec `flexbox` ou `grid`.

---

## **9. Exemples de mise en page complète**

### Exemple avec CSS Grid
```html
<div class="conteneur">
  <div class="entete">Entête</div>
  <div class="menu">Menu</div>
  <div class="contenu">Contenu</div>
  <div class="aside">Aside</div>
  <div class="pied">Pied</div>
</div>

<style>
.conteneur {
  display: grid;
  grid-template-areas:
    "entete entete entete"
    "menu contenu aside"
    "pied pied pied";
  gap: 10px;
}
.entete { grid-area: entete; }
.menu { grid-area: menu; }
.contenu { grid-area: contenu; }
.aside { grid-area: aside; }
.pied { grid-area: pied; }
</style>
```

### Exemple avec Flexbox
```html
<div class="conteneur">
  <div class="element">Élément 1</div>
  <div class="element">Élément 2</div>
  <div class="element">Élément 3</div>
</div>

<style>
.conteneur {
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.element {
  flex: 1;
  margin: 10px;
  text-align: center;
}
</style>
```

---

Avec ces notions et exemples, tu es paré pour réussir ton DS ! 💪✨