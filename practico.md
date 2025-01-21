# Sistema de Gimnasio "PowerGym" 🏋️‍♂️

## Historia del Cliente
"Tengo un gimnasio pequeño y necesito un sistema simple para gestionar a mis clientes y las clases. Quiero registrar los datos básicos de mis clientes,
 controlar sus membresías mensuales, y que puedan inscribirse en las clases que ofrecemos. También tengo instructores que dan las clases y necesito saber 
 qué clases da cada uno."

## Requisitos Funcionales

### Gestionar Clientes
- Registrar nuevos clientes (nombre, teléfono, email)
- Verificar si su membresía está activa o no
- Guardar fecha de inicio y fin de membresía

### Gestionar Clases
- Crear clases (yoga, spinning, zumba)
- Asignar instructor a cada clase
- Registrar horarios de clases
- Permitir que clientes se inscriban en clases

### Gestionar Instructores
- Registrar datos de instructores
- Asignar qué clases puede dar cada instructor

## Requisitos No Funcionales
- Fácil de usar
- Rápido
- Seguro (solo personal autorizado puede usar el sistema)
- Debe funcionar en una computadora básica

## Diagrama del Sistema

[![Diagrama-ER-de-DBMS-notaci-n-UML.png](https://i.postimg.cc/bN3rhfgz/Diagrama-ER-de-DBMS-notaci-n-UML.png)](https://postimg.cc/4mHs6MjM)

## Explicación de cada relación:

### CLIENTE -- MEMBRESIA
- Un cliente puede tener muchas membresías.
- Una membresía pertenece a un solo cliente.

### CLIENTE -- INSCRIPCION
- Un cliente puede tener muchas inscripciones.
- Una inscripción pertenece a un solo cliente.

### INSCRIPCION -- CLASE
- Una inscripción es para una sola clase.
- Una clase puede tener muchas inscripciones.

### CLASE -- INSTRUCTOR
- Una clase es dictada por un instructor.
- Un instructor puede dictar una clase.
- (Esta última podría ajustarse a ||--o{ si un instructor puede dar varias clases)

# Modelo en SQL 


```sql
-- Crear la base de datos
CREATE DATABASE powergym;
USE powergym;

-- Tabla de Clientes
CREATE TABLE clientes (
    id_cliente INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL,
    telefono VARCHAR(20),
    email VARCHAR(100),
    fecha_registro DATE
);

-- Tabla de Membresías
CREATE TABLE membresias (
    id_membresia INT PRIMARY KEY AUTO_INCREMENT,
    id_cliente INT,
    fecha_inicio DATE,
    fecha_fin DATE,
    estado VARCHAR(20), -- 'Activa' o 'Vencida'
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente)
);

-- Tabla de Instructores
CREATE TABLE instructores (
    id_instructor INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL,
    telefono VARCHAR(20),
    email VARCHAR(100)
);

-- Tabla de Clases
CREATE TABLE clases (
    id_clase INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(50) NOT NULL,
    id_instructor INT,
    horario TIME,
    dia VARCHAR(20), -- 'Lunes', 'Martes', etc.
    cupo_maximo INT,
    FOREIGN KEY (id_instructor) REFERENCES instructores(id_instructor)
);

-- Tabla de Inscripciones a Clases
CREATE TABLE inscripciones (
    id_inscripcion INT PRIMARY KEY AUTO_INCREMENT,
    id_cliente INT,
    id_clase INT,
    fecha DATE,
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente),
    FOREIGN KEY (id_clase) REFERENCES clases(id_clase)
);




## Datos de Ejemplo

```sql
-- Insertar algunos clientes
INSERT INTO clientes (nombre, telefono, email, fecha_registro) VALUES
('Juan Pérez', '555-1234', 'juan@email.com', '2024-01-01'),
('María López', '555-5678', 'maria@email.com', '2024-01-02');

-- Insertar instructores
INSERT INTO instructores (nombre, telefono, email) VALUES
('Carlos Ruiz', '555-9876', 'carlos@gym.com'),
('Ana Silva', '555-6543', 'ana@gym.com');

-- Insertar clases
INSERT INTO clases (nombre, id_instructor, horario, dia, cupo_maximo) VALUES
('Yoga', 1, '09:00:00', 'Lunes', 15),
('Spinning', 2, '18:00:00', 'Martes', 10);



