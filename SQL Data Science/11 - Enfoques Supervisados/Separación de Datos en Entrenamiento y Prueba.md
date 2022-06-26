# Separación de Datos en Entrenamiento y Prueba
Creado: 2022-06-26 10:20
Tags: #sql, #data-science, #supervised, #code 
Topic: [[Enfoques Supervisados]]

----

El siguiente código de SQL separa los datos en conjuntos y entrenamiento:
```sql
CREATE TABLE new-data
as SELECT *, random() as split
FROM Data;

CREATE TABLE training-data
as SELECT *
FROM new-data
WHERE split >= .1;

CREATE TABLE testing-data
as SELECT *
FROM new-data
WHERE split < .1;
```

## Referencias