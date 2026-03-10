> Package: java.time.LocalDate
## Variables
### LocalDate
#### Constructor
LocalDate.of(YYYY, MM, DD);
#### Actual
LocalDate.now();

### LocalTime
#### Constructor
LocalTime.of(HH, MM, SS, NS);
#### Actual
LocalTime.now();

### LocalDateTime
#### Constructor
LocalDateTime.of(YYYY, MM, DD, HH, MM, SS, NS);
#### Actual
LocalDateTime.now();

## Operaciones

| Operación             | Método no estático                                      |
| --------------------- | ------------------------------------------------------- |
| Agregar o restar días | LocalDate.plusDays (nDays) / LocalDate.minusDays(nDays) |
| Comparar fechas       | .isBefore(date) / .isAfter(date) / .isEqual(date)       |

## Formato
### dd/MM/yyyy
El API de Java nos permite formatear la fecha mediante una expresión regular.

```java
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;
---
public static void main(String[] args){  
    LocalDateTime nowDateTime = LocalDateTime.now(); // es un objeto
    DateTimeFormatter f = DateTimeFormatter.ofPattern("dd/MM/yyyy");  
    
    System.out.println(nowDateTime.format(f)); // 10/3/2026
}
```
	- java.time.format.DateTimeFormatter
	- DateTimeFormatter.ofPatern("regex")
	- date.format(pattern)
	- pattern puede ser también = "dd/MM/yyyy HH:mm:ss"

### Establecer zona horaria (recomendado)
Por defecto, LocalDateTime, etc. establecen como zona horaria la del sistema. Es recomendable no hacerlo.

```java
LocalDateTime nowDateTime = LocalDateTime.now(ZoneId.of("Europe/Madrid"));
```
	- LocalDateTime(ZoneId.of("zone"))
	- ZoneId.getAvailableZoneIds() devuelve todas los zonas horarias

### ZoneDateTime
Podemos asignar una zona, fecha y hora a un objeto, para después formatearlo e imprimirlo.

```java
import java.time.ZoneId;  
import java.time.ZonedDateTime;  
import java.time.format.DateTimeFormatter;
---
public static void main(String[] args){
    ZonedDateTime converted=ZonedDateTime.now(ZoneId.of("Europe/Madrid"));
    DateTimeFormatter formatter = DateTimeFormatter.ofPattern(
    "yyyy/MM/ddHH:mm:ss");
    System.out.println(converted.format(formatter));
}
```

### Representar el mismo tiempo en dos zonas distintas (husos horarios)
Podemos utilizar los métodos y la clase ZoneDateTime para representar el mismo tiempo en dos zonas horarias distintas. Eso es útil si queremos dar la opción de ver más de una zona horaria.

```java
import java.time.ZoneId;
import java.time.ZonedDateTime;
import java.time.format.DateTimeFormatter;
---
public static void main(String[] args) {
	ZonedDateTime horaMadrid = ZonedDateTime.now(ZoneId.of("Europe/Madrid"));
    ZonedDateTime horaLondres = horaLondres.withZoneSameInstant(ZoneId.of("Europe/London"));
	DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy/MM/dd HH:mm:ss");
	System.out.println(
		"Hora en Londres: " + horaLondres.format(formatter));
    System.out.println(
	    "Hora en Madrid:  " + horaMadrid.format(formatter));
}
```
