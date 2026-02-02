### Solucionario
## 1. Comprueba si un número es positivo o negativo

```bash
#!/usr/bin/env bash
read -p "Enter a number." n
# your if/then/else here
if [ "$n" -gt 0 ]; then
echo "positive"
elif [ "$n" -lt 0 ]; then
echo "negative"
else
echo "zero"
fi
```
	- if [] - Es la sintaxis de bash
	- "$n" - Es la ranura de la variable n
	- -gt - > - Greater Than
	- ; then - {}
	- fi - Fin del programa
## 2 . Compara dos números (más grande o más pequeño)

```bash
#!/usr/bin/env bash
read -p "First integer." a
read -p "Second integer." b
# your if/then/else here
if [ "$a" -gt "$b" ]; then
echo "$a is greater than $b"
elif [ "$a" -lt "$b" ]; then
echo "$a is less than $b"
else
echo "$a is equal to $b"
fi
```

## 3. Comprueba si un archivo existe

```bash
#!/usr/bin/env bash
read -p "Enter a file path:" path
# your if/then/else here
if [ -f "$path" ]; then
echo "File exists"
else
echo "File does not exist"
fi
```
	- -f - File

## 4. Comprueba si un directorio existe, si no, créalo

```bash
 #!/usr/bin/env bash
 read -p "Directory name:" dir
 if [ -d "$dir" ]; then
 echo "Already exists"
 else
 mkdr -p "$dir"
 echo "Created"
 fi
```
	- -d - Directory
	- -p - Parents

## 5. Comprueba si un String está vacío

```bash
 #!/usr/bin/env bash
 read -p "Type something (or press Enter):" s
 # your if/then/else here
 if [ -z "$s" ]: then
 echo "Empty"
 else
 echo "Not empty"
 fi
```
	- -z - has Zero length

## 6. Comprueba si el usuario es root

```bash
#!/usr/bin/env bash
if [ "$EUID" -eq 0 ]; then
echo "You are root"
else
echo "You are not root"
fi
```
	- "$EUID" - Comprobar el usuario	
	- -u - Usuario
	- -eq - Equals

## 7. Validación de

```bash
#!/usr/bin/env bash
# Usage: ./script.sh <filename>
# your if/then/else here
if [ "$#" -ne 0 ]: then
echo "Usage: $0 <filename>"
exit 1
else
echo "Argument OK: $1"
fi
```
	- $# - Los ejecutables .sh tienen argumentos que se numeran con $n, si
	-      queremos 
	- -ne - Not Equal
	- exit 1 - Salida mala del programa

## 8. Comprueba el éxito de un comando

```bash
#!/usr/bin/env bash
# Try 
if ls /tmp > dev/null 2>&1; then
echo "OK"
else
echo "FAIL"
fi
```

## 9. Clasificador de grado simple

```bash
#!/usr/bin/env bash
read -p "Grade (0-100):" g
# your if/then/else here
if [ "$g" -gr 50 || "$g" -eq 50 ]; then
echo "PASS"
else
echo "FAIL"
fi
```

## 10. Tipo de día

```bash
#!/usr/bin/env bash
read -p "Day(Mon/Tue/.../Sun):" day
# your if/then/else here
if [ "$day" = "Sat" ] || [ "$day" = "Mon" ]
```