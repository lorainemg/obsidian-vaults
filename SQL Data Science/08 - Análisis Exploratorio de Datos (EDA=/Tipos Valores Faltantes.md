# Tipos de Valores Faltantes
Creado: 2022-04-29 22:47
Tags: #sql, #data-science, #eda, #data-preprocessing, #missing-values
Topic: [[EDA]]

----

Se distinguen 3 tipos de valores faltantes:
- **Faltan completamente al azar** (_missing completly at random, MCR)_ o _observado a random:_ los valores están faltantes independientemente del valor subyacente de A, y cualquiera de los valores de B. En este caso, los valores faltantes pueden ser llenados porque los valores de A presentes nos dan una buena idea de la distribución de todos los valores de A, así que podemos inferir la distribución subyacente y reemplaza los valores faltantes por la media de los valores presentes o ajustada a la distribución.
- **Faltan al azar** (_missing at random, MAR_): los valores faltan independientemente del valor subyacente de A pero puede depender de otros valores de B. En este caso, los valores faltantes pueden ser llenados si podemos encontrar cuales atributos en B están relacionados con A, y la naturaleza de la relación. En tales casos, podemos aplicar un método **predictor** a los valores de los atributos relevantes en B en filas en las que A esté faltando.
- **Valores faltantes no ignorables** (_non-ignorable missing values_): los valores están perdidos independientemente de otros valores de B pero pueden depender en el valor subyacente de A. El problema con este caso es que puede no haber una manera de reemplazar los valores faltantes significativamente, ya que los valores de otros atributos no ayudan, y hay una conexión con otros valores de A, lo que siginifica que esos otros valores de A que tenemos no son una guía imparcial a los valores faltantes.

## Referencias
[[Tareas del Preprocesamiento de Datos]]