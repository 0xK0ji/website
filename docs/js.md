# Fondamentaux

## Exécuter du JavaScript

Deux méthodes possibles :

1. Depuis le HTML 

```html
<body>
	<script>
		// Your JavaScript goes here!
		console.log("Hello, World!")
	</script>
</body>
```

1. Importer depuis un fichier js dans le HTML

```html
<body>
	<script src="javascript.js"></script>
</body>
```

## Vérifier le type d’une variable
a
```jsx
typeof myint;
```

## Variable

```jsx
let message;
message = 'Hello';
alert(message); //afficher le contenu de la variable

// On peut aussi directement déclaré la variable et l'assigné
let message = 'Hello';

//On peut utilise $ et _ comme nom de variable
let $ = 1;
let _ = 2;
alert($ + _); //3
```

## Constante

```jsx

// Il vaut mieux nommer les constante non calculé durant le runtime en majuscule
const AGE = 10;
const COLOR_RED = "#F00";

// QUand on a besoin de choisir une couleur
let color = COLOR_RED
alert(color); // #FF7F00
```

## Nombres

```jsx
// Javascript utilise l'operateur + pour additioné ou concaténer
z = "ab" + "bc";

// Javascript essaie de convertir les strings en nom, cela ne fonctionne pas pour l'opérateur +
z = "30" \ 5; //6

z = "30" + 30; //3030

// Si une opération échoue, le résultat est NaN (Not a Number)
z = 100 / "Apple"; //z = NaN

// On peut vérigier si le resultat est NaN avec la fonction 
// isNaN()

isNaN(x);

// Infinity ou -Infinity est retourné si le nombre est en
// dehors du nombre le plus large possible

let myNumber = 2;
// Execute until Infinity
while (myNumber != Infinity) {
  myNumber = myNumber * myNumber;
}

// Hexadecimal -> Précédé par 0x
let x = 0xFF;

// On peut afficher les nombres dans une base différente
// avec toString()

myNumber.toString(16); //Affiche le nombre en base16

// Pas recommandé : il est possible de créé un nombre en tant qu'objet
let x = new Number(500);
```

## Méthodes pour nombre

```jsx
// Cast un string en nombre : Number(x)
let z = "30";
let y = Number(z) + 4; // 34
```

## Opérateur == et ===

- == : loose equality → converti les variables afin qu’elles soient du même type avant de les comparer. attention : les booléen sont convertis en nombre (1 ou 0)
- === : strict equality → compare directement la valeur des variables
    - ! == : not equal to

## Strings

3 types de strings possible : 

- “”
- ‘’
- ``  ->  appelé template literal -> permet d'embed du javascript

```jsx
// Exemple template lital
const name = "Chris";
const greeting = `Hello, ${name}`

//multiligne 
const newline = `One day you finally
knew what had to do, and begin`;

const newline = "One day you finally\nknew what had.."
```

On peut convertir une varible en string avec la fonction String()

```jsx
const myNum2 = 123;
const myString2 = String(myuNum2);
```

## Strings méthodes importantes

