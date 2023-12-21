## Manipulación de BASES DE DATOS
### Crear
```sql
CREATE DATABASE agencia_viajes;
```
### Eliminar
```sql
DROP DATABASE agencia_viajes;
```
### Mostrar
```sql
SHOW DATABASES;
```
### Entrar
```sql
USE agencia_viajes;
```


## Manipulación de TABLAS
### Crear
```sql
CREATE TABLE clientes (
  id INT PRIMARY KEY,
  nombre VARCHAR(30) NOT NULL,
  dni VARCHAR(9),
  telefono INT,
  email VARCHAR(20)
);
```
### Eliminar
```sql
DROP TABLE clientes;
```
### Mostrar Estructura
```sql
DESCRIBE clientes;
```
### Borrar columna
```sql
ALTER TABLE clientes DROP COLUMN telefono;
```
### Añadir columna
```sql
ALTER TABLE clientes ADD COLUMN telefono INT(9);
```
### Añadir constraint
```sql
ALTER TABLE clientes ADD CONSTRAINT PK_clientes PRIMARY KEY (ID, nombre);
```
### Eliminar constraint
```sql
ALTER TABLE clientes DROP CONSTRAINT PK_clientes;
```
### Cambiar el nombre de la tabla
```sql
ALTER TABLE clientes RENAME TO usuarios;
```
### Cambiar el nombre de la columna
```sql
ALTER TABLE clientes RENAME nombre TO nombre_completo;
```
### Borrar los datos de la tabla
```sql
TRUNCATE TABLE clientes;
```


## Modificación de datos
### INSERT INTO (añadir una fila en una tabla)
```sql
INSERT INTO clientes (id, nombre, dni, telefono, pais, ciudad) VALUES (1, "Francesc Gavaldà Reig", "388745124-K", 654123574, "España", "Tarragona");
INSERT INTO clientes VALUES (2, "Alba Cardona Bonastre", "38914452-Q", 632123478, "Dinamarca", "Copenhague");
```
### Añadir múltiples filas en una tabla
```sql
INSERT INTO clientes (id, nombre, dni, telefono, pais, ciudad)
VALUES
(1, "Francesc Gavaldà Reig", "32214578-L", 621789621, "España", "Tarragona"),
(2, "Alba Cardona Bonastre", "38914452-Q", 632123478, "Dinamarca", "Copenhague"),
(3, "Judit Fortuny Roig", "39945278-M", 633788415, "Reino Unido", "Londres");
```
### Valor NULL (significa que este campo no tiene ningún valor, sirve para campos opcionales)
```sql
INSERT INTO clientes (id, nombre, dni, telefono, pais, ciudad) VALUES (3, "Judit Fortuny Roig", "39945278-M", null, "Reino Unido", "Londres");
```
### UPDATE (modificar registro en una tabla)
```sql
UPDATE clientes SET nombre = 'Francesc Puig Crespo', ciudad = 'Londres' WHERE id = 1;
UPDATE clientes SET nombre = 'Albert' WHERE pais = 'España';
UPDATE clientes SET nombre = 'Alex'; -- Sin el WHERE, cambia todos los nombres de la tabla 'clientes'
```
### DELETE (borrar registro en una tabla)
```sql
DELETE FROM clientes WHERE nombre = 'Francesc Puig Crespo';
DELETE FROM clientes; -- Borra todas las filas de la tabla 'clientes', pero la tabla sigue existiendo.
```


