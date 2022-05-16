# Calcular Propiedades de Atributos Catégoricos
Creado: 2022-05-15 23:44
Tags: #sql, #data-science, #eda, #categorical-data, #code
Topic: [[EDA]]

----

### Histrogramas
```sql
SELECT A, count(*)
FROM R
GROUP BY A;
```

### Entropía
```sql
SELECT sum(Pa * log(Pa))
FROM (SELECT A, sum(1.0 /total) as Pa
	FROM Data, (SELECT count(*) as total FROM Data) AS T
	GROUP BY A);
```

### Probabilidad y Probalidad Conjunta
```sql
WITH ProbA AS
	(SELECT A, sum(1.0/total) as PrA
	 FROM Data, (SELECT count(*) as total FROM Data) as T
	 GROUP BY A),
ProbB AS
	(SELECT B, sum(1.0/total) as PrB
	 FROM Data, (SELECT count(*) as total FROM Data) as T
	 GROUP BY B),
ProbAB AS
	(SELECT A, B, sum(1.0/total) as PrAB
	 FROM Data, (SELECT count(*) as total FROM Data) as T
 	 GROUP BY A, B)
SELECT sum(PrAB - (PrA * PrB))
FROM (SELECT A, B, PrA, PrB, PrAB
			FROM ProbA, ProbB, ProbAB
			WHERE ProbA.A = ProbAB.A and ProbB.B = ProbAB.B)
			AS Probabilities;
```

### Información Mutua Puntual
```sql
SELECT log(sum (PrAB / (PrA * PrB)))
FROM Probabilities;
```

## Referencias
[[Cómo se Aplica EDA]]