```jsx
// Taille d'une strings
let text = "blabla";
let length = text.length; 

//Extraire des caractères
let char = text.at(position); //Permet d'utiliser un index negatif
let char = text[2]; //Obtenir le 3eme caractere
let char = charAt(position); //Retourne un caractère à l'index spécifié
let char = charCodeAt(position) //Retourne le code UTF-16 d'un caractère

//Extraire une slice
let char = text.slice(start, end); //Si le second parametre est omis, prend du start jusqu'à la fin
let char = text.substring(start, end); //les arguments négatif sont traité comme 0
let char = text.substr(start, length)

//Majuscule et minuscule
let char = text.toUpperCase();
let char = text.toLowerCase();

//Joindre des strings
let text1 = "Hello";
let text2 = "World";
let text3 = text1.concat(" ", text2) //Hello World

// Trim les leading et ending whitespace
let text1 = text2.trim(); //trim leading & ending whitespace
let text1 = text2.trimStart(); //trim les leading whitespace
let text1 = text2.trimEnd();

// Padding -> attention padStart et padEnd sont des strings méthod
// Pour padder un nombre il faut d'abord le convertir
test.padStart(4, "0"); //Ajoute 4 zero au debut
test.padEnd(4,"0"); //Ajoute 4 zero à la fin

//Repeter une string
let text2 = "Hello";
let text1 = text2.repeat(2); //HelloHello

//Remplacer le contenu (seulement le first match)
let text = "Visit Microsoft";
let text2 = text.replace("Microsoft","Apple"); //Visit Apple
//flag /i pour enlever la casse
let text2 = text.replace("/MICROSOFT/i", "Apple");
//flag /g pour changer tous les matchs
let text2 = text.replace("/MICROSOFT/g", "Apple");
//Remplacer tous les match avec la fonction replaceAll()
let text2 = text.replaceAll("Cat","Dog");
//Il faut ajouter le flag /g si on veut untiliser un regex
let text2 = text.replaceAll(/Cat/g,"Dog");

//Convertir un String en Array avec split()
stringArray = text1.split(","); //Split à la virgule
stringArray = text1.split(""); //Split tous les caractères
StringArray = text1.split(); //La strings entiere est contenu à l'index 0

```

## Function

### Function Déclaration

```jsx
function name(paramter..) {return x;}
```

### Scope

Les functions peuvent utilisé des variables exterieur seulement si elles n’existent pas localement dans la fonction. **mieux vaut minimiser l’utilisation de variable global**.

### Anonyme Function & Arrow Function

```jsx
//Anonymous function : fonction sans nom
//Souvent utilisé lors qu'une function demande une fonction 
//en paramètre
(function () { alert("hello"); });

//les fonctions Arrow est une forme alternative des 
// fonction anonyme
textBox.addEventListener("keydown", (event) => { codeblock..;});
//On peut enlever les parenthese s'il n'y a qu'1 argument
textBox.addEventListener("keydown", event => { codeblock..;});
//Si elle ne contient qu'une ligne, et que c'est un return
//alors on peut enlever les accolades
//Exemple function Arrow qui contient return item * 2
x = orginals.map(item => item * 2);
```

### Paramètre

Si une valeur n’est pas passé à un paramètre, alors sa valeur est **undefined**

#### Valeur par défaut

```jsx
function name(param1 = "test", param2)
```

### Function Expression

Il est possible de créer une nouvelle fonction au milieu d’une expression, et même stocker dans une variable : 

```jsx
let sayHi = function() { alert("Hello"); };
```

Une function est une valeur, si on utilise la variable sans mettre de paranthèse à la fin, alors c’est le code source de la fonction qui est passé comme valeur.

```jsx
function sayHi() { alert("Hello") }
let func = sayHi //la fontion sayHi est copié dans func
func(); //Hello
sayHi(); //Hello
```

## Array

Les array en javascript sont des objets. Nous pouvons mélanger n’importe quel type de donnée.

Attention, les array ne supporte pas l’utilisation de nom à la place d’index (appelé hash ou associative array). 

Si on utilise un nom à la place d’un index, alors on ne créé pas un array mais un objet.

```jsx
const array_name = [item1, item2, ...];

const cars = [];
cars[0]= "Saab";
cars[1]= "Volvo";
cars[2]= "BMW";

//Pas consellé (lisibilité) : utilisation de new
const cars = new Array("Saab", "Volvo", "BMW");

//Convertir un array en string
const fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.toString();
//Resultat : Banana,Orange,Apple,Mango

//Accéder à l'entiereté de l'array : avec le nom
const arr2 = arr1

//Taille d'un array
array.length

//Trier un array
array.sort()

//Ajout d'un élément
fruits.push("Lemon");
//Ajout d'un élément par l'index (attention peut créer des trous)
fruits[fruits.length] = "Lemon");

//Looper sur un array
//via for(...)
for (i=0; i < arr.length ;i++) {...}
//via forEach()
function myFonction(value) { console.log(value); }
arr.forEach(myFonction);
```

