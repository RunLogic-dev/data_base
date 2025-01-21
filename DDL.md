# Primeros pasos en Base de Datos

## Usando DDL

### Ejercicio 1: Crear una base de datos para una tienda en línea
```sql
CREATE DATABASE tienda_online;
USE tienda_online;

Ejercicio 2: Crear tabla de categorías

CREATE TABLE categorias (
    id_categoria INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(50) NOT NULL,
    descripcion TEXT,
    activo BOOLEAN DEFAULT true,
    fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

Ejercicio 3: Crear tabla de productos con clave foránea

CREATE TABLE productos (
    id_producto INT PRIMARY KEY AUTO_INCREMENT,
    id_categoria INT,
    nombre VARCHAR(100) NOT NULL,
    precio DECIMAL(10,2) NOT NULL,
    stock INT DEFAULT 0,
    fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_categoria) REFERENCES categorias(id_categoria)
);

ALTER - Modificar la estructura de objetos existentes
Ejercicio 4: Agregar columna a tabla existente

ALTER TABLE productos
ADD COLUMN sku VARCHAR(20) UNIQUE;

Ejercicio 5: Modificar tipo de dato de una columna
ALTER TABLE productos
MODIFY COLUMN descripcion VARCHAR(500);

DROP - Eliminar objetos de la base de datos
Ejercicio 6: Eliminar una tabla
-- DROP TABLE productos; -- (Comentado para no ejecutar accidentalmente)

TRUNCATE - Eliminar todos los registros de una tabla
Ejercicio 7: Vaciar una tabla

-- TRUNCATE TABLE productos; -- (Comentado para no ejecutar accidentalmente)