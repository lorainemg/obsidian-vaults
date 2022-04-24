# Tratar con Datos no Tabulares
Creado: 2022-04-23 22:53
Tags: #sql, #data-science, #no-tabular, #schemes
Topic: [[Esquema de Bases de Datos]]

----

Existen diferentes opciones para tratar con cada uno de los escenarios típicos que provocan datos no tabulares:

### Datos Opcionales (Heterogéneos):
Para tratar con estos atributos se tienen las siguientes opciones:
- Crear una sola tabla y añadir todos los atributos presentes en cualquier registro al esquema. Entonces, en cada fila, se describe un registro, cuando el registro no tiene un valor para un atributo se usa el marcador NULL.
- Identificar conjuntos de registros con los mismos atributos y crear una tabla para cada uno de ellos.

### Atributos Multi-Valor
Para tratar con estos atributos se describe un registro con múltiples filas, cada valor para el atributo en cada fila. Esto causa ciertas anomalías, que pueden ser arregladas normalizando los datos.

### Datos Complejos
Para tratar con los datos complejos se crean diferentes tablas para cada uno de los eventos o entidades relacionadas y se establece una relación entre ellos.

## Referencias
[[Datos no Tabulares]]