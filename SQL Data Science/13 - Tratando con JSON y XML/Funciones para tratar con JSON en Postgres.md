# Funciones para tratar con JSON en Postgres
Creado: 2022-06-26 11:23
Tags: #sql, #data-science, #json-xml, #postgres, #json
Topic: [[Tratando con JSON y XML]]

----

Existen varias funciones para tratar con JSON en Postgres:
-   `JSON_each(JSON)`: Expande el objeto JSON más atrás en un conjunto de pares llave/valor, cada par se convierte en una fila en la tabla resultante.
-   `JSON_extract_path(from_JSON, VARIADIC path_elems text[])`: Retorna el valor de JSON encontrado siguiendo el argumento `path_elems`.
-   `JSON_populate_recordset(base anyelement, from_JSON JSON)`: Expande el array de objetos más afuera en el segundo argumento a un conjunto de filas cuyas columnas matchean el tipo de fila definida en el primer argumento.

## Referencias
[[Datos Jerárquicos]]
