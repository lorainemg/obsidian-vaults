# SELECT
Creado: 2022-04-24 20:06
Tags: #sql, #data-science, #code, #query
Topic: [[Consulta Básica de SQL]]

----

La forma básica de utilizar el comando `SELECT` es:
```sql
SELECT result_list
FROM data_sources
WHERE condition;
```
Además, se puede usar el comando `AS` para expresar subconsultas. Por ejemplo:
```sql
SELECT origin
FROM (SELECT id, distance, origin
	FROM ny-flights
	WHERE year = 2013 and month = 11 and
	day = 10 and dest = "JFK") AS T
WHERE distance > 1000;
```

## Referencias