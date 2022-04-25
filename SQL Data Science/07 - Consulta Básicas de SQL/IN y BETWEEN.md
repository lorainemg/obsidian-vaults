# IN y BETWEEN
Creado: 2022-04-24 20:10
Tags: #sql, #data-science, #code, #query 
Topic: [[Consulta Básica de SQL]]

----

El comando `IN`, se utiliza para comprobar si un valor determinado pertenece a una lista de valores. Ejemplo:
```sql
SELECT *
FROM ny-flights
WHERE dest IN ("JFK", "LGA", "EWR");
```

Por otro lado, el comando `BETWEEN`, cuando un valor está en un rango de valores (numéricos). Ejemplo:
```sql
SELECT origin
FROM ny-flights
WHERE arr_time BETWEEN 400 and 500;
```

## Referencias
[[SELECT]]