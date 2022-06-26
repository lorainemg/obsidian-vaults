# Algoritmo de K-Means
Creado: 2022-06-26 11:04
Tags: #sql, #data-science, #unsupervised, #k-means
Topic: [[Enfoques no Supervisados]]

----

El algoritmo de clustering K-means usa el siguiente enfoque:
1.  Elige el número de clusters `k`.
2.  Elige `k` puntos de datos aleatorios y crea los clusters poniendo cada punto solo en un cluster. Pon la media (también llamado **centroid**) de cada cluster para ser este (único) punto.
3.  Por cada punto de datos `p`, calcula la distancia entre `p` y cada uno de los centroides del cluster; asigna `p` al cluster con la menor distancia.
4.  Cuando esto esté hecho, en cada cluster recalcula la **media** o **centroide**.
5.  Repite la asignación de los puntos de datos `p` al clusters computando de nuevo la distancia de `p` a cada cluster, usando un nuevo centroide.
6.  Repite los últimos dos pasos hasta que los clusters no cambian, o hasta que cada cluster es suficientemente **cohesivo**, o por un número fijo de iteraciones.

## Referencias
[[Distancias]]
[[Cohesión de un Cluster]]