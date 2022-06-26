# Clausura Transitiva
Creado: 2022-06-26 11:27
Tags: #sql, #data-science, #json-xml, #transitive-closure, #code
Topic: [[Tratando con JSON y XML]]

----

La clausura transitiva de un grafo puede ser realizada de la siguiente forma:
```mysql
WITH RECURSIVE
transitive_closure(source, dest, distance, path_string) AS
(SELECT source, dest, 1 AS distance,
				source || ’.’ || dest || ’.’ AS path_string
	FROM edges
UNION ALL
	SELECT tc.source, e.dest, tc.distance + 1,
				 tc.path_string || e.dest || ’.’ AS path_string
	FROM transitive_closure AS TC JOIN edges AS E
				ON TC.dest = E.source
WHERE TC.path_string NOT LIKE ’%’ || E.source || ’.%’)
SELECT * FROM transitive_closure
ORDER BY source, dest, distance;
```

## Referencias
[[Datos en Forma de Grafos]]