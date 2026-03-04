# Gradle
### Introducción
Segunda parte de un ejercicio centrado en builders de Java.
### Descripción
En este bloque vamos a desarrollar un programa en Java que genere una conversación entre 2 LLMs. Dado que el uso de los servicios que vamos a utilizar es muy limitado de forma gratuita, la conversación se reducirá a que una IA hace una pregunta y la otra responde. Para ello vamos a utilizar Ollama y para facilitar el acceso a las IA desde Java, utilizaremos la librería LangChain4j.

<p align="center">
	<img src="https://gradle.org/assets/images/gradle-knowledge-graph-logo.png" width="100" alt="Maven logo" >
</p>
### Dependencias
- **LangChain4j**

```kotlin
implementation(platform("dev.langchain4j:langchain4j-bom:1.10.0")) implementation("dev.langchain4j:langchain4j-open-ai")
```


## Examen

- **Activar el plugin:** En el bloque `plugins` al inicio del archivo, debes incluir `id("application")`.

```kotlin
plugins {
    id("java")
    id("application")
}
```
    
- **Definir la entrada:** Hay que decirle a Gradle dónde está tu método `main`. Esto se hace añadiendo un bloque `application` que apunte a tu clase: `mainClass.set("com.alejandrocamino.tema4gradle.Main")`.

```kotlin
application {
    mainClass.set("com.alejandrocamino.tema4gradle.Main")
}
```

### Crear una tarea (básica)

Las tareas definen acciones que Gradle puede ejecutar.

- **Registro:** Se crean usando `tasks.register("nombreDeLaTarea") { ... }`.
- **Ejecución de código:** Si quieres que la tarea ejecute código propio de Gradle/Java (como imprimir un texto por consola), debes meter ese código dentro de un bloque `doLast { ... }`.
- **Dependencias:** Si necesitas que una tarea fuerce la ejecución de otras previas, utilizas `dependsOn("tarea1", "tarea2")`

```kotlin
// 3. Dependencias entre tareas
tasks.register("llmInfo") {
    group = "ollama custom"
    description = "Ejecuta todas las comprobaciones de Ollama"

    dependsOn("ollamaVersion", "ollamaPs")

    doLast {
        println("Demo finalizada")
    }
}
```

### Hacer comandos customizados (Tareas de sistema)

Si necesitas que la tarea actúe como una terminal y ejecute comandos del sistema operativo (como consultar Ollama), el tipo de tarea cambia.

- **Tipo Exec:** En lugar de un registro normal, usas `tasks.register<Exec>("nombreDeLaTarea") { ... }`.
    
- **Línea de comandos:** En estas tareas no usas `doLast`. Utilizas directamente la propiedad `commandLine`, pasando el comando y sus argumentos separados por comas. Por ejemplo: `commandLine("ollama", "--version")` o `commandLine("ollama", "ps")`.

```kotlin
// ¿Está Ollama vivo?
tasks.register<Exec>("ollamaVersion") {
    group = "ollama custom"
    description = "Muestra la versión instalada de Ollama"

    commandLine("ollama", "--version")
}
```
