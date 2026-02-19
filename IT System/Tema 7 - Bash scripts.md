### Diferencias con otros lenguajes
`bash` identifica los scripts a través de una función especial de `#` (símbolo de comentario), que es `#!`. La expresión completa con ruta queda como `#!/usr/bin/env bash`. Para cerrar un script formalmente usamos `fi` aunque hay otros métodos
## 1. Introducción
### 1. Comprueba si un número es positivo o negativo

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
### 2 . Compara dos números (más grande o más pequeño)

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

### 3. Comprueba si un archivo existe

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

### 4. Comprueba si un directorio existe, si no, créalo

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

### 5. Comprueba si un String está vacío

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

### 6. Comprueba si el usuario es root

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

### 7. Validación de

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

### 8. Comprueba el éxito de un comando

```bash
#!/usr/bin/env bash
# Try 
if ls /tmp > dev/null 2>&1; then
echo "OK"
else
echo "FAIL"
fi
```

### 9. Clasificador de grado simple

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

### 10. Tipo de día

```bash
#!/usr/bin/env bash
read -p "Day(Mon/Tue/.../Sun):" day
# your if/then/else here
if [ "$day" = "Sat" ] || [ "$day" = "Mon" ]
```

## 2. Bucles
### 1. Contar {1-10}

```bash
#!/usr/bin/env bash
for i in {1..10}; do
echo "$i"
done
```
	- {n..m} - para establecer un bucle
	- do - {
	- done - }

### 2. Cuenta atrás

```bash
#!/usr/bin/env bash
read -p "Enter a positive number N:" n

while [ "$n" -gt 0 ]; do
echo "$n"
n=$((n-1))   #((n--))
done
```
	- $ - Es la ranura después del igual, dónde luego va un valor
	- (()) - Es una expansión aritmética

### 3. Suma recursiva

```bash
#!/usr/bin/env bash
read -p "Enter N:" n
sum=0

for ((i=1; i<=n; i++)); do
sum=$((sum+i))
done

echo "SUM=$sum"
fi
```

### 4. Números pares con un límite

```bash
#!/usr/bin/env bash
read -p "Enter N:" n

i=0

while [ "$i" -le "$n" ]; do
if((i%2==0)); then
	echo "$i"
fi
i=$((i+1))   #i++
done
```
	- -le - <=

### 5. Iteración de una lista

```bash
#!/usr/bin/env bash
frutas=("apple", "banana", "cherry")

for fruta in "${frutas[@]}"; do
echo "${fruta^^}"
done
```
	- "${frutas[@]}" - expresión de iteración
	- ^^ - .toUpperCase()

### 6. ASCII Art: Triángulo

```bash
#!/usr/bin/env bash
read -p "Enter N:" n

for ((i=1; i<=n; i++)); do
	for ((j=1; j<=i; j++)); do
		echo -n "*"
	done
	echo ""
done
```
	- for/do - sintaxis común
### 7. Bucle con número secreto

```bash
#!/usr/bin/env bash
secret=7
guess=0

while [ "$guess" -ne "$secret" ]; do
    read -p "Guess the number: " guess
    
    if [ "$guess" -ne "$secret" ]; then
        echo "Try again"
    fi
done

echo "Correct! The number was $secret."
```
	- -ne - Not Equal
	- if []: then fi  |  while []; do done  |  for (()); do done

### 8. Leer un archivo línea por línea

```bash
#!/usr/bin/env bash
read -p "Enter filename: " filename

if [ ! -f "$filename" ]; then
    echo "File not found!"
    exit 1
fi

count=1

while IFS= read -r line; do
    echo "$count $line"
    ((count++))
done < "$filename"
```
	- ! - Operador de negación, niega la siguiente expresión
	- -f - Comprueba si existe ese archivo (File)
	- exit 1 - Cierra el programa
	- count=1 - Contador de líneas
	- IFS= - Internal Field Separator (Mantiene el esquema del archivo)
	- read -r - Read Raw (evita errores de interpretación)
	- < "$n" - Es la entrada al bucle en bash

### 9. Factoriales

```bash
#!/usr/bin/env bash
read -p "Enter N: " n

result=1

for ((i=1; i<=n; i++)); do
	((result*=i))
done

echo "$result"
```

### 10. Cuenta con saltos

```bash
for ((i=0; i<=20; i++)); do
	if ((i % 3 == 0)); then
		continue
	fi
	echo "$i"
done
```
