# LENGUAJE DE MANIPULACIÓN DE DATOS (DML)

El DML nos permite manipular los datos dentro de las tablas. A continuación, se presentan ejemplos de las principales operaciones DML: INSERT, UPDATE, DELETE y SELECT.

## 1. INSERT - Insertar registros

### Ejercicio 8: Insertar categorías
```sql
INSERT INTO categorias (nombre, descripcion) VALUES
('Electrónicos', 'Productos electrónicos y gadgets'),
('Ropa', 'Todo tipo de prendas de vestir'),
('Libros', 'Libros físicos y digitales');

Ejercicio 9: Insertar productos

INSERT INTO productos (id_categoria, nombre, precio, stock, sku) VALUES
(1, 'Smartphone XYZ', 599.99, 50, 'SMRT001'),
(1, 'Laptop ABC', 999.99, 30, 'LAP001'),
(2, 'Camiseta Básica', 19.99, 100, 'SHIRT001');

2. UPDATE - Actualizar registros
Ejercicio 10: Actualizar precio de un producto

UPDATE productos 
SET precio = 549.99 
WHERE sku = 'SMRT001';

Ejercicio 11: Actualizar stock de múltiples productos

UPDATE productos 
SET stock = stock + 10 
WHERE id_categoria = 1;

3. DELETE - Eliminar registros
Ejercicio 12: Eliminar un producto específico

DELETE FROM productos 
WHERE sku = 'SHIRT001';

4. SELECT - Consultar datos
Ejercicio 13: Consulta básica

SELECT * FROM productos;

Ejercicio 14: Consulta con JOIN

SELECT p.nombre AS producto, 
       c.nombre AS categoria, 
       p.precio, 
       p.stock
FROM productos p
JOIN categorias c ON p.id_categoria = c.id_categoria;

