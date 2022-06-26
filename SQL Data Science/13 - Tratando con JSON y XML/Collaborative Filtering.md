# Collaborative Filtering
Creado: 2022-06-26 11:31
Tags: #data-science, #sql, #json-xml, #collaborative-filtering, #code
Topic: [[Tratando con JSON y XML]]

----

Para escribir *Collaborative Filtering* se puede escribir siguiente código:
```mysql
WITH similar_items(itemid, distance) AS
	SELECT D2.itemid, sum(D1.rating * D2.rating) /
					  (sqrt(sum(D1.rating))*sqrt(sum(D2.ratings))
	FROM Data D1, Data D2
	WHERE D1.itemid = ’i’ and D1.itemid <> D2.itemid
	GROUP BY D2.itemid
SELECT itemid
FROM similar_items
WHERE distance = (SELECT max(distance)
					FROM similar_items);
```

## Referencias