# CASE
Creado: 2022-04-24 20:23
Tags: #sql, #data-science, #code, #query 
Topic: [[Consulta Básica de SQL]]

----

La cláusula `CASE` es como una condicional ternaria. Un ejemplo de uso:
```sql
SELECT max(CASE WHEN month = 1 THEN temp ELSE 0 END)
		as JanMax
	max(CASE WHEN month = 2 THEN temp ELSE 0 END)
		as FebMax
FROM Temperatures;
```

## Referencias
[[SELECT]]