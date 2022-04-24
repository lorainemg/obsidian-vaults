# Datos en Forma de Grafos
Creado: 2022-04-23 23:09
Tags: #sql, #data-science, #data, #code
Topic: [[Otros Tipos de Datos]]

----

Para representar los datos en formas de grafos en datasets SQL se crean dos tablas, una tabla nodo, y una tabla arista, que tiene dos llaves foráneas de tipo nodo, origen y destino. Un ejemplo genérico en SQL:
```sql
CREATE TABLE nodes (
	id INTEGER PRIMARY KEY,
	name character(16) NOT NULL,
	feature1 datatype1,
	feature2 datatype2,
	...);
CREATE TABLE edges (
	a INTEGER NOT NULL REFERENCES nodes(id)
	ON UPDATE CASCADE ON DELETE CASCADE,
	b INTEGER NOT NULL REFERENCES nodes(id)
	ON UPDATE CASCADE ON DELETE CASCADE,
	label character(256),
	PRIMARY KEY (a, b));
```

Otra opción es representar los grafos mediante su matriz de adyacencia.

## Referencias
[[Clasificación de Datasets]]