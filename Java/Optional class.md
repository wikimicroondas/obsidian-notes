### Definición
`NPE` es el error más común de Java, `Optional` resuelve este problema y su funcionamiento está directamente implementado en Frameworks esenciales, como `Spring Boot`.

## Instanciación

### Optional.ofNullable(value)
Es el estándar. Si el valor es nulo, devuelve un `Optional` vacío de forma segura. Si tiene contenido, lo envuelve.

### Optional.empty()
Devuelve explícitamente un `Optional` vacío. Muy útil si tienes un `if` temprano en tu método y quieres cortar la ejecución devolviendo la ausencia de dato.

### Optional.of(value)
Usar solo en el caso de que el valor no pueda ser nulo. Si se pasa un nulo a este método, saltará un `NullPointerException` (destruyendo el propósito de usar la clase).

```java
String name = scanner.nextLine();
Optional<String> optAddress = AddressBook.getAddressByName(name);
```

## Métodos
---
Centrado en la extracción e integridad de datos, existen muchos más métodos

### .orElse(defaultValue)

Extrae el valor si existe dentro de la caja. Si está vacía, devuelve el `valorPorDefecto` que le hayas indicado. Es perfecto para evitar valores nulos al inicializar variables.

```java
// Si la base de datos no encuentra el rol, asignamos "Usuario_Base"
String rol = repositorioRoles.findRolById(10).orElse("Usuario_Base");
```

### .orElseThrow(Exception)

Imprescindible en la construcción de APIs REST. Si el dato existe, lo desempaqueta y te lo entrega. Si está vacío, lanza directamente una excepción.

Es la forma estándar de cortar la ejecución y devolver, por ejemplo, un error 404 (Not Found) al cliente.

```java
Usuario usuario = repositorioUsuarios.findById(idBuscado)
    .orElseThrow(() ->
    new RuntimeException("El usuario solicitado no existe"));
```
