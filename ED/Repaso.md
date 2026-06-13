# Tema 5: JUnit
> JUnit es un framework, da herramientas para el tests unitarios

Para `JUnit 6` configuraremos `build.gradle.kts` de esta manera:

```kotlin
dependencies {
	testImplementation(platform("org.junit:junit-bom:6.0.2"))
	testImplementation("org.junit.jupiter:junit-jupiter")
	testRuntimeOnly("org.junit.platform:junit-platform-launcher")
}

tasks.test {  
    useJUnitPlatform()  
}
```

## Annotations
| Annotation           | Use                        | Example                    |
| -------------------- | -------------------------- | -------------------------- |
| `@Test`              | Flags a method as a test   | @Test<br>void sumaBasica() |
| `@BeforeEach`        | It runs before each test   | Initialize data            |
| `@AfterEach`         | It runs after each test    | Clean up resources         |
| `@BeforeAll`         | Runs once before all tests | Global configuration       |
| `@AfterAll`          | Runs once after all tests  | Global clean up            |
| `@Disabled`          | Disables a test            | @Disabled("Pendiente")     |
| `@DisplayName`       | Human readable test        | "Positive sum"             |
| `@ParameterizedTest` | Test with parameters       | - - -                      |
## Assertions
| Method                     | Checks                       | Example                                    |
| -------------------------- | ---------------------------- | ------------------------------------------ |
| assertEquals(e, o)         | Equal                        | assertEquals(5, r)                         |
| assertNotEquals(e, o)      | Distinct                     | assertNotEquals(0, r)                      |
| assertTrue(c)              | True conditional             | assertTrue(x > 0)                          |
| assertFalse(c)             | False conditional            | assertFalse(x < 0)                         |
| assertNull(o)              | Is null                      | assertNull(obj)                            |
| assertNotNull(o)           | Isn't null                   | assertNotNull(obj)                         |
| assertSame(e, o)           | Same object                  | assertSame(a, b)                           |
| assertNotSame(e, o)        | Distinct objects             | assertNotSame(a, b)                        |
| assertArrayEquals(e, o)    | Same array                   | assertArrayEquals(arr1, arr2)              |
| assertThrows(ex, l)        | If an exception is thrown    | assertThrows(IOException.class, () -> f()) |
| assertDoesNotThrow(I)      | If an exception isn't thrown | assertDoesNotThrow(() -> divide(10, 2))    |
| assertThrowsExactly(ex, l) | if an ex is thrown somewhere | assertThrowsExactly( - - - )               |
# Tema 6: Javadoc
> Documentación generada automáticamente

## Etiquetas
### Métodos
```java
/**
 * Realiza la división entera de dos números.
 *
 * @param dividendo Número que se va a dividir
 * @param divisor Número por el que se divide
 * @return Resultado de la división
 * @throws ArithmeticException Si el divisor es cero
 */
public int dividir(int dividendo, int divisor) {
    if (divisor == 0) {
        throw new ArithmeticException("División por cero");
    }
    return dividendo / divisor;
}
```
### Clases
```java
/**
 * Clase que representa una calculadora avanzada para operaciones matemáticas.
 * * Este componente mejora la precisión utilizando la constante {@link Math#PI} 
 * para los cálculos circulares. Si el valor es {@code null}, la clase lanzará 
 * un error.
 *
 * @author Germán Gascón Grau <g.gascongrau@edu.gva.es>
 * @version 2.0
 * @since 1.0
 * @see Math
 * @see Math#PI
 * @deprecated Esta clase ha quedado obsoleta por problemas de rendimiento. 
 * Usar {@link CalculadoraCientifica} en su lugar.
 */
@Deprecated
public class CalculadoraAvanzada {

    /**
     * Límite máximo de operaciones permitidas en memoria: {@value}.
     */
    public static final int MAX_OPERACIONES = 1000;

    /**
     * Calcula el área de un círculo.
     * * Método obsoleto para el cálculo del área. 
     *
     * @param radio El radio del círculo a calcular
     * @return Área calculada en formato decimal
     * @throws IllegalArgumentException Si el radio es un número negativo
     * @deprecated Usar {@link #calcularAreaPrecisa(double)} en su lugar.
     */
    @Deprecated
    public double calcularArea(double radio) {
        if (radio < 0) {
            throw new IllegalArgumentException("El radio no puede ser negativo");
        }
        return Math.PI * radio * radio;
    }
}
```

