# Medias, Moda y Medianas
Creado: 2022-05-15 23:37
Tags: #sql, #data-science, #eda, #code, #numerical-data, #mean, #mode, #median
Topic: [[EDA]]

----

### *Trimmed Mean*
*Trimmed Mean* no se ve afectado por *outliers*:
```sql
SELECT avg(A)
FROM Data, (SELECT max(A) as Amax FROM Data) AS T1,
			(SELECT min(A) as Amin FROM Data) AS T2
WHERE A < Amax and A > Amin;
```
### Media Geométrica
```sql
SELECT exp(sum(log(Attr)) / count(Attr))
FROM Data;
```
### Media Armónica
```sql
SELECT Count(Attr) / Sum(1/Attr)
FROM Data;
```

### Moda
```mysql
WITH Histogram as
	(SELECT Value as val, count(*) as freq
	FROM Data
	GROUP BY Attr)
SELECT val
FROM Histogram, (SELECT max(freq) as top FROM Histogram) AS T
WHERE freq = top;
```

### Mediana
```mysql
SELECT avg(Attr)
FROM (SELECT Attr
	FROM Data, (SELECT count(*) as size FROM Data)
	ORDER BY value
	LIMIT 2 - MOD(size, 2)
	OFFSET CEIL(size / 2.0)) AS T;
```

## Referencias
[[Calcular Propiedades de Atributos Numéricos]]
[[Cómo se Aplica EDA]]