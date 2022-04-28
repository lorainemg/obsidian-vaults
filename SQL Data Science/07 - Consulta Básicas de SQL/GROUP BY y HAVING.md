# GROUP BY y HAVING
Creado: 2022-04-27 22:16
Tags: #sql, #data-science, #code, #query 
Topic: [[Consulta Básica de SQL]]

----

`GROUP BY` se usa para dividir los datos de una tabla por un atributo determinado. En el siguiente ejemplo, se seleccionan de la tabla *ny-flights* las filas donde origin tiene el valor *'JFK'*, estas filas son pasadas al `GROUP BY`, en este caso se dividirán en grupos de filas, cada grupo conteniendo todas las filas con el mismo atributo `carrier`, y una vez esta hecha la partición, se aplica `count(*)` **para cada grupo**.
```sql
SELECT carrier, count(*)
FROM ny-flights
WHERE origin = 'JFK'
GROUP BY carrier;
```

Por otro lado, `HAVING` reduce los grupos formados por el `GROUP BY`, de la misma forma que `WHERE` los reduce en la cláusula `FROM`. Un ejemplo usando la tabla *ny-flights*:
```sql
SELECT dest, count(*)
FROM ny-flights
GROUP BY dest
HAVING count(*) > 10;
```

## Referencias
[[SELECT]]