# RetailChain



¿Cuántas filas devuelve cada consulta y por qué son distintas? Explicá con ejemplos concretos de los datos qué filas se eliminaron con UNION.



Cada sucursal tiene 7 registros, así que en total hay 14. UNION ALL devuelve las 14 filas porque conserva todos los registros, incluso los repetidos. UNION devuelve 11 porque elimina las filas que son completamente idénticas.



Las 3 filas eliminadas son los productos que existen en ambas sucursales con exactamente los mismos datos:



* 103, Monitor 4K 27", Computación
* 104, Teclado Mecánico, Accesorios
* 106, SSD Externo 1TB, Almacenamiento



¿Por qué UNION ALL es más eficiente que UNION? ¿Qué operación adicional realiza UNION internamente que consume más recursos?



UNION ALL solo concatena el resultado de las dos consultas, sin hacer nada más. UNION hace lo mismo y además tiene que eliminar duplicados, lo que implica comparar cada fila contra todas las demás del resultado combinado. ho.

Por eso, si ya sé que no hay duplicados o si los duplicados me importan, conviene usar UNION ALL



¿En qué casos de negocio usarías cada uno? Dá al menos dos ejemplos reales distintos a los del ejercicio.



UNION:



Armar una lista única de contactos para una campaña de email juntando los correos de clientes y los de suscriptores al newsletter, para no enviarle dos veces el mismo mensaje a una persona que figura en ambas listas.

Obtener la lista de ciudades donde opera una empresa combinando las ciudades de sus clientes y las de sus proveedores, sin repetir ninguna.



UNION ALL:



Calcular la facturación anual juntando las tablas de ventas de cada trimestre (o de cada mes), donde cada transacción debe contar aunque dos sean idénticas.

Consolidar los logs de varios servidores para contar la cantidad total de eventos o errores: si un mismo error ocurrió dos veces, ambas ocurrencias importan.



¿Qué pasa si las columnas de ambas consultas no coinciden en número o tipo? ¿Qué error genera SQL?



Distinto número de columnas: Devuelve un error y no ejecuta la consulta. Ambas partes del UNION deben tener la misma cantidad de columnas y en el mismo orden.



Distinto tipo de dato: depende del motor. Por eso conviene que las columnas que se combinan tengan tipos compatibles y significado equivalente.

