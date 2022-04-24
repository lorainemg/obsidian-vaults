# Representación de Relaciones en SQL
Creado: 2022-04-23 22:58
Tags: #sql, #data-science, #relantioships 
Topic: [[Esquema de Bases de Datos]]

----

A continuación, se muestran ejemplos de como representar los distintos tipos de relaciones binarias en SQL:

### Relación uno-a-uno
Se hacen dos tablas y se copia la llave primaria de una tabla en la otra:
```sql
CREATE TABLE PEOPLE (
	Name VARCHAR(64) PRIMARY KEY,
	...)
CREATE TABLE ADDRESS (
	street-number INT,
	street-name VARCHAR(128),
	city VARCHAR(64),
	...
	Name VARCHAR(64) FOREIGN KEY REFERENCES PEOPLE
	PRIMARY KEY (street-number, street-name, city))
```

### Relación uno-a-muchos
Se hacen dos tablas y se copia la llave primaria de la tabla que representa el lado ‘uno’:
```sql
CREATE TABLE PEOPLE (
	Name VARCHAR(64) PRIMARY KEY,
	...)
CREATE TABLE ADDRESS (
	street-number INT,
	street-name VARCHAR(128),
	city VARCHAR(64),
	...
	Name VARCHAR(64) FOREIGN KEY REFERENCES PEOPLE
	PRIMARY KEY (street-number, street-name, city))
```

### Relación muchos-a-muchos
Se crea una tabla aparte donde se copian, como *foreign keys*, las llaves primarias de las tablas representando los registros involucrados en la relación:
```sql
CREATE TABLE SUPPLIER (
	SupName character(100) PRIMARY KEY,
	...);
CREATE TABLE LABORATORY (
	LabName character(200) PRIMARY KEY,
	...);
CREATE TABLE BUYS (
	SupName character(100) FOREIGN KEY REFERENCES SUPPLIER,
	LabName character(200) FOREIGN KEY REFERENCES LABORATORY,
	CompoundId character(10),
	Amount int,
	Date date,
	...
	PRIMARY KEY (SupName, LabName));
```

## Referencias
[[Relaciones]]