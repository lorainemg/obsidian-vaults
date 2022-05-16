# Cómo se Aplica EDA
Creado: 2022-05-15 23:28
Tags: #sql, #data-science, #eda 
Topic: [[EDA]]

----

Para realizar EDA en datos estructurados donde el esquema es conocido se procede cómo sigue:
- Se examina cada atributo en aislamiento. Esto es llamado análisis **univariado** en la literatura estadística. La primera tarea es determinar el tipo de dominio. Luego se exploran los valores de la siguiente forma:
    - Para los __atributos categóricos__, los histogramas y sus variaciones son la herramienta principal.
    - Para los __valores numéricos__, se encuentran medidas de tendencia central y dispersión. Además podemos querer encajar una distribución conocida a un dominio.
    
    En este punto, se deberá intentar identificar los errores potenciales en el dominio de cada atributo. Algunos de los errores principales son: **_valores faltantes_**, **_outliers_** y errores de tipo, etc.
- Examinar las relaciones (o su falta de ellas) entre varios atributos. Esto es llamado análisis **multivariado** en la literatura estadística. Algunas técnicas para evaluar las conexiones potenciales son:
    - Para el análisis **categórico-categórico**: tablas de contingencia, test chi-square.
    - Para el análisis **categórico-numérico**: regresión logística, ANOVA.
    - Para el análisis **numérico-numérico**: covarianza, correlación, PMI, regresión lineal.
    - Para el análisis **ordinal-ordinal**: Spearman’s rank, Kendall’s rank,

## Referencias
[[Actividades Realizadas en EDA]]