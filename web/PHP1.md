# Révision PHP

## Introduction à PHP
- **PHP (Hypertext Preprocessor)** : langage de script côté serveur pour créer des sites web dynamiques.
- Créé en 1994 par **Rasmus Lerdorf**.
- Exécuté sur un serveur, renvoie du HTML au client.
- Fichiers PHP : **extension `.php`**.

```php
<?php
  echo "Bonjour, monde !";
?>
```

---

## Variables et Constantes

### **Variables**
- Déclarées avec un `$`.
- Typage dynamique : pas besoin de préciser le type.

```php
$nom = "Alice";
$age = 25;
$prix = 19.99;
$estVrai = true;
```

### **Constantes**
- Définies avec `define()` ou `const`.

```php
define("PI", 3.1415);
const TVA = 20;
```

---

## Structures de Contrôle

### **Conditions**
```php
if ($age >= 18) {
    echo "Majeur";
} else {
    echo "Mineur";
}
```

### **Switch**
```php
$jour = "lundi";
switch ($jour) {
    case "lundi":
        echo "Début de semaine";
        break;
    case "vendredi":
        echo "Bientôt le week-end";
        break;
    default:
        echo "Jour normal";
}
```

### **Boucles**
```php
for ($i = 0; $i < 5; $i++) {
    echo $i;
}

while ($i < 5) {
    echo $i;
    $i++;
}

foreach (["Alice", "Bob"] as $nom) {
    echo $nom;
}
```

---

## Fonctions

```php
function saluer($nom) {
    return "Bonjour " . $nom;
}

echo saluer("Alice");
```

**Valeur par défaut** :
```php
function direBonjour($nom = "Utilisateur") {
    return "Bonjour " . $nom;
}
```

---

## Tableaux

### **Tableaux indexés**
```php
$tab = ["Alice", "Bob", "Charlie"];
echo $tab[0]; // Alice
```

### **Tableaux associatifs**
```php
$info = ["nom" => "Alice", "age" => 25];
echo $info["nom"]; // Alice
```

### **Fonctions utiles**
```php
count($tab); // Nombre d'éléments
array_push($tab, "David"); // Ajoute à la fin
array_pop($tab); // Supprime le dernier élément
array_shift($tab); // Supprime le premier élément
in_array("Alice", $tab); // Vérifie la présence
```

---

## Manipulation des Chaînes

```php
strtolower("TEXTE"); // "texte"
strtoupper("texte"); // "TEXTE"
strlen("PHP"); // 3
strpos("Hello World", "World"); // 6
str_replace("le", "un", "le monde"); // "un monde"
```

---

## Fonctions sur les Dates

```php
echo date("Y-m-d"); // Affiche la date du jour
echo time(); // Timestamp actuel
echo strtotime("+1 week"); // Timestamp dans une semaine
```

---

## Inclusion de Fichiers

```php
include "header.php"; // Continue même si le fichier est absent
require "config.php"; // Erreur fatale si absent
```

---

## Fichiers en PHP

### **Lire un fichier**
```php
$contenu = file_get_contents("test.txt");
echo $contenu;
```

### **Écrire dans un fichier**
```php
file_put_contents("test.txt", "Hello");
```

### **Supprimer un fichier**
```php
unlink("test.txt");
```

---

## Sécurité et Formulaires

### **Récupérer une variable `POST` de manière sécurisée**
```php
$nom = filter_input(INPUT_POST, "nom", FILTER_SANITIZE_STRING);
```

### **Éviter les failles XSS**
```php
echo htmlspecialchars("<b>Hello</b>"); // Affiche: &lt;b&gt;Hello&lt;/b&gt;
```

### **Hacher un mot de passe**
```php
$hash = password_hash("monMotDePasse", PASSWORD_DEFAULT);
```

### **Vérifier un mot de passe**
```php
if (password_verify("monMotDePasse", $hash)) {
    echo "Mot de passe valide";
}
```

---

## Expressions Régulières

```php
preg_match('/^Q[0-9]{3}$/', "Q123"); // Vérifie un format
```

---

## JSON et PHP

### **Convertir un tableau en JSON**
```php
$json = json_encode(["nom" => "Alice", "age" => 25]);
echo $json; // {"nom":"Alice","age":25}
```

### **Convertir du JSON en tableau PHP**
```php
$data = json_decode($json, true);
echo $data["nom"]; // Alice
```

---

## Générer un Nombre Aléatoire

```php
echo rand(1, 100);
```

---

## Résumé des Comparaisons

| Opérateur | Signification |
|-----------|--------------|
| `==` | Comparaison de valeurs (laxiste) |
| `===` | Comparaison stricte (valeur + type) |
| `!=` | Différent (valeur) |
| `!==` | Différent (valeur + type) |

```php
var_dump(5 == "5");  // true
var_dump(5 === "5"); // false
```

---

## Pour réviser efficacement:
Envoie à ChatGPT : 
- Ce fichier
- Le QCM de l'année dernière


Et demande lui de te générer des qcms similaires pour que t'y réponde
Fait ça jusqu'à obtenir toujours des bons scores
