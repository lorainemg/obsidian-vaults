# Llaves Primarias, IDs automáticos, Identificadores Únicos
Creado: 2022-04-21 23:43
Tags: #sql, #data-science, #database, #code, #postgres, #mysql 
Topic: [[Tablas de Bases de Datos]]

----
 
 A continuación se muestra cómo alterar características de los atributos en difierentes lenguajes para crear llaves primarias, IDs automáticos e identificadores únicos.

### Llaves primarias
Las llaves primarias se crean con la siguiente sintaxis:
```sql
CREATE TABLE ny-fligts (flightid int PRIMARY KEY, ...);
```

O después del último atributo:
```sql
CREATE TABLE ny-flights (flightid int, ... timehour timestamp, PRIMARY KEY(flightid));
```
Además podemos modificar una tabla existente para añadir información sobre las llaves
```sql
ALTER TABLE ny-flights ADD PRIMARY KEY(flightid);
```
Técnicamente, la declaración de una llave primaria es lo que es llamada una restricción y también puede ser escrita como tal:
```sql
CREATE TABLE ny-fligts (flightid int CONSTRAINT nyf-pk PRIMARY KEY, ...);
```
```sql
CREATE TABLE ny-flights (flightid int, ... timehour timestamp, CONSTRAINT nyf-pk PRIMARY KEY (flightid));
```

### Atributos IDs Automáticos
Comandos para crear IDs Automáticos al crear la tabla:
- En Postgres:
	```postgres
	CREATE TABLE books (book-id SERIAL PRIMARY KEY, ...)
	```
- Y en MySQL:
	```mysql
	CREATE TABLE books (book-id INT NOT NULL AUTO_INCREMENT PRIMARY KEY, ...)
	```
También pueden ser añadidos a la tabla después de su creación:
- En Postgres:
	```postgres
	ALTER TABLE books ADD book-id INT AUTO_INCREMENT PRIMARY KEY;
	```
- En MySQL:
	```mysql
	ALTER TABLE books ADD book-id INT AUTO_INCREMENT PRIMARY KEY;
	```
### Identificadores Únicos
Comando para crear identificadores únicos:
```mysql
CREATE TABLE car (
	Vin VARCHAR(36) PRIMARY KEY, 
	State CHAR(2), 
	License-number CHAR(6), 
	Year INTEGER, 
	UNIQUE (State, Licence-number))
```
La última línea también podría ser:
```mysql
CONSTRAINT uniq-car UNIQUE (State, License-number).
```
Además, también se podría hacer después,
```mysql
ALTER TABLE car ADD UNIQUE (State, License-number)
```

## Referencias
[[Tratar con Tablas de Bases de Datos]]