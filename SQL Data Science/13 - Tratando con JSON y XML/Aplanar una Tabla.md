# Aplanar una Tabla
Creado: 2022-06-26 11:21
Tags: #sql, #data-science , #json-xml, #flatten, #postgres, #code 
Topic: [[Tratando con JSON y XML]]

----
Para aplanar una tabla en Postgres se usa la función `xmltable` que tiene el formato siguiente:
```postgresql
xmltable(
	row_expression PASSING document_expression
		COLUMNS name { type [PATH column_expression]
												[DEFAULT default_expression]
												[NOT NULL | NULL]
												| FOR ORDINALITY })
```

## Referencias