# Técnicas de Limpieza de Datos
Creado: 2022-05-15 23:10
Tags: #sql, #data-science, #data-cleaning 
Topic: [[Limpieza de Datos]]

----

Existen distintos tipos de técnicas de limpieza de datos en dependencia al dominio donde están definidos estos datos.

### Técnicas de Limpieza  para datos enumerados (finitos):
Para tipos de datos enumerados finitos, una simple prueba de pertenencia a este conjunto es suficiente.

### Técnicas de Limpieza para dominios basados en patrones:
Una prueba puede descartar valores que no cumplen el patrón. Sin embargo, cuando un valor falla el patrón esperado, puede ser el caso de un formato malo; tales valores deben ser reescritos, no ignorados, o eliminados.

### Técnias de Limpieza para dominios abiertos:
En este dominio lo que es un valor 'malo' o 'equivocado' no es claro. Un análisis profundo de los valores existentes e información del dominio tiene que ser combinado para inferir el rango de los valores posibles y/o probables, e incluso con este conocimiento puede no ser suficiente para discernir entre valores 'buenos' o 'malos' en muchos casos.

## Referencias
[[Tareas de la Limpieza de Datos]]