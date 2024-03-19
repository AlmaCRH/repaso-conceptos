# repaso-conceptos
(poner aquí el link de html y etc)
# Funciones

## ¿Qué es una función?
Una función es un trozo de código que nos sirve para ejecutar instrucciones en nuestra aplicación, hay muchas formas de escribirlas pero nos vamos a centrar en la más común.

## ¿Cómo se estructura?
Una función sigue una estructura muy simple y versátil que nos será de mucha ayuda.
Haremos la estructura paso a paso:
```
function myName
```
Para definir la funcion lo primero que haremos será usar la palabra "function" y luego escribir el nombre que queremos que reciba dicha función, para este ejemplo he usado "myName" pero podéis poner la que más os guste o sea más descriptiva para el trabajo que realice la función.

```
function myName(myParam1, myParam2)
```
El siguiente paso es abrir parentesis, esto es necesario en todas las funciones. "myParam1" y "myParam2" son los datos que recibirá mi función, pero no son obligatorias, veremos cuál es su utilidad más adelante.

```
function myNmae(myParam1, myParam2) {
  //Escribimos lo que hace la función
}
```
Las llaves: {} definen el alcance de nuestra función ¿Que quiere decir esto? significa que todo lo que escribamos dentro de las llaves será lo que ejecute la función, todo lo que esté fuera de ellas es ajeno a la función.
Vamos a hacer una pequeña prueba, en tu editor de preferencia pon este código.
```
function myNmae(myParam1, myParam2) {
  console.log(myParam1, myParam2)
}

console.log(myName)
```
Si nos fijamos en la consola de nuestro navegador, nos devuelve function myName(myParam1, myParam2), pero no nos hace el console.log() que tenemos dentro ¿por qué?
Pues ahí es donde entran los paréntesis, cuando queremos ejecutar lo que hace una función, tenemos que poner el nombre de dicha función y escribir paréntesis seguidamente, esto lo que hará es "activar" la función.
```
function myNmae(myParam1, myParam2) {
  console.log(myParam1, myParam2)
}

console.log(myName())
```
Perooo... ahora nos hace el console.log(), sí, pero no nos muestra nada. Ahí es donde entran los params, cuando invocamos a la función podemos agrerar los datos que queramos y myParam1 y myParam2 copiaran esos valores y los tomaran como suyos. Aquí un ejemplo:
```
function myNmae(myParam1, myParam2) {
  console.log(myParam1, myParam2)
}

console.log(myName("Alma", "Cruz"))
//Ahora myParam1 tendrá el valor de "Alma" y myParam2 de "Cruz"
```

