> Las expresiones regulares limitan los inputs del usuario

#### Regex = Regular expresions
### Aplicación en Java
En Java existen varios métodos que nos permiten comparar patrones de cadenas de texto
### A.matches(B)
```Java
if (cadena.matches(".*1(?!2).*")) {
	System.out.println("Sí");
} else {
	System.out.println("No");
}
```

### Ejemplos
```Java
String tmp = "(1[012]|[1-9]):[0-5][0-9]\s(am|pm)"
```
Este patrón corresponde a la hora en formato 12h
## Símbolos
-  `.` Cualquier carácter
-  `^` -> Indica que el String debe empezar con una expresión
-  -> `$` Indica que el String debe finalizar con una expresión
-  `[abc]` String = a  | b | c
-  `[abc][12]` a | b | c, 1 | 2
-  `[^abc]` Dentro de los corchetes significa negación
-  `[a-z1-9]` Indica el rango
-  `[0-9a]` Cualquier carácter entre el 0 y el 9a
-  `A|B` A o B
-  `AB` A.concat(B)

## Cuantificadores
Los operadores de repetición son: `*` *,`+`,`?`
-  `a*` 0 o más veces la 'a'
-  `a+` 1 o más veces la 'a'
-  `a?` 1 o ninguna vez la 'a'
-  `(abc)+` 1 o más veces la cadena 'abc'
-  `a{4} ` la cadena 'aaaa'
-  `a{2,4}` la cadena 'a' entre 2 y 4 veces
-  `a{4,}` la cadena 'a' al menos 4 veces
## Alternativas (Opcionalidad)
Puedes usar `(A|B)` para declarar una división en la lógica

## Anclas
Las anclas son límites de los elementos con los que trabajamos
-  `^A` Indica que el elemento debe comenzar por A
-  `A$` Indica que el elemento debe terminar por A
-  `\bA\b`Indica que el elemento es y solo es igual a A, sin evaluar AB o BA, por ejemplo

## Casos especiales
En estos casos hay que comentar que para poder utilizar las cadenas especiales (llamadas ==regex== ) hay que hacer escapar el primer "\ " con otro back slash

-  `\\w` - carácter alfanumérico
-  `\\W` – carácter no alfanumérico
-  `\\s` – espacio en blanco
-  `\\S` - no espacio en blanco
-  `\\d` - dígito
-  `\\D` - no dígito

### .replaceAll( regex, replacement)
Método para Strings
