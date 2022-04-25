# Seleccionar Filas y Columnas
Creado: 2022-04-24 20:13
Tags: #sql, #data-science, #code, #query 
Topic: [[Consulta Básica de SQL]]

----

Existen diferentes formas de nombrar las columnas. Estas pueden ser referidas de forma enumerada: `SELECT 1, 3 FROM foo`; y su nombre también puede ser redefinido: 
```sql
SELECT dest AS destination, flight AS flight-number FROM ny-flights;
```

Para seleccionar todas las columnas, se usa el caracter `*`. Ejemplo:
```sql
SELECT * FROM ny-flights WHERE dest="JFK" and arr_time < 800;
```

Además, se pueden querer seleccionar filas distintas (cuyo valor sea único en la consulta, es decir, que no se repita). Ejemplo:
```sql
SELECT DISTINCT carrier, origin FROM ny-flights;
```

## Referencias
[[SELECT]]