# Exportar Datos
Creado: 2022-04-23 23:32
Tags: #sql, #data-science, #code, #mysql, #postgres, #data
Topic: [[Cargar y Descargar Datos de una BD]]

----

### MySQL
El comando para exportar los datos en MySQL tiene el siguiente formato:
```mysql
SELECT columns INTO OUTFILE filename
	[FIELDS [TERMINATED BY string]
	[ENCLOSED BY char]
	[ESCAPED BY char]]
FROM table-name;
```
Además se puede ejecutar el comando `mysqldump`: `mysqldump --databases database-name > mydump.sql` o `mysqldump database-name > mydump.sql`. Para guardar tablas específicas en la base de datos: `mysqldump database-name table-name > mydump.sql`. Para recargar un archivo guardado: `mysql < mydump.sql`.

### Postgres
Para exportar los datos en Postgres se usa el comando reverso de `COPY FROM`, `COPY TO`:
```sql
COPY { table_name [ ( column_name [, ...] ) ] | ( query ) }
TO ’filename’
[ [ WITH ] ( option [, ...] ) ]
```
El comando equivalente a `mysqldump` en Postgres es `pg_dump`: `pg_dump -t table-name mydb > filename.sql`. Para recuperar datos de un fichero:` psql -d new-table-name -f filename.sql`. Una base de datos entera puede ser guardada en un fichero: `pg_dump database-name > filename.sql`.

## Referencias
[[Tratar con Bases de Datos]]