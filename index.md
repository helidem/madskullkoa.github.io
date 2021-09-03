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

__Les opérateurs ternaires ? et :__

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
__Switch...case...break__

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

__for, do...while, while__
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
Si on utilise une expression à droite de la flèche => plutôt qu'un bloc d'instructions, alors l'expression sera interprétée implicitement avec le mot-clé `return` devant :
```javascript
const add = (x) => 3 + 4;
let somme = add(); // 7
```

