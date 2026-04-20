Las colecciones principales son definidas en interfaces y son implementadas en clases.
```
Iterable
└── Collection
	├── List
	├── Queue
	└── Set
Map
└── Map
```
`Java Collections Framework`
# Set
`Set` es una colección de valores únicos mutables

```java
// Ejemplo más básico inmutable            - métodos -
Set <String> n = Set.of("a", "b"); // contains, size, isEmpty
```

El uso real reside en sus implementaciones específicas
## HashSet
Utiliza una `Hash Table`, una tabla hash es un índice clave-valor. No garantiza el orden de los elementos.
```java
Set<String> countries = new HashSet<>();
// add, remove, contains
```

## TreeSet
Utiliza `Comparator` > `SortedSet`, garantiza el orden natural de los elementos (a-z, - a +) y herramientas suficientes para 
```java
SortedSet<Integer> sortedSet = new TreeSet<>();
// headSet, tailSet, subSet, first, last
// El objeto comparador no tiene un uso claro hasta ahora, imprime una cadena de caracteres con la función
```

## LinkedHashSet
Utiliza una `LinkedList` y garantiza el orden en el que los elementos han sido introducidos.
```java
Set<Character> characters = new LinkedHashSet<>();
```

### Igualdad
- No hay duplicados
- Son los mismos conjuntos de elementos

# List
La implementación más básica usa `List.of` y es inmutable, pero las de uso real son las siguientes:
## ArrayList
Es una implementación con una base de  `Array`
```java
List<String> mutableList = new ArrayList<>(immutableList);
// add, addAll, contains, get, size, subList
```

## LinkedList
Utiliza punteros para formar una lista, cada elemento se apunta a otro, de forma que modificarlo supone muchos menos recursos en listas muy grandes. A cambio, iterar sobre ella supone `O(n)`
```java
List<Integer> numbers = new LinkedList<>();
```

### Igualdad
- Mismo orden de elementos
- Mismos elementos y tamaño

# Map
Es un conjunto de pares clave-valor, las claves son únicas pero los elementos pueden repetirse
```
// Key-Value (K, V)
put, get, contains{ Key | Value }, putIfAbsent, getOrDefault
// Methods that return other collections
keySet, values, entrySet
```
## HashMap
```java
Map<Integer, String> products = new HashMap<>();
// get(K), putIfAbsent(3000, "Mouse")
```

## TreeMap
Ordenado por claves naturalmente
```java
TreeMap<String, String> capitalCities = new TreeMap<>();
```

## LinkedHashMap
```java
Map<Integer, String> products = new LinkedHashMap<>();
```
