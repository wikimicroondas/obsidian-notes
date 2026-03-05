### Renombrar la rama principal
`git branch -M main`

### Crear y cambiar de rama
`git checkout -b feature/balanceo`

### Volver y reincorporar una rama
`git checkout main`
`git merge feature/balanceo`

### Taggear una versión
`git tag -a v0.1.0 -m "Primera versión jugable"`

### Establecer el repositorio remoto
`git remote add origin [url]`

### Cambiar el repositorio remoto
`git remote set-url origin [url]`

### Revertir un commit con otro
`git revert HEAD`

### Borrar el último commit (problematico)
`git reset --hard HEAD~1`