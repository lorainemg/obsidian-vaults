# Análisis Multivariado
Creado: 2022-05-15 23:49
Tags: #sql, #data-science, #eda, #code, #sql, #multivariate-analysis
Topic: [[EDA]]

----

### Análisis Numérico-Numérico
----
#### Coeficiente de Correlación de Pearson
```mysql
SELECT (avg(A*B) - (avg(A)* avg(B))) / (std(A) * std(B))
FROM Data;
```


### Análisis Ordinal-Ordinal 
---
#### Rango de correlación de Kendall
```mysql
SELECT
	sum(CASE WHEN ((D1.Arank < D2.Arank AND D1.Brank < D2.Brank)
						OR (D1.Arank > D2.Arank AND D1.Brank > D2.Brank))
					THEN 1 ELSE 0 END) as concordant -
	sum(CASE WHEN ((D1.Arank < D2.Arank AND D1.Brank > D2.Brank)
						OR (D1.Arank > D2.Arank AND D1.Brank < D2.Brank))
					THEN 0 ELSE 1 END) as discordant
	/ (count(*) * (count(*) - 1)
FROM Data AS D1, Data AS D2;
```
#### Spearman’s Rho
```mysql
SELECT 1 - (6 * sum(pow(Arank - Brank, 2))) /
					 (pow(count(*), 3) - count(*))
FROM Data;
```


### Análisis Categórico-Numérico
---
#### One-Way ANOVA
```mysql
WITH group_means AS
	SELECT fertilizer, avg(height) as group-mean
	FROM Growth
	GROUP BY fertilizer
SELECT between_groups / within_groups
FROM (SELECT sum(pow(group_mean - overall_mean, 2)) *
						(size * (num_groups - 1)) AS between_groups
			FROM (SELECT count(*) AS size FROM Growth),
					 (SELECT count(DISTINCT fertilizer) as num_groups
					  FROM Growth),
						group_means) AS temp1,
		(SELECT sum(pow(height - group_mean, 2)) /
						(num_groups * (size - 1)) AS within_groups
		 FROM Growth, group_means
		 WHERE Growth.fertilizer = group_means.fertilizer)
		 AS temp2;
```

## Referencias
[[Cómo se Aplica EDA]]