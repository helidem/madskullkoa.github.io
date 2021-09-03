# 1. Rappels Javascript

## 1.1 Variables et types de valeurs

### 1.1.1 Déclaration d'une variable

Définition d'une variable : 
```javascript
var a; //"undefined"
let b; //"undefined"
const c; //undefined"

//initialisation
var e = 1;
let f = "bonjour";
const g = 1 + 0.45;

//on peut aussi faire sans erreur :
let a = 2;
a = "bonjour"
```

### 1.1.2 Types de valeurs

- **string** : une chaine de caractères
```javascript
let a = "bonjour";
```
- **number** : un nombre entier, décimal, ou la valeur `Nan`
- **boolean** : 
```javascript
let a = true;
let b = false;
```

- **object** : Exemples : `Date, Math, String, Number, Boolean, JSON, window, document,` etc.

```javascript
let a = {a: 4, b: "bonjour"}; //expression littérale
let b = new Date(); //instanciation d'un objet à partir de l'objet de type natif Date()
let c = null;
``` 
- **function** : 
```javascript
let a = function () { return 5 };
let b = a(); // appelle la fonction a et retourne 5
```

## 1.2 Structures de controle

### 1.2.1 Conditionnelles

__Les opérateurs ternaires `?` et `:`__

Ce sont des raccourcis des blocs `if ... else`.
```javascript
let maVar = condition ? ExpressionSiVrai : ExpressionSiFaux;

//exemple : 
let i = 1;
let chaine;
if (i === 1) {
	chaine = "oui";
} else {
	chaine = "non";
}

//equivaut à :
let i = 1;
let chaine = 1 == 1 ? "oui" : "non";
```
__`Switch...case...break`__

Comme en C.
```javascript
switch (var) {
	case "...":
		instruction_1;
		break;
	...
	default:
		instruction_par_defaut;
		break;
```

### 1.2.2 Boucles

__`for`, `do...while`, `while`__
Comme en C. 
- Le `break` permet de sortir de la boucle
- Le `continue` permet de passer à la prochaine itération sans lire le reste du bloc

## 1.3 Fonctions

### 1.3.1 Closures 
Exemple :
```javascript
function additionner(nb1) {
	let ajouter = function(nb2) {
		return nb1 + nb2;
	};
	return ajouter;
}
let add2 = additionner(2);
let add3 = additionner(3);

let somme1 = add2(4); //6
let somme2 = add3(3); //6
```

### 1.3.2 Fonction en argument d'autres fonctions

```javascript
function afficherSomme(callback) {  
    let nombre = 3;  
    let somme = callback(nombre);  
    console.log(somme);  
}  
  
afficherSomme(add2); //5
```
### 1.3.3 Fonctions fléchées
Une fonction fléchée utilise une déclaration plus concise qu'une fonction classique.
Prenons, par exemple, la fonction `setTimeout`, qui prends en premier paramètre une fonction de rappel :
```javascript
//syntaxe classique avec fonction anonyme

let str = "Bonjour";

setTimeout(function(str) {
	console.log(str);
}, 1000); // affiche "Bonjour" au bout d'une seconde

//syntaxe fléchée
setTimeout((str => {
	console.log(str);
}, 1000)); // affiche "Bonjour" au bout d'une seconde
```
Si on utilise une expression à droite de la flèche `=>` plutôt qu'un bloc d'instructions, alors l'expression sera interprétée implicitement avec le mot-clé `return` devant :
```javascript
const add = (x) => 3 + 4;
let somme = add(); // 7
```

### 1.3.4 Fonctions anonymes autoexécutantes
Ces fonctions, aussi appelées IIFE sont des fonctions appelées dès qu'elles sont définies.

```javascript
(function () {
    var x = 1; // ici x ne remonte pas dans le contexted'execution global
});
```

- Une deuxième paire de parenthèses crée la fonction directement exécutable

```javascript
(function (){ console.log("hello");}) (); // affiche "hello"
var resultat = (function () {return 1}) ();
console.log(resultat); // affiche 1
```

## 1.4 Manipulation de tableaux

### 1.4.1 Déclarer, lire, modifier, supprimer des éléments

```javascript
let tab = ["pomme", "banane", "orange"];
let tab2 = Array("pomme", "banane", "orange");
```

- Pour lire, on utilise l'indice, comme en C.
- Pour remplir, 
  - on peut utiliser directement l'indice.
  - on peut utiliser `push` pour l'ajouter à la fin.
  - on peut utiliser `unshift` pour ajouter un ou plusieurs éléments au début d'un tableau.
- Pour retirer,
  - on peut utiliser `delete` à un indice donné, sans changer l'indice des autres : il remplace tout simplement par `undefined`
  - on peut utiliser `shift` pour retirer le 1er element et le retourner
  - on peut utiliser `pop` pour retirer le dernier element et le retourner
  - on peut utiliser `splice` pour retirer un ou plusieurs élements a partir d'un indice donné

On peut retirer une valeur donnée avec `indexOf()`
```javascript
let tab = ["pomme", "banane", "orange"];

//supprimer la valeur orange
let index = tab.indexOf("orange"); //renvoie -1 si non trouvé

if (index >= 0){
    tab.splice(index,1);
}
```

### 1.4.2 Itérer sur un tableau
Tu peux faire comme en Java, ou bien avec un `forEach` et une fonction fléchée : 
```javascript
let tab = ["pomme", "banane", "orange"];

tab.forEach((elmt, index) => console.log(elmt));
```

Pour faire un traitement sur chaque élement, tu peux utiliser `map` : elle retourne un nouveau tableau avec le résultat de la fonction fournie en paramètre.
```javascript
let tab = ["pomme", "banane", "orange"];

// passer tous les mots au pluriel
tab = tab.map(elmt => elmt + "s");
console.log(tab); // ["pommes", "bananes", "oranges"]
```