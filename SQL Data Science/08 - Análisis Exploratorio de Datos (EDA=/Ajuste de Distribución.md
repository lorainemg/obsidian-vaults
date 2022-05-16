# Ajuste de Distribución
Creado: 2022-05-15 23:56
Tags: #sql, #data-science, #eda, #distribution, #code 
Topic: [[EDA]]

----

El enfoque general es el siguiente para el ajuste de distribución es el siguiente:
- Formar los datos en forma de una distribución, es decir, crear una tabla con el esquema `(valor, probabilidad)`. Esto puede ser hecho como fue visto anteriormente, estimando probabilidades de los porcentajes, y los porcentajes de recuentos sin procesar de datos.
	```sql
	CREATE TABLE DATA AS
	SELECT num_minutes, sum(1.0/ total) as prob
	FROM Raw_data, (SELECT count(*) as total FROM Raw_data)
	GROUP BY num_minutes;
    ```
- Encontrar los parámetros de esta distribución empírica, en particular, la media y la distribución estándar.  
- Añadir un atributo para la estimación de la tabla de datos. Terminamos con una tabla con el esquema `(valor, probabilidad, estimado)`. Esta nueva tercera columna tiene nulos en todas las filar por ahora.  
    ```sql
    CREATE TABLE NORMAL(data,observed_freq,expected_freq) AS
    SELECT num_minutes, freq, null
    FROM DATA;
    ```
- Escoger una distribución. Usando la fórmula para esta distribución, y la media y la desviación estándar de la muestra, genera un estimado de cada valor y lo deja en el atributo `estimado`. (En el siguiente ejemplo se usa la distribución normal, PostgreSQL)  
    ```sql
    UPDATE NORMAL
    SET expected_freq = (1 / sqrt(2*pi()*stddev)) *
    		exp(- (pow(observed_freq - avg, 2) / (2*stdev)));
    ```    
- Compara el estimado obtenido (`estimado`) con la `probabilidad` empírica y decide si la diferencia es lo suficientemente pequeña. Una manera muy fácil de hacer esto es añadir las diferencias absolutas y expresarlas en términos de desviaciones estándar. Una manera más sofisticada de atacar este problema es mediante el test chi-square.

## Referencias
[[Objetivos Principales de EDA]]