## Gradle task

```kotlin
import org.gardle.external.javadoc.JavadocMemberLevel
import org.gradle.external.javadoc.StandardJavadocDocletOptions

{ ... } // Código no relacionado

tasks.javadoc {
	description = "Genera la documentación JavaDoc del proyecto"
	group = "documentation"
	destinationDir = layout.buildDirectory.dir("docs/javadoc").get().asFile
	title = "Documentación API del proyecto"
	options.encoding = "UTF-8"
	options.memberLevel = JavadocMemberLevel.PROTECTED
	(options as StandardJavadocDocletOptions).apply {
		author(true)
		version(true)
		charSet("UTF-8")
		docEnconding("UTF-8")
	}
}
```

### Comando
`./gradlew javadoc`
### Ruta
`ruta_del_proyecto/build/docs/javadoc/index.html`

# Tema 7: Diagrama de clases
## Cardinalidad / Multiplicidad

Indica el número de elementos que participan en una relación:

- **1**: Uno y sólo uno.
	- **0..1**: Cero o uno.
- **N..M**: Desde N hasta M.
- 0.. * : Cero o varios.
- 1.. * : Uno o varios (al menos uno).

## Tipos de Relaciones entre Clases (Símbolos Clave)

1. **Asociación:** Línea continua simple. Representa dependencia semántica (ej. Piloto conduce Nave). Puede ser unidireccional (con flecha) o bidireccional.
2. **Herencia** Línea continua con **flecha de triángulo vacío** apuntando a la clase base/padre.
3. **Agregación:** Línea con **rombo vacío** en la clase contenedora. Relación "todo-parte" donde las partes **pueden existir independientemente** del contenedor (ej. Equipo y Jugadores).
4. **Composición:** Línea con **rombo relleno (negro)** en la clase contenedora. Relación donde las partes **dependen totalmente** del contenedor y no pueden existir sin él (ej. Libro y Capítulos).
5. **Dependencia:** Línea **discontinua** con flecha abierta. Una clase usa temporalmente a otra (ej. uso de librerías externas).

# Tema 8: Diagrama de Casos de uso

## Comportamiento

Responde a la pregunta: _"¿Qué puede hacer el sistema desde el punto de vista del usuario?"_.

Elementos Básicos

- **Actor:** Figura de un "muñeco de palo". Entidad externa (usuario o sistema). **Representan roles, NUNCA nombres de personas concretas** (Ej: Cliente sí, Juan no).
- **Caso de Uso:** Elipse con el nombre dentro. Representa la funcionalidad o acción (Ej: "Realizar compra").
- **Sistema:** Rectángulo que engloba todos los casos de uso. Define los límites del sistema (los actores quedan fuera).

## Tipos de Relaciones en Casos de Uso

1. **Asociación:** Línea continua que conecta a un Actor con el Caso de Uso en el que participa.
2. **Inclusión (****<<include>>): Línea discontinua con flecha. Indica que un caso de uso siempre utiliza de forma obligatoriaa otro (ej. "Realizar compra" obliga a "Validar pago").
3. Extensión (<<extend>>): Línea discontinua con flecha. Indica que un caso de uso añade comportamiento de forma opcional o condicional a otro (ej. "Realizar compra" se extiende con "Aplicar descuento" solo si hay cupón).
4. eneralización (Herencia): Línea continua con flecha de triángulo vacío. Un actor/caso más específico hereda de uno más general (ej. Cliente hereda de Usuario).