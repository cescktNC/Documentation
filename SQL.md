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
### Añadir una fila en una tabla
```sql
INSERT INTO clientes (id, nombre, dni, telefono, email) VALUES (1, "Francesc Gavaldà Reig", "388745124-K", 654123574, "fgavalda@gmail.com");
INSERT INTO clientes VALUES (2, "Alba González Garcia", "38914452-Q", 632123478, "agonzalez@gmail.com");
```
### Añadir múltiples filas en una tabla
```sql
INSERT INTO clientes (id, nombre, dni, telefono, email)
VALUES
(1, "Francesc Gavaldà Reig", "32214578-L", 621789621, "fgavalda@gmail.com"),
(2, "Alba González Garcia", "38914452-Q", 632123478, "agonzalez@gmail.com"),
(3, "Judit López Martínez", "39945278-M", 633788415, "jlopez@gmail.com");
```
### Valor NULL (significa que este campo no tiene ningún valor, sirve para campos opcionales)
```sql
INSERT INTO clientes (id, nombre, dni, telefono, email) VALUES (3, "Judit López Martínez", "39945278-M", null, "jlopez@gmail.com");
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
### Operador AND (se tienen que cumplir todas las condiciones), OR (almenos una se tiene que cumplir) y NOT (resultado opuesto)
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
### Operador IS NULL (para saber valores vacíos) y IS NOT NULL (para saber valores que no són vacíos)
```sql
SELECT nombre, telefono, direccion FROM clientes WHERE direccion IS NULL;
SELECT nombre, telefono, direccion FROM clientes WHERE direccion IS NOT NULL;
```
