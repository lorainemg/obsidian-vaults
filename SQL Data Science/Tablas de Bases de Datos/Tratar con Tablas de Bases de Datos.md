# Tratar con Tablas de Bases de Datos
Creado: 2022-04-21 23:16
Tags: #sql, #data-science, #database, #code, #mysql, #postgres 
Topic: [[Tablas de Bases de Datos]]

----

Los comandos más comunes para tratar con tablas de bases de datos son:
- Crear una tabla: 
	```sql
	CREATE TABLE Employee (name char(64), age int, date-of-birth date, salary float
	```
- Insertar datos en una tabla:
	```sql 
	INSERT INTO {table_name} Values(...)
	```
	- Para especificar el orden de los atributos se puede usar el comando:
	 ```sql
	 INSERT INTO {table_name(B,C,A)} Values(b, c, a)
	 ```
- Destruir todos los datos de una tabla: 
	```sql
	DROP {table_name}
	```
- Mostrar información de una tabla, incluído el esquema: 
	- En MySQL: 
	```mysql
	SHOW COLUMNS [FROM table_name] [FROM database_name]
	```
	- En Postgres: 
	```postgres
	\dt database-name.table-name
	``` 
	O para todas las bases de datos existentes:
	```postgres
	\dt *.*
	```
	- Otra forma de extraer información directa es mediante el código: 
	```sql
	SELECT column_name, data_type 
		FROM INFORMATION_SCHEMA.COLUMNS 
		WHERE table_name = 'table_name' 
			[AND table_schema = 'database_name'];
	```
## Referencias
[[Tratar con Bases de Datos]]
[[Atributos de un Dataset]]