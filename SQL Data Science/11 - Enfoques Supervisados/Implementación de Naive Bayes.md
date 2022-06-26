# Implementación de Naive Bayes
Creado: 2022-06-26 10:23
Tags: #sql, #data-science, #supervised, #naive-bayes, #code 
Topic: [[Enfoques Supervisados]]

----

Implementación de Naive Bayes en SQL:
- Para cada clase, calcular la probabilidad a priori:
```sql
CREATE TABLE classPriors AS
SELECT class, sum(1.0 / total) as classProb,
count(*) as rawclass
FROM training-data,
(SELECT count(*) AS total FROM training-data) AS T
GROUP BY class;
```
- Para cada atributo predictor $A_i$, clase $C_j$, calculamos la probabilidad condicional $P(C_j | A_i = a_i)$:
```sql
CREATE TABLE AiPriors
SELECT Ai, class, sum (1.0 / rawclass) AS classProb
FROM training-data, classPriors
WHERE training-data.class = Priors.class
GROUP by Ai, class;
```
- Se calcula la probabilidad conjunta (de todos los atributos usando la fórmula $P(C_i | r) = P(C_i|a_1, ..., a_n) = \prod_j P(C_i | A_j = a_j)P(c_i)$. Este cálculo es realizado para cada clase (en el código * es usado como un shortcut, es necesario poner todos los atributos)
```sql
CREATE TABLE results as
SELECT test-data.*, classPrior.class,
	classPrior.prior * A1prior.prob * A2prior.prob ...
	as ClassProb
FROM classPriors, A1Prior, ..., AnPrior, test-data
WHERE test-data.A1 = A1Prior.value
	and classPrior.class = A1Prior.class and
	test-data.A2 = A1Prior.value
	and classPrior.class = A2Prior.class and
	...
GROUP BY test-data.*, classPrior.class;
```
- Para elegir los pasos finales, este paso es realizado en el conjunto de prueba con cada clase:
```sql
SELECT test-data.*, classPrior.class
FROM results R1
WHERE ClassProb = (SELECT max(ClassProb)
FROM results R2
WHERE R2.test-data.* = R1.test-data.*)
```

## Referencias