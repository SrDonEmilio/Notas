# TypeScript

Aarón Cervantes / Meetup GDG UNAM - 28/03/2020

---

Es un superset de JS que se compila a JS, funciona en cualquier navegador.

## Características

- Lenguaje
- Compilador
- Lenaguage Service

## Instalación

```shell
npm i -g typescript
```



Se puede practivar online en [Playground](https://typescriptlang.org/play/index.html)



## Primeros Pasos

Como su finaliad es la de proveer de un tipado más fuerte a JS, se tiene que definir el tipo de variable

```typescript
const menssage: string = 'Hello, world'
let nombre = 'Emilio'

console.log(`${message}, ${ nombre }`)
```



```typescript
var resultado;

function add(n1: number, n2: number){
    resultado = n1 + n2;
    return resultado;
}

let suma = add(1, 2);
console.log(suma);
console.log(resultado);
```



## El Scope

Debido a que TS se compila en el modo estricto de JS, el uso de *var* y *let* se vuelve más relevante

```typescript
if(true){
    let hola = '';
}

console.log(hola);
```

El output de lo anterior, si de por sí  en JS ya estaba mal, en TS se genera un error durante el compilado. Lo "correcto" sería:

```typescript
if(true){
    var hola = '';
}

console.log(hola);
```

O directamente, declarar la variable antes de entrar al condicional

```typescript
var hola; // o let hola
if(true){
    hola = ''
}

console.log(hola);
```



---



TS te ayuda a detectar tempranamente errores, durante el desarrollo, sin necesidad de ejecutar el código ocurre en en JS.

Aunque TS está basado en JS, siempre se tiene que compilar, los navegadores todavía no acepta TS directamente. (*En parte creo que está bien, porque entonces se perdería un poco la discipliona que te provee TS*.)



## Funciones

``` typescript
function resta(a, b){ return a-b; }
```

Aunque en JS esto sería correcto, en TS hay advertencias porque no están explícitos los tipos. Lo correcto sería:

```typescript
function resta(a: number, b: number){ returm a-b; }
```

En el caso de la resta, no se nota tanto, pero en el caso de la suma sí puede llegar a generar más conflicto

```typescript
function suma(a, b){ return a+b; }
```

En el ejemplo anterior, bien podría ser una suma numérica o la concadenación de strings, por tanto lo correcto sería:

```typescript
function suma(a: number, b: number){ return a+b; }
```

Y para asegurarnos más, podríamos poner

```typescript
function suma(a: number, b: number): numner {
    return a+b;
}
```



*Dejaré de tomar apuntes para poner más atención al ejercicio*



