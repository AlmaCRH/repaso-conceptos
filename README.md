# Repaso de conceptos
Para este repaso tenéis una carpeta starter_code con todo lo necesario para practicar, pero ojo! tendréis que enlazar al html el archivo script.js:
```
<script src="Aquí la ruta del archivo"></script>
```


# Funciones

## ¿Qué es una función?
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

# Scope
## ¿Qué es el scope?
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

# Shadowing
## ¿Qué es el shadowing?
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
