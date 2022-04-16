# Etapas y Operaciones en el Ciclo de Vida de los Datos
Creado: 15/04/2022

El primer paso para el análisis de datos es el **Análisis Exploratorio de Datos** (*Exploratory Data Analysis, EDA*), también llamado ***data profiling***. En este paso, se trata de aprender las características básicas de los datos y cualquier objeto, evento u observación que describe. 

Si hay metadatos, se comprueba las características de dataset con respecto a ellos, tratando de validar lo que nos ha dicho (y aumentar la información del dataset, si es posible). Si no hay metadatos, es momento de recolectarlos.

Entre las actividades que involucra la realización de EDA, se encuentran acciones como clasificar el dataset, sacar una idea de los atributos involucrados, y para cada atributo, buscar tener una idea de la distribución de datos a través de técnicas de **visualización**, o **herramientas descriptivas**, como histogramas y medidas de centralidad o dispersión.

EDA es importante porque ayuda a contruir un entendimiento de los datos y guiar el trabajo futuro.

Entre las técnicas usadas para la limpieza de datos (*data cleaning*) se encuentran:
- Encontrar y manejar los valores faltantes.
- Encontrar y manejar valores atípicos (*outliers*)
- Encontrar y manejar *datos duplicados*

Las técnicas típicas para realizar el preprocesamiento de datos (o preparación de datos) incluyen:
- Transformaciones para poner los valores de los datos en un cierto formato o en un cierto cuadro de referencia. Esto involucra operaciones como *normalización*, *escalado*, o *estandarización*
- Transformaciones que cambian los valores de los datos de un tipo a otro, como *discretización* o *binarización*.
- Transformaciones que cambian la estructura del dataset, como *pivoting* o *(des)normalización*. La mayoría de las herrmamientas de análisis de datos asumen que el dataset está organizado en un formato determinado, llamado **datos tabulares**; los datasets que no estén en este formato necestan ser reestructurados.

## Referencias:
