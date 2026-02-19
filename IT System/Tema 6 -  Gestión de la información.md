#Linux #Unix 

### Redundant Array of Independent Disks (RAID)
Es una técnica que combina diferentes discos en conjuntos que incrementan su capacidad, rendimiento y tolerancia. Hay muchas formas de tratar los datos en estos sistemas, pero el foco de los ejercicios son las fórmulas de optimización, según:

-  $N$  - El número de discos
-  $S$   - El almacenamiento por disco
-  $U$   - El almacenamiento requerido

## 1.  Ejercicios

Exercise 1: 
$U = 8$ TB
$S = 2$ TB
/ $N$ - Number of disks

> RAID 1:      $NS  /2$                                                                          Sol. $N = 8$
> RAID 5:     $(N-1)S$                   N >= 3                                     Sol. $N = 5$
> RAID 6:     $(N-1)S$                   N >= 3                                     Sol. $N = 5$
> RAID 01:   $NS / 2$     N(even)     N >= 4                                     Sol. $N = 8$
> RAID 10:   $NS / 2$     N(even)     N >= 4                                     Sol. $N = 8$
