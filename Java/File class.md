> Package: java.io.File
> Exceptions: IOException

To deal with files, Java creates objects that points a path. These can be actual archives or directories.

# Base classes
#### Base flux
`Crear > Abrir > Cerrar`
Otherwise changes won't be reflected
## File cycle
### File
```java
File f = new File("path");

/** -- Methods --*/

.createNewFile();
.mkdir();
.renameTo();
.get Path | AbsolutePath | Name ();

.list();
.list("n.txt", Filter f);
```
#### File class
To invoke a File class is optional to work with files
### FileReader
```java
File f = new File("/");
FileReader fr = new FileReader(File f); | FileReader("path");

/** -- Methods --*/
.read(); // deprecated

.read(char[] cbuf); // Reads an array of characters
.close();
```

### FileWriter
```java
File f = new File("/");
FileWriter fw = new FileWriter(File f); | FileWriter("path");

/** -- Methods -- */
.write(char c); // deprecated

.write(char[] cbuf);
.write(char[] cbuf, int off, int len);
/** cbuff = {'a', 'b', 'c'}
  * int offset =   ^
  * int length = --> Inside of the offset
  */

.write(String s, int off, int len);
.close();
```

# Buffer classes
Using base classes is not recommended because they do not manage operations efficiently. Every action creates a query to the physical disk, causing major functionality issues dealing with larger files.

## BufferedReader
```java
BufferedReader br = new BufferedReader(new FileReader("file.txt"));

/** -- Methods -- */
.readLine(); // One line only
.close();
```

## BufferedWriter
```java
BufferedWriter bw = new BufferedWriter(new FileWriter("file.txt"));

/** -- Methods -- */
.newLine();       // Writes an empty line
.write(String s); // Writes a String
.close();
```

## PrintWriter
In a real case scenario, using `BufferedWriter` can cause boilerplate code. Caused by lack of methods that make coding agile. This issue is solved by PrintWriter's methods
### e.g
#### BufferedWriter
```java
public static void main(String[] args) {
    String nombre = "Ana";
    int edad = 20;
    double nota = 8.5;

    try (BufferedWriter bw = new BufferedWriter(new
		    FileWriter("datos_bw.txt"))) {
		    
        bw.write("Nombre: " + nombre);
        bw.newLine(); // Manual enter
            
        // Parsing manually each type of data
        bw.write("Edad: " + String.valueOf(edad)); 
        bw.newLine();
            
        bw.write("Nota media: " + String.valueOf(nota));
        bw.newLine();

        } catch (IOException e) {
            e.printStackTrace();
        }
    }
```
#### PrintWriter
```java
public static void main(String[] args) {
    String nombre = "Ana";
    int edad = 20;
    double nota = 8.5;

    try (PrintWriter pw = new PrintWriter(new
	    FileWriter("datos_pw.txt"))) {
            
        pw.println("Nombre: " + nombre);
        pw.println("Edad: " + edad); // Does .ln directly
        pw.println("Nota media: " + nota); // No need to parse

    } catch (IOException e) {
        e.printStackTrace();
    }
}
```
### Class
```java
PrintWriter pw = new PrintWriter(
				 new BufferedWriter(
				 new FileWriter));
/** -- Methods -- */
.print(String s); // Writes a String
.println(any);    // Writes any kind of data type with a line break
```
The reason why the constructor looks like that it's because by default Java doesn't add a Buffer to our input, so, not wrapping it this way will cause performance issues.