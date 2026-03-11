### Definición
Es el framework de pruebas unitarias más renombrado de Java, consiste en verificar y reproducir funcionalidades esperadas de fragmentos de código, i.e métodos o unidades.

- Automatiza pruebas
- Framework muy probado, motivo por el cual es un estándar

El test realizado se adhiere a la versión: `JUnit 6`.

```kotlin
dependencies {
	testImplementation(platform("org.junit:junit-bom:6.0.2"))
	testImplementation("org.junit.jupiter:junit-jupiter")
	testRuntimeOnly("org.junit.platform:junit-platform-launcher")
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

> [!info] Todos los tests, devuelven `void`

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
## First test

```java
class Player { void curar(int amount){ ... } }
class PlayerTest {
	@Test
    void curarNoSuperaMaximo() {
        Player p1 = new Player("Character", 90, 67);
        p1.curar(67);
        assertEquals(100, p1.getVida());
    }
}
```

> This test runs a class Player(name, health, attack)

### Parameterized test
Este test admite un test por elemento del array src
```java
@ParameterizedTest
@ValueSource(strings = {"racecar", "radar", "level"})
void palindromasSonReconocidas(String palabra) {
	assertTrue(esPalindroma(palabra));
}
```
