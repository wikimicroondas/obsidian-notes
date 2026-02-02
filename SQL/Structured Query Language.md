# Apuntes
#SQL #PostgreSQL

### Orden de ejecución

* `FROM / JOIN / USING`. Invita a grupos de datos a unirse a la **Query**.
- `WHERE`.  Actúa como un filtro y descarta registros innecesarios.
* `GROUP BY`. Agrupa los registros por un dato.
* `SELECT`. Invita a la tabla principal, ya filtrada.
* `ORDER BY`. Modifica la representación de los datos.

_e.g._
```PostgreSQL
SELECT c.region, AVG(e.inflation_rate) AS average_inflation
FROM countries AS c
INNER JOIN economies AS e
USING (code)
WHERE e.year > 2015
GROUP BY c.region
ORDER BY average_inflation DESC;
```
