# Técnicas de Limpieza de Datos
Creado: 2022-04-29 22:20
Tags: #sql, #data-science, #eda, #data-cleaning
Topic: [[Limpieza de Datos]]

----

Existen diferentes técnicas de limpieza de acuerdo al tipo de datos que se quiere analizar.

### Datos Enumerados
Para los datos enumerados finitos, la limpieza de los datos es suficiente realizar una simple prueba de pertenenecia.

### Dominios Basados en Patrones
Una prueba puede descartar valores que no cumplen el patrón. Sin embargo, cuando un valor falla el patrón esperado, puede ser el caso de un formato malo; tales valores deben ser reescritos, no ignorados, o eliminados.

### Dominios Abiertos
Los dominios abiertos abarcan casi todas las medidas. En este dominio lo que es un valor 'malo' o 'equivocado' no es claro. Un análisis profundo de los valores existentes e información del dominio tiene que ser combinado para inferir el rango de los valores posibles y/o probables, e incluso con este conocimiento puede no ser suficiente para discernir entre valores 'buenos' o 'malos' en muchos casos.

## Referencias
[[Tareas de la Limpieza de Datos]]