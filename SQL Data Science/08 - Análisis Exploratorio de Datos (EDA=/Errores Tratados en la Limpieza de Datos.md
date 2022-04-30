# Errores Tratados en la Limpieza de Datos
Creado: 2022-04-29 22:27
Tags: #sql, #mysql, #eda, #data-cleaning 
Topic: [[EDA]]

----

Los errores básicos que la mayoría está de acuerdo con que debe ser tratado en este punto son:
- **Datos adecuados**. Para empezar, necesitamos asegurarnos que los valores son del tipo adecuado y están en el formato adecuado.
- **Valores faltantes**. En el contexto de datos tabulares, esto significa registros que tienen algunos valores de atributos faltantes, no registros faltantes. La detección puede ser complicada cuando los valores faltantes en un dataset está marcado de una manera específica en un dataset, pero el problema real es qué hacer con los registros incompletos. Las estrategias generales son ignorar (eliminar) los registros afectados (ya sea el atributo o el registro), o predecir (también llamado imputar) la absencia de valores de otros valores del mismo atributo o del valor de otros atributos.
- **Puntos atípicos**. Los puntos atípicos son valores de datos que tienen características que son muy diferentes de las características de la mayoría de los valores de datos en el mismo atributo. Detectar puntos atípicos es extremadamente complicado porque este es un concepto vago, dependiente del contexto: a menudo no está claro si un punto atípico es el resultado de un error o problema, o si es un valor legítimo extremo. Por lo tanto, el desafío con los puntos atípicos es encontrarlos. Una vez localizado, ellos pueden ser tratados como valores faltantes.
- **Datos duplicados**. A veces podemos tener un dataset donde diferentes registros en realidad son sobre la misma entidad, por lo tanto, son duplicados. En muchas situaciones, esto es considerado indeseable ya que puede sesgar los datos. Por lo tanto, detectar duplicados y deshacerse de ellos puede ser considerado una manera de mejorar la calidad de los datos.

## Referencias
[[Tareas de la Limpieza de Datos]]
[[Técnicas de Limpieza de Datos]]