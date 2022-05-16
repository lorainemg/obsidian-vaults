# Calcular Propiedades de Atributos Numéricos
Creado: 2022-05-15 23:33
Tags: #sql, #data-science, #eda, #code, #cardinality, #numerical-data 
Topic: [[EDA]]

----
Ejemplo de comando en SQL para calcular propiedades de atributos numéricos:
```SQL
SELECT count(Attr) as number-values,
	count(distinct Attr) as cardinality,
	min(Attr) as minimum, max(Attr) as maximum,
	max(Attr) - min(Attr) as range,
	avg(Attr) as mean,
	stddev(Attr) as standard-deviation,
	variance(Attr) as var
FROM Data;
```

## Referencias
[[Cómo se Aplica EDA]]
[[Actividades Realizadas en EDA]]