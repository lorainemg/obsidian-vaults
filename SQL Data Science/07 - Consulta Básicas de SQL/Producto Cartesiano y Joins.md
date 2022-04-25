# Producto Cartesiano y Joins
Creado: 2022-04-24 20:19
Tags: #sql, #data-science, #code, #join
Topic: [[Consulta Básica de SQL]]

----

El producto cartesiano entre dos tablas es el comportamiento por defecto al usar la cláusula:  `FROM (SELECT * FROM T, S);`. En el ejemplo anterior, se forma un producto cartesiano de las dos tablas T y R con el esquema, el cual es una concatenación de los esquemas de T y R (es decir, todos los atributos de T seguidos de los atributos de R); las tuplas para esta tabla son creadas combinando las tuplas en T y en R

Por otro lado, los *Joins* unen 2 tablas de acuerdo a un atributo común. Se puede hacer de 2 formas:
```sql
FROM Table1, Table2 WHERE attribute1 = attribute2
```
Y:
```SQL
FROM Table1 JOIN Table2 on (attribute1 = attribute2)
```

## Referencias
