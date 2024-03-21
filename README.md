# Índice
- [Funciones](#funciones)
- [Scope](#scope)
- [Shadowing](#shadowing)
- [Arrays](#arrays)
  
# Repaso de conceptos
Para este repaso tenéis una carpeta starter_code con todo lo necesario para practicar, pero ojo! tendréis que enlazar al html el archivo script.js:
```
<script src="Aquí la ruta del archivo"></script>
```


# Funciones
Una función es un trozo de código que nos sirve para ejecutar instrucciones en nuestra aplicación, hay muchas formas de escribirlas pero nos vamos a centrar en la más común.

## ¿Cómo se estructura?
Una función sigue una estructura muy simple y versátil que nos será de mucha ayuda. Haremos la estructura paso a paso:
```
function myName
```
Para definir la funcion lo primero que haremos será usar la palabra "function" y luego escribir el nombre que queremos que reciba dicha función, para este ejemplo he usado "myName" pero podéis poner la que más os guste o sea más descriptiva para el trabajo que realice la función.

```
function myName(myParam1, myParam2)
```
El siguiente paso es abrir parentesis, esto es necesario en todas las funciones. "myParam1" y "myParam2" son los datos que recibirá mi función, pero no son obligatorias, veremos cuál es su utilidad más adelante.

```
function myName(myParam1, myParam2) {
  //Escribimos lo que hace la función
}
```
Las llaves: {} definen el alcance de nuestra función ¿Que quiere decir esto? significa que todo lo que escribamos dentro de las llaves será lo que ejecute la función, todo lo que esté fuera de ellas es ajeno a la función.
Vamos a hacer una pequeña prueba, en tu editor de preferencia pon este código.
```
function myName(myParam1, myParam2) {
  console.log(myParam1, myParam2)
}

console.log(myName)
```
Si nos fijamos en la consola de nuestro navegador, nos devuelve function myName(myParam1, myParam2), pero no nos hace el console.log() que tenemos dentro ¿por qué?
Pues ahí es donde entran los paréntesis, cuando queremos ejecutar lo que hace una función, tenemos que poner el nombre de dicha función y escribir paréntesis seguidamente, esto lo que hará es "activar" la función.
```
function myName(myParam1, myParam2) {
  console.log(myParam1, myParam2)
}

console.log(myName())
```
Perooo... ahora nos hace el console.log(), sí, pero no nos muestra nada. Ahí es donde entran los params, cuando invocamos a la función podemos agrerar los datos que queramos y myParam1 y myParam2 copiaran esos valores y los tomaran como suyos. Aquí un ejemplo:
```
function myName(myParam1, myParam2) {
  console.log(myParam1, myParam2)
}

console.log(myName("Alma", "Cruz"))
//Ahora myParam1 tendrá el valor de "Alma" y myParam2 de "Cruz"
```
Los parámetros pueden tener el nombre que prefieras y puedes añadir tanto como gustes, para diferenciar que valor toma cada parámetro se hace separando los valores con una coma en la llamada. Ahora el console.log() nos mostrará: Alma, Cruz

Ahora imaginémos que tenemos una función que, por si acaso, queremos que en caso de que no le pasemos valores a los parámetros tenga uno predeterminado, para que así siempre pueda mostrar algo.
```
function myName(myParam1="Adri", myParam2="Suarez") {
  console.log(myParam1, myParam2)
}

console.log(myName())
```
Ahora, el console.log() mostrará: Adri, Suarez

Y antes de terminar con las funciones, un recordatorio amabale. Las funciones nombres pueden ser llamadas cuantas veces quieras, en cambio aquellas que no tengan nombre solo podrán ser utilizadas una unica vez y en el momento. A estas funciones se les llama anónimmas y tienen la siguiente estructura:
```
function () {
  //Haz algo
}
```
Como véis, la única diferencia a nivel de sintaxis es que no tienen nombre.

### Ejercicios para repasar funciones
https://www.codewars.com/kata/523b4ff7adca849afe000035/train/javascript

# Scope
El scope es donde declaramos las variables y hasta donde son accesibles. Por ejemplo, si definimos una variable en el scope global, sin estar encerrada entre llaves, como veremos en el siguiente ejemplo. Será accesible desde cualquier parte de nuestra aplicación (o archivo js).
```
var myGlobalVar = 'Hello World!' //scope global
```
Ahora, si declaramos una variable dentro de llaves esta pasará a estar dentro del scope local, el scope local se refiere a todo aquello que esté entre llaves. Aquí un ejemplo.
```
var myGlobalVar = 'Hello World!' //scope global

{
var myLocalScope = 'Hello rebooter' //scope local
}

if(//your condition goes here){
var anotherLocalScope = 'Hello people!' //scope local
}

function myFunc(){
 var anotherOtherLocalVariable = 'Hello? Hello!' //scope local
}
```
Cada variable definida dentro de las llaves solo existirá en su scope local, esto quiere decir que si tratamos de hacer un console.log() a una variable que no exista dentro de esas llaves o que no esté definida en el scope global, recibiremos un aviso de que esa variable no existe.

```
var myGlobalVar = 'Hello World!' //scope global

{
var myLocalScope = 'Hello rebooter' //scope local
console.log(myGlobalVar) // 'Hello World!'
}
console.log(myLocalScope) // myLocalScope is not defined

if(//your condition goes here){
var anotherLocalScope = 'Hello people!' //scope local
}

function myFunc(){
console.log(anotherLocalScope) // anotherLocalScope is not defined
 var anotherOtherLocalVariable = 'Hello? Hello!' //scope local
}
```
Visto esto, te habrás dado cuenta de que podemos acceder a las variables globales desde una local pero no al revés, esto es gracias a cómo funciona JavaScript, pero esto nos permite dar paso al siguiente concepto.

### Ejercicios para repasar el scope
https://www.codewars.com/kata/56d344c7fd3a52566700124b
https://www.codewars.com/kata/526ec46d6f5e255e150002d1

# Shadowing
El shadowing es cuando definimos una variable con el mismo nombre que otra, esto hace que, dependiendo de donde operemos con esa variable, tomará un valor u otro. Aquí un ejemplo.
```
var myVariable = 'Alma'
console.log(myVariable) // Alma
var myVariable = 'Adri'
console.log(myVariable) // Adri
```
Esto es en el scope global, pero si lo hacemos de scope global a local ocurre igua. Otro ejemplo.
```
var myVariable = 'Alma'
console.log(myVariable) // 'Alma'

{
var myVariable = 'Adri'
console.log(myVariable) // Adri
}
```
Cuando hacemos el console.log() de myVariable dentro de las llaves y queremos acceder al valor del scope global, Javascript se parará en la variable del scope local porque ahí se está redeclarando la variable y opacará el valor anterior. Este fenómeno se llama shadowing.

# Arrays
Las arrays: [], son un tipo de objetos en JavaScript, nos sirve para almacenar diferentes tipos de datos dentro de ellas. Una array puede tener cualquier tipo de dato dentro suya:
```
let myArray = [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]]
```
Como veis, una array es como una caja a la que le puedes echar cualquier cosa, incluso otras cajas(arrays).
Esto es sencillo, pero la cosa puede complicarse a la hora de operar con ellas, cómo acceder a los valores y modificar su contenido, ahí entran los métodos de array.

## Añadir o quitar datos de una array
### .push()
El método push introducirá el elemento deseado al final de la array
```
let myArray = [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]]

myArray.push(4)

console.log(myArray) // [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"], 4] //El valor se añade al final
```
### .pop()
El método de pop nos permite sacar el elemento situado al final de la array
```
let myArray = [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]]

myArray.pop()

console.log(myArray) // [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]] //El elemento del final se elimina
```
### .shift()
shift hace lo mismo que el .pop() pero al principio de la array.
```
let myArray = [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]]

myArray.shift()

console.log(myArray) // [2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]] //El elemento del principio se elimina
```
### .unshift()
Igual que el .pop() pero añadiendo el elemento al principio de la array
```
let myArray = [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]]

myArray.unshift("Hellow world!")

console.log(myArray) // ["Hellow world!", 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]] //El elemento se añade al principio de la array
```

## Accediendo a una array
Para acceder a una array y obtener el valor deseado tenemos varias maneras, podemos acceder directamente al valor usando el índice. Pero para ello debemos de saber cual es y no siempre sabemos la longitud exacta de una array o si puede cambiar de aquí a un futuro. Para ello, iteramos en base a su longitud.
```
let myArray = [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]]

myArray[0] // con [0] estamos accediendo al índice 0 del array que pertenece al elemento 1 
```
Las arrays comienzan con índice 0, así que si tienen 6 elementos tendrá 5 índices.
Como dijimos antes, no siempre sabemos con exactitud la cantidad de elementos de una array o si puede cambiar, por eso iteramos en base a su longitud con un bucle for y el método length
```
let myArray = [1, 2, 3, "Hola", {name: 'Alma'}, ["Otra", "array"]]

for(let index = 0; index < myArray.length; index++) {
  console.log(myArray[index])
}
```
Analicemos lo que está pasando en el código. Primero el for se divide en 3 partes:
for(declaración de la variable; condición del bucle; acción)

- Declaración de la variable: declaramos una variable con el nombre deseado, en este caso hemos usado index para que sea más descriptivo y le asignamos el valor 0.
- condición del bucle: la condición que queremos que se tenga en cuenta para ejecutar la acción, en el primer ciclo index < myArray.length se traducirá en 0 < 6, como la condición se cumple (devuelve true) la acción se ejecuta
- Acción, lo que queremos hacer con la variable, normalmente se suma o resta según lo que deseemos.

Una vez visto esto, ahora podemos pasar a lo que ocurre dentro, el console.log() irá mostrando en la consola el valor del índice, al principio será 0 y pasará por todos los numeros hasta llegar a 6, en cuanto llegue a 6, que en este caso es la longitud de nuestra array, la condición pasará a devolver false y se dejará de ejecutar la acción y con ello el console.log()
### Ejercicios para repasar arrays
- https://www.codewars.com/kata/511f0fe64ae8683297000001
- https://www.codewars.com/kata/53dc54212259ed3d4f00071c
- https://www.codewars.com/kata/5783d8f3202c0e486c001d23
- https://www.codewars.com/kata/544a54fd18b8e06d240005c0
