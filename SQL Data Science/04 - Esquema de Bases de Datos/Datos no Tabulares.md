# Datos no Tabulares
Creado: 2022-04-23 22:37
Tags: #sql, #data-science, #no-tabular, #schemes
Topic: [[Esquema de Bases de Datos]]

----

Tres de los escenarios típicos para que los datos sean **no tabulares**:
- Datos heterogéneos, es decir, datos donde los registros pueden tener valores para diferentes atributos.
- Datos con atributos multi-valor, es decir, atributos que tienen más de un valor por registro.
- Datos complejos involucrando eventos o entidades diferentes (pero relacionados)

Existen opciones para tratar con cada uno de estos escenarios:

### Datos Opcionales (Heterogéneos):
Para tratar con estos atributos se tienen las siguientes opciones:
- Crear una sola tabla y añadir todos los atributos presentes en cualquier registro al esquema. Entonces, en cada fila, se describe un registro, cuando el registro no tiene un valor para un atributo se usa el marcador NULL.
- Identificar conjuntos de registros con los mismos atributos y crear una tabla para cada uno de ellos.

### Atributos Multi-Valor
Para tratar con estos atributos se describe un registro con múltiples filas, cada valor para el atributo en cada fila. Esto causa ciertas anomalías, que pueden ser arregladas normalizando los datos.

### Datos Complejos
Para tratar con los datos complejos se crean diferentes tablas para cada uno de los eventos o entidades relacionadas y se establece una relación entre ellos.

## Referencias
[[Atributos de un Dataset]]
[[Atributos Simples]]
