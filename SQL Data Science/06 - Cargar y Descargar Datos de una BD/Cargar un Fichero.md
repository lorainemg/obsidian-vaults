# Cargar un Fichero
Creado: 2022-04-23 23:23
Tags: #sql, #data-science, #load, #mysql, #postgres, #code 
Topic: [[Cargar y Descargar Datos de una BD]]

----

### MySQL
Para cargar un fichero en MySQL (donde `TERMINATED BY` especifica el caracter que separa un campo del otro (por defecto es tab), `ENCLOSED BY` indica como los valores de tipo string están puestos y `ESCAPED BY` es usado para indicar como manejar los caracteres especiales, usualmente indicados por un '\') se hace de la siguiente forma:
```mysql
LOAD DATA INFILE filename
INTO TABLE table
[FIELDS [TERMINATED BY string]
[ENCLOSED BY char]
[ESCAPED BY char]]
```

### Postgres
Para cargar un fichero en Postgres usaríamos un comando como el siguiente:
```sql
COPY ny-flights FROM '~/DATA-MNGMNT/DBS/ny-flights.csv'
	DELIMITER ',' WITH FORMAT CSV HEADER;
```

## Referencias
[[Tratar con Bases de Datos]]