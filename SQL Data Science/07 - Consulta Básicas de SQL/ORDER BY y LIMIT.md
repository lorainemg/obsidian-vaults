# ORDER BY y LIMIT
Creado: 2022-04-27 22:22
Tags: #sql, #data-science, #code, #query 
Topic: [[Consulta Básica de SQL]]

----

`ORDEN BY`  imponen un orden al resultado de una consulta, es ejecutada después de las cláusulas `WHERE` o `GROUP BY`. Un ejemplo con la tabla *ny-flights*:
```sql
SELECT dest, count(*)
FROM ny-flights
GROUP BY dest
ORDER BY count(*) desc;
```

Por otro lado, `LIMIT` se usa para coger los ***n*** primeros resultados de una consulta. `OFFSET` para saltarse los ***n*** primeros resultados. Por ejemplo, en la siguiente consulta se eligen los 10 mejores destinos después de los 20 mejores.
```mysql
SELECT dest, count(*)
FROM ny-flights
GROUP BY dest
ORDER BY count(*) desc;
LIMIT 10 OFFSET 20;
```

## Referencias
[[SELECT]]