## Loop et collection

```jsx
//Looper sur une collection
const cats = ["Felix","Catty","Lol"];
for (const cat of cats) {...}

//map() : permet d'appliquer une fonction sur une collection 
//et de créer une nouvelle collection avec les items changés
const cats = ["felix","catty","lol"];
const catsUpper = cats.map(toUpper);

//filter() : permet de filtrer les éléments d'une collection
//grâce à une fonction et retourner les éléments qui match
fonction fCat(cat) { return cat.startwith("f"); }
const cats = ["felix","catty","lol"] 
const catsfiltered = cats.filter(fCat);
```

## DOM

Le DOM (document object model) est une representation tree-like d’une page web.

## Cibler un node

Pour cibler un node, on peut utiliser plusieurs méthode : 

Selecteurs du style CSS (.div#container…) ainsiq que des selecteurs relationnel

```jsx
const container = document.querySelector('#container');
console.dir(container.firstElementChild);
//Selectione le première enfin de #container
```

### Méthodes des node

#### Query Selector

Il est important de noté que la méthode “querySelectorAll” ne retourne pas un array mais bien une nodelist. Une nodelist n’a pas toutes les méthodes d’un array. Cependant, on peut convertir la nodelist en array avec la fonction `Array.from()`

```jsx
//Selectionner la première occurance d'un node
//Retourne une reference du premier match
element.querySelector(selector)

//Selectionner toutes les occurances d'un node
//Retourne une "nodelist" de reférence de tous les match
element.querySelectorAll(selector)
```

#### getElementById()
```html
<div id='message'></div>
```
```jsx
const ele = document.getElementById('message');
```

#### getElementsByName()
Retourne une `Node List` de tous les éléments HTML qui partage la même valeur pour l'attribut `name`.
```html
<div name="boite"></div>
```
```jsx
const ele = document.getElementByName('boite');
```

#### getElementsByTagName()
Est une méthode de l'objet `document` qui retourne une `Node List` de tous les éléments HTML qui partage le même `tag`.
```html
<div>bla</div>
```
```jsx
const ele = document=getElementsByTagName('div');
```
#### getElementsByClassName()
Retourne un objet array-like des éléments enfant avec le nom de classe spécifié.
```jsx
const elements = rootElement.getElementsByClassName(names);
```

### Création d’un élément

```jsx
//document.createElement(tagName, [options])
//Il est possible d'ajouter des options
const div = document.createElement('div');
```

Il faut noté que cette méthode ne place pas l’élément dans le DOM (il est créé en mémoire), cela permet notamment de manipuler l’élement (ajout de style..) avant de le placer sur la page.

### Ajout de l’élement sur le DOM

Pour l’ajouter sur la page, on peut utiliser les méthode suivantes : 

```jsx
//Ajout de l'élément en tant que dernière enfant de parentNode
parentNode.appendChild(childNode)

//Insert newNode dans parentNode avant referenceNode
parentNode.insertBefore(newNode, referenceNode)
```

### Suppression d’un élément

```jsx
// Supprime child de parentNode sur le DOM et retourne une reference à child
parentNode.removeChild(child)
```

### Ajout de style inline

```jsx
//Ajout de la règle de style indiqué
div.style.color = 'blue';

//Ajout de plusieurs règles de style
div.style.cssText = 'color: blue; background: white;';

//Ajout de plusieurs règles de style
div.setAttribute('style', 'color: blue; background: white;');
```

Les règles css en kebab-cased (avec des tiret) doivent être accéder par du camelCase ou entre crochet :

```jsx
div.style.background-color // doesn't work - attempts to subtract color from div.style.background
div.style.backgroundColor // accesses the div's background-color style
div.style['background-color'] // also works
div.style.cssText = "background-color: white;" // sets the div's background-color by assigning a CSS string
```

### Editer des attributs

```jsx
div.setAttribute('id', 'theDiv');                              
// if id exists, update it to 'theDiv', else create an id
// with value "theDiv"

div.getAttribute('id');                                        
// returns value of specified attribute, in this case
// "theDiv"

div.removeAttribute('id');                                     
// removes specified attribute
```

### Travailler avec des classes

```jsx
//Ajouter une class à un élément
div.classList.add('new');

//Supprimer une class d'un élément
div.classList.remove('new);

//Supprimer la class new si elle existe et vise versa
//Cette méthode est préférée à la suppression/ajout
div.classList.toggle('new');
```

### Ajouter du contenu texte

```jsx
div.textContent = 'Hello World!'                               
// Créé un node text qui contient "Hello World!"
// et l'insert dans div
```

### Ajouter du contenu HTML

```jsx
div.innerHTML = '<span>Hello World!</span>';
//Rendu de l'HTML dans la div
```

Attention : il vaut mieux ajouter du texte via **textContent** plutot que via l’ajout d’HTML, car cela peut engendrer un risque de sécurité.

### Délayer le contenu du javascript

Pour manipuler le DOM, il faut que le javascript soit appelé avant sa création. Pour cela, on peut utiliser deux méthodes :

- Inclure le javascript à la fin du fichier html
- Ajouter le keyword `defer`  dans le tag script afin de la lancer après le parsing de l’HTML

```jsx
<head>
	<script src="js-file.js" defer></script>
</head>
```

## Events

Les Events sont des actions qui sont réalisées sur notre page tel que un clic-souris ou un keypress, et utilise JavaScript pour que notre page web écoute et réagit à ses evenements.

Il existe trois façon primaire d’ajouter un Events : 

- **Méthode 1** : Spécifié l’attribue de function directement dans le HTML
- **Methode 2** : Spécifié un attribue on[eventType] (exemple onclick, onmouse, ect..) sur le node DOM avec Javascript
- **Méthode 3 [préféré] :** Attaché un `event listener`  sur le node DOM dans le JavaScript.

**Méthode 1** 

Pas idéal car ajoute du javascript dans notre HTML

```html
<button onclick="alert('Hello World')">Click Me</button>
```

**Méthode 2**

```html
<!-- The HTML File-->
<button id="btn">Click Me</button>
```

```jsx
// The Javascript File
const btn = document.querySelector('#btn");
btn.onclick = () => alert("Hello World");
```

**Méthode 3** 

Cette méthode est plus fexible et puissante, on peut ajouter plusieurs event listener à un même node.

```html
<!-- The HTML File-->
<button id="btn">Click Me</button>
```

```jsx
// The Javascript File
const btn = document.querySelector('#btn");
btn.addEventListener('click', () => {
	alert("Hello World");
});
```

**Remarque** : 

- Des fonctions nommés peuvent être utilisé à la place des arrows function. Cela permet d’améliorer la lisibilité du code.
- Sur les 3 méthodes nous pouvons accéder à plus d’information sur l’event en passant un paramètre à la fonction que nous appelons (callback function) :
    
    `btn.addEventListener(’click’,function (e) { console.log(e);});`
    
    le **`e`** est un objet qui reference l’**event** lui même, il contient des méthodes qui permet par exemple de déterminer quel clic a été appuyé.
    
    ```jsx
    btn.addEventListener(’click’,function (e) { 
    	console.log(e.target); //e.target se refere à l'élement cliqué
    	e.target.style.background = 'blue';
    }
    ```
    

### Attacher un event listener à un groupe de node

Pour ça on selectionne plusieurs node avec `document.querySelectorAll(’element’)` couplé avec `nodelist.forEach()`

```html
<div id=container>
	<button id="1">Click Me</button>
	<button id="2">Click Me</button>
	<button id="3">Click Me</button>
</div>
```

```jsx
//buttons est une node list, Cela agit presque comme un array
const buttons = querySelectAll('button');

//On utilise la méthode forEach pour itérer au travers de buttons
buttons.forEach((button) => {
	//Pour chaque button on ajoute le listener 'click'
	button.addEventListener('click', () => {
		alert(button.id);
	});
});
```

### Liste des Events utiles

- click
- dblclick
- keydown
- keyup



