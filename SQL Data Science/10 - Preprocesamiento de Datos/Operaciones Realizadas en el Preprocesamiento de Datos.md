# Operaciones Realizadas en el Preprocesamiento de Datos
Creado: 2022-06-05 22:18
Tags: #data-science, #sql, #eda, #data-preprocessing, #code 
Topic: [[Preprocesamiento de Datos]]

----

Las operaciones típicas realizadas en esta etapa son:
- **Agregación**: esto consiste en combinar dos o más registros de datos en uno. Esto es especialmente común cuando los datos pueden ser vistos a diferentes niveles de granularidad o detalle. Los datos agregados tienen menos detalles pero tienden a tener menor variabilidad, y los patrones generales pueden ser más claros. Es usualmente implementado usando el operador GROUP BY en SQL.
- **Muestreo**: elegir un subconjunto de datos ('muestra') para trabajar. Esto hace la computación menos costosa, así que es común muestrear cuando queremos realizar análisis complejos sobre datasets grandes, o cuando intentamos distintos análsis tentativos de los mismos datos. Una muestra elegida de forma aleatoria se espera que sea representativa de todo el dataset, por lo tanto puede ayudar a establecer las propiedades del dataset.
    En Postgres se realiza de la siguiente manera: 
	```sql
	FROM table_name TABLESAMPLE sampling_method (percent)
	```
	Y en MySQL: 
	```mysql
	SELECT * FROM Table_Name ORDER BY random() LIMIT n;
	```
- **Discretización**: esto es una transformación que cambia los valores numéricos continuos a ordinales. Esta es una transformación muy común en las tareas de clasificación. En SQL puede ser logrado, pero requiere de varios pasos:
	```mysql
	ALTER TABLE People ADD ATTRIBUTE height-category varchar(6);
	UPDATE People
	SET height-category = CASE WHEN height > 5.8 THEN 'low'
							   WHEN height > 5.2 THEN 'medium'
							   ELSE 'low' END;
	```
- **Binarización**: es una variación de la discretización, toma un atributo numérico continuo y lo transforma en una atributo binario (o varios atributos binarios)
- **Reducción de Dimensiones**: en caso de que algunos atributos sean redundantes o innecesarios y no sean útiles en predecir la salida, puede ser necesario deshacerse de los atributos innecesarios. La razón es que, para muchos algoritmos, más atributos significan más parámetros para considerar, y esto implica más trabajo que hacer. En el peor escenario, los atributos inútiles pueden confundir al algoritmo.
- **Creación de Características**: cuando todos los atributos juntos combinados no tienen suficiente información para predecir la salida, puede ser posible que queramos crear nuevos atributos adicionales combinando atributos existentes. Esto se realiza con la esperanza de que los nuevos atributos nos permitirán predecir la salida haciendo explícita algunas información que era implícita en los atributos.

## Referencias
[[Tareas del Preprocesamiento de Datos]]