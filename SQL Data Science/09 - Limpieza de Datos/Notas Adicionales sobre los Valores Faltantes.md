# Notas Adicionales sobre los Valores Faltantes
Creado: 2022-04-29 22:52
Tags: #sql, #data-science, #eda, #data-cleaning, #missing-values, #code
Topic: [[Limpieza de Datos]]

----

Cosas a tener en cuenta con valores faltantes (*NULL*):
- Cualquier comparación con *NULL* devuelve *Unknown*, haciendo que el cálculo falle. Para tratar con esto SQL provee 2 predicados especiales: `IS NULL` y `IS NOT NULL`.
- Como regla, las funciones de _aggregates_ (`SUM`, `AVG`, `MIN`, `MAX`) funcionan bien con *NULL*, ignorándolos. Una excepción de esto es `COUNT`, que cuenta filas, sin preocuparse del contenido de las mismas. Si todos los valores en un atributo son *NULL*, los _aggregates_ retornan un valor por defecto, esto es 0.
- En el contexto de `GROUP BY`, los valores *NULL* se tratan como uno solo. El comportamiento es el mismo que los _aggregates_: en cada grupo, se ignoran los *NULLS*:

## Referencias
[[Tipos Valores Faltantes]]