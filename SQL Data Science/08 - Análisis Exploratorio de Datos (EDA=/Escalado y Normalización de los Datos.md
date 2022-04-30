# Escalado y Normalización de los Datos
Creado: 2022-04-29 22:31
Tags: #sql, #data-science, #eda, #data-preprocessing, #code 
Topic: [[EDA]]

----

Mediante el escalado lineal, se intentan llevar todos valores a un rango de 0 a 1. Se usa la siguiente fórmula: $\dfrac{v-min}{max - min}$. Un comando en SQL para realizar dicho escalado puede ser el siguiente:
```mysql
UPDATE Dataset
SET Attr = (Attr - (SELECT mean
					FROM (SELECT avg(Attr) as mean
						  FROM Dataset) as D1)) /
					(SELECT maxa - mina
					FROM (SELECT max(Attr) as maxa, min(Attr) as mina
						  FROM Dataset) as D2 ) ;
```

Otra operación similar a realizar durante el preprocesamiento de los datos es la normalización de los mismos mediante la fórmula: $Z(v) = \dfrac{x - \mu}{stdev}$. Un comando en SQL para realizar dicha fórmula puede ser:
```mysql
UPDATE Data
SET Attr = (Attr - (SELECT avg(Attr) FROM Data)) /
				(SELECT std(Attr) FROM Data);
```

## Referencias
[[Tareas del Preprocesamiento de Datos]]