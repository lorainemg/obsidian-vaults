# Limitaciones de la Regresión Lineal
Creado: 2022-06-26 10:37
Tags: #sql, #data-science, #supervised, #linear-regression
Topic: [[Enfoques Supervisados]]

----

Limitaciones que deberíamos tener en cuenta respecto a la regresión lineal:
-   Asume que hay una relación lineal entre las variables dependientes e independientes (no una más compleja)
-   Asume que los errores se comportan bien (los errores deben ser independientes e idénticamente distribuidos con una distribución normal)
-   Requiere que normalicemos todos nuestros datos antes; si un atributo tiene una magnitud mucho más grande que otro, dominará los cálculos, creando la mayor diferencia, y por lo tanto, será minimizado incluso a expensas de otros factores.
-   Es muy sensitivo a los _outliers_.

## Referencias