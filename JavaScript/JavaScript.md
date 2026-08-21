### Definición
> JS Es un lenguaje de programación ligero e interpretado.

## 0. Implementación

Antes de cerrar la etiqueta `</body>` se añade `<script>` añadiendo la fuente `src=""`.

```html
<body>
(...)
<script src="script.js"></script>
</body>
```

## 1. Fundamentos de JS
### Consola. Template Literals

Para poder detectar errores dentro del flujo de la lógica es útil usar la consola.

```JavaScript
const nombre = "Ana";
const edad = 25;

console.log(`Me llamo ${nombre} y tengo ${edad} años`);
```

### Operadores
-  Potencias. `**`.
-  Comparador. `===`.

## 2. Funciones
### Function Expression
==No tiene prioridad de ejecución==. (no hoisted).
```JavaScript
// Una variable contiene el valor devuelto por la función
let dividir = function(a, b) { return a / b; };
// Es una cuestión de boiled code, reduce las líneas, nada más
let resultadoDivision = dividir(100, 20);
console.log(`Resultado de la división: ${resultadoDivision}`);
```

### Arrow Function
Son otra forma del mismo concepto, function expression.
```JavaScript
// Expresión tradicional
let cuadradoTradicional = function(x) { return x * x; };

// Arrow | variable | function() = => (devuelve)
let cuadradoArrow = x => x * x;
// Si hay más de una variable hace falta un paréntesis.
```

## Arrays
Listas de varias variables
```JavaScript
let productos = ["Portátil", "Ratón", "Teclado"];
```
## Métodos
.length sin paréntesis.
### For each (JS)
```JavaScript
for (let seccion of secciones) {
	console.log(seccion);
}
```
### array.push(elemento)
Añade al final
```JavaScript
carrito.push("Cuaderno");
```
### array.splice(inicio, cantidad, elementos)
-   ==Cantidad > 0.==
	Elimina(desde, cantidad)
```JavaScript
let tecnologias = ["HTML", "CSS", "jQuery"];
tecnologias.splice(2, 1);
// ["HTML", "CSS"]
```
-  ==Cantidad = 0.==
	Añade(desde, 0, "JavaScript")
```JavaScript
tecnologias.splice(2, 0, "JavaScript");
// ["HTML", "CSS", "JavaScript"]
```
### array.indexOf("valor")
```JavaScript
let extensiones = [".html", ".css", ".js"];
let posicion = extensiones.indexOf(".js"); // 2
```
### array.includes("valor")
Es un boolean
```JavaScript
let roles = ["admin", "editor", "usuario"]; console.log(roles.includes("admin")); // true
```

## Notas
### .querySelector(" ")
querySelector entiende de CSS, por lo que para seleccionar etiquetas de CSS es mucho más claro.