## Consultando tablas
### Mostrar datos de 1 tabla
```sql
SELECT * FROM clientes;
SELECT nombre, telefono FROM clientes;
```
### Mostrar datos distintos de 1 tabla (evitamos mostrar datos duplicados o repetidos)
```sql
SELECT DISTINCT ciudad FROM clientes;
SELECT COUNT(DISTINCT ciudad) FROM clientes;
SELECT COUNT(*) AS ciudadesDiferentes FROM (SELECT DISTINCT ciudad FROM clientes);
```
### Cláusula WHERE
#### Operadores
Operador|Descripción
|--------|-----------|
|=|Igual|
|>|Más grande que|
|<|Más pequeño que|
|>=|Más grande o igual que|
|<=|Más pequeño o igual que|
|<> o !=|Diferente|
|BETWEEN|Entre un rango determinado|
|LIKE|Busca sobre un patrón|
|IN|Para especificar múltiples posibles valores para una columna|
```sql
SELECT * FROM clientes WHERE pais='Mexico';
SELECT * FROM clientes WHERE clienteID=1;
SELECT * FROM clientes WHERE clienteID > 80;
```
### Ordenar el resultado con la palabra clave ORDER BY
```sql
SELECT * FROM productos ORDER BY precio;
SELECT * FROM productos ORDER BY precio DESC;
SELECT * FROM productos ORDER BY nombre;
SELECT * FROM clientes ORDER BY pais, nombre;
SELECT * FROM clientes ORDER BY pais ASC, nombre DESC;
```
### Operador AND, OR y NOT
1. AND - se tienen que cumplir todas las condiciones.
2. OR - almenos una se tiene que cumplir.
3. NOT - resultado opuesto.
```sql
SELECT * FROM clientes WHERE pais = 'España' AND nombre LIKE 'G%';
SELECT * FROM clientes WHERE pais = 'Alemania' OR pais = 'España';
SELECT * FROM clientes WHERE pais = 'Alemania' AND ciudad = 'Berlin' AND codigoPostal > '12000';
SELECT * FROM clientes WHERE ciudad = 'Berlin' OR nombre LIKE 'G%' OR pais = 'Noruega';
SELECT * FROM clientes WHERE pais = 'España' AND (nombre LIKE 'G%' OR nombre LIKE 'R%');
SELECT * FROM clientes WHERE NOT pais = 'España';
SELECT * FROM clientes WHERE nombre NOT LIKE 'A%';
SELECT * FROM clientes WHERE clienteID NOT BETWEEN 10 AND 60;
SELECT * FROM clientes WHERE ciudad NOT IN ('Paris', 'Londres');
SELECT * FROM clientes WHERE NOT clienteID > 50;
```
### Operador IS NULL y IS NOT NULL
1. IS NULL - para saber valores vacíos.
2. IS NOT NULL - para saber valores que no són vacíos.
```sql
SELECT nombre, telefono, direccion FROM clientes WHERE direccion IS NULL;
SELECT nombre, telefono, direccion FROM clientes WHERE direccion IS NOT NULL;
```
### Cláusula TOP, LIMIT, FETCH FIRST o ROWNUM
1. TOP - devuelve un número específico de registros.
2. LIMIT - lo mismo pero para MySQL.
3. FETCH FIRST o ROWNUM - lo mismo pero para Oracle.
```sql
SELECT TOP 3 * FROM clientes;
SELECT TOP 3 * FROM clientes ORDER BY nombre DESC;
SELECT TOP 3 * FROM clientes WHERE pais = 'Alemania';
SELECT TOP 50 PERCENT * FROM clientes; -- Devuelve el 50% de los registros de la tabla 'clientes'

SELECT * FROM clientes LIMIT 3;
SELECT * FROM clientes ORDER BY nombre DESC LIMIT 3;
SELECT * FROM clientes WHERE pais = 'Alemania' LIMIT 3;

SELECT * FROM clientes FETCH FIRST 3 ROWS ONLY; -- Oracle
SELECT * FROM clientes ORDER BY nombre DESC FETCH FIRST 3 ROWS ONLY;
SELECT * FROM clientes WHERE pais = 'Alemania' FETCH FIRST 3 ROWS ONLY;
SELECT * FROM clientes FETCH FIRST 50 PERCENT ROWS ONLY;
```
### Funciones MIN(), MAX(), COUNT(), SUM() y AVG()
1. MIN() - devuelve el valor más pequeño de la columna especificada.
2. MAX() - devuelve el valor más grande de la columna especificada.
3. COUNT() - devuelve el número de filas que cumplen un criterio especificado.
4. SUM() - devuelve la suma total de una columna numérica.
5. AVG() - devuelve el valor promedio de una columna numérica
```sql
SELECT MIN(precio) FROM productos;
SELECT MAX(precio) FROM productos;
SELECT MIN(precio) FROM productos WHERE tipoProducto = 'Gel';
SELECT MIN(precio) AS PrecioMasBajo FROM productos; -- Usa el alias 'PrecioMasBajo'

SELECT COUNT(*) FROM productos;
SELECT COUNT(productoID) FROM productos WHERE precio > 20;
SELECT COUNT(nombre) FROM productos; -- Devuelve el número de productos que el campo 'nombre' no es NULL
SELECT COUNT(DISTINCT precio) FROM productos; -- Ignora duplicados
SELECT COUNT(*) AS [Número de registros] FROM productos;

SELECT SUM(cantidad) FROM productos;
SELECT SUM(cantidad) FROM productos WHERE productoID = 11;
SELECT SUM(cantidad * 10) FROM productos; -- Multiplica cada cantidad por 10 y luego lo suma todo

SELECT AVG(precio) FROM productos;
SELECT AVG(precio) FROM productos WHERE tipoProducto = 'Gel';
SELECT * FROM productos WHERE precio > (SELECT AVG(precio) FROM productos); -- Devuelve los productos con un precio superior al promedio
```






SELECT SUM(Price * Quantity)
FROM OrderDetails
LEFT JOIN Products ON OrderDetails.ProductID = Products.ProductID;
