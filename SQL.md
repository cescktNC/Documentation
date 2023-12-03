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
