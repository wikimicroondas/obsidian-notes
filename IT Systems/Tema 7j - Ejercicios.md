# Unit 7 – Learning Assessment 4

## 1. Bash: print "OK" if variable x equals 42 (integer comparison).

- a. `if (x == 42) echo OK`
- b. `if [ "$x" -eq 42 ]; then echo "OK"; fi`
- c. `if [[ $x =*= 42 ]]; then echo OK; fi`
- d. `None is correct`

**Respuesta: b**

---

## 2. Bash: test if file stored in $f is readable and regular file.

- a. `if [ -f "$f" ] && [ -r "$f" ]; then echo "readable"; fi`
- b. `None is correct`
- c. `if [ -file $f -and -read $f ]; then echo readable; fi`
- d. `if fileReadable($f) then echo readable`

**Respuesta: a**

---

## 3. Bash: string comparison — print YES if variable s equals literal 'admin'.

- a. `if (s == 'admin') echo YES`
- b. `None is correct`
- c. `if [ $s -eq admin ]; then echo YES; fi`
- d. `if [ "$s" = "admin" ]; then echo YES; fi`

**Respuesta: d**

---

## 4. Bash: print "NEGATIVE" if n is less than 0 (using arithmetic context).

- a. `None is correct`
- b. `if (( n < 0 )); then echo NEGATIVE; fi`
- c. `if [ n < 0 ]; then echo NEGATIVE; fi`
- d. `if (n lt 0) { echo NEGATIVE }`

**Respuesta: b**

---

## 5. Bash: check exit status of previous command and print 'success' only when it returned 0.

- a. `None is correct`
- b. `if [ $? -eq 0 ]; then echo success; fi`
- c. `if [ $? = TRUE ]; then echo success; fi`
- d. `if status(prev) == ok then echo success`

**Respuesta: b**

---

## 6. Bash: classic C-style for loop from 1 to 5 inclusive printing numbers.

- a. `None is correct`
- b. `for ((i=1;i<=5;i++)); do echo "$i"; done`
- c. `for i=1..5 do echo $i done`
- d. `foreach i (1..5) echo $i`

**Respuesta: b**

---

## 7. Bash: iterate words in the list 'red green blue' and print each.

- a. `for color in {red,green,blue} print color`
- b. `for color list(red green blue) { echo color }`
- c. `for c in red green blue; do echo "$c"; done`
- d. `None is correct`

**Respuesta: c**

---

## 8. Bash: read a file line by line stored in $FILE without mangling backslashes.

- a. `while read line from $FILE; do echo $line; done`
- b. `for line in $(cat $FILE); do echo $line; done`
- c. `while IFS= read -r line; do echo "$line"; done <"$FILE"`
- d. `None is correct`

**Respuesta: c**

---

## 9. Bash: loop 1..10 and skip even numbers using continue.

- a. `None is correct`
- b. `for i in 1..10 skip even; echo i`
- c. `for i in {1..10}; do if (( i%2==0 )); then continue; fi; echo "$i"; done`
- d. `for (i=1;i<=10;i++) if even(i) continue print i`

**Respuesta: c**

---

## 10. Bash: count down from N to 1 using while and arithmetic expansion.

- a. `while gt(N,0) { print N; N=N-1 }`
- b. `while [ N > 0 ]; do echo $N; N-- ; done`
- c. `while (( N > 0 )); do echo "$N"; N=$((N-1)); done`
- d. `None is correct`

**Respuesta: c**
