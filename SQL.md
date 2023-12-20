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
INSERT INTO clientes(id, nombre, dni, telefono, email) VALUES(1, "Francesc Navarro Crespo", "39913428X", 653574853, "cesccat82@gmail.com");
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
SELECT Count(*) AS ciudadesDiferentes FROM (SELECT DISTINCT ciudad FROM clientes);
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
SELECT * FROM clientes WHERE ciudad='Mexico';
SELECT * FROM clientes WHERE clienteID=1;
SELECT * FROM clientes WHERE clienteID > 80;
```
