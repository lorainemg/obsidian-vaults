# Funciones para Tratar Strings
Creado: 2022-04-29 22:43
Tags: #sql, #data-science, #eda, #data-cleaning, #data-preprocessing , #code
Topic: [[Limpieza de Datos]]

----

Funciones útiles que están presentes tanto en Postgres como en MySQL para tratar con strings organizadas con respecto a lo que hacen:
- Funciones que **limpian** el string: ellos lo cambian desasiéndose de ciertos caracteres o transformando caracteres existentes. Entre ellas están `TRIM()`, `LOWER()`, y `UPPER()`. El inverso de esto (añadir caracteres al string) es llamado _padding_, expresado como `LPAD()`, `RPAD()` y otros.
- Funciones que **encuentran** elementos (caracteres o substrings) dentro de string dado. Las más populares son `POSITION()`, y `STRPOS()`.
- Funciones que **extraen** elementos de un string o **dividen** el string en partes. Esto incluye funciones como `SUBSTR()` y `SPLIT()`. El inverso de esto (poner junto diferentes strings en uno solo) es llamado generalmente **concatenación**, expresado como `CONCAT()`.
- Otras funciones están disponibles como **reemplazo**, donde partes de una string son eliminadas y otros caracteres son substituidos por ellos, como `SUBSTR()`.
- Finalmente, la mayoría de las funciones incluyen la función útil `LENGTH()`.

## Referencias
[[Tareas de la Limpieza de Datos]]