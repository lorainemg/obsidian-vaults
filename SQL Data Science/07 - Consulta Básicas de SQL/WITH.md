# WITH
Creado: 2022-04-27 22:28
Tags: #sql, #data-science, #code, #query 
Topic: [[Consulta Básica de SQL]]

----

El comando `WITH` es otra forma de hacer subconsultas. Por ejemplo:
```mysql
WITH T AS
	(SELECT id, distance, origin
	FROM ny-flights
	WHERE year = 2013 and month = 11 and
		day = 10 and dest = "JFK")
SELECT origin
FROM T
WHERE distance > 1000;
```

## Referencias
[[SELECT]]