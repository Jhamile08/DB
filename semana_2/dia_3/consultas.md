# Entrenando consultas

- vas a tomar y crear la siguiente base de datos y vas a hacer las siguientes consultas
```sql
-- Crear base de datos

CREATE DATABASE libreria;

USE libreria;
 
-- Tabla de autores

CREATE TABLE autores (

    id INT PRIMARY KEY AUTO_INCREMENT,

    nombre VARCHAR(100) NOT NULL,

    nacionalidad VARCHAR(50)

);
 
-- Tabla de libros

CREATE TABLE libros (

    id INT PRIMARY KEY AUTO_INCREMENT,

    titulo VARCHAR(150) NOT NULL,

    genero VARCHAR(50),

    anio_publicacion INT,

    autor_id INT,

    precio DECIMAL(10,2),

    FOREIGN KEY (autor_id) REFERENCES autores(id)

);
 
-- Tabla de clientes

CREATE TABLE clientes (

    id INT PRIMARY KEY AUTO_INCREMENT,

    nombre VARCHAR(100),

    correo VARCHAR(100),

    ciudad VARCHAR(50)

);
 
-- Tabla de ventas

CREATE TABLE ventas (

    id INT PRIMARY KEY AUTO_INCREMENT,

    cliente_id INT,

    libro_id INT,

    fecha DATE,

    cantidad INT,

    FOREIGN KEY (cliente_id) REFERENCES clientes(id),

    FOREIGN KEY (libro_id) REFERENCES libros(id)

);

```




# Nivel Básico

    Muestra todos los libros registrados en la base de datos.

    Lista únicamente los nombres de los autores.

    Busca los libros publicados después del año 2015.

    Filtra los clientes que viven en una ciudad específica (por ejemplo, Bogotá).

    Cuenta cuántos libros hay en total en la base de datos.

 # Nivel Intermedio

    Muestra los títulos de los libros junto con el nombre del autor correspondiente.

    Calcula cuántos libros ha comprado cada cliente.

    Obtén el promedio de precios agrupado por género de libro.

    Muestra los clientes que han comprado más de 3 libros en total.

    Lista los libros escritos por autores de nacionalidad "Colombiana".

 # Nivel Avanzado

    Muestra los libros que aún no han sido vendidos.

    Encuentra los clientes que han comprado libros de un autor específico (por ejemplo, Gabriel García Márquez).

    Lista los 3 libros más vendidos (por cantidad).

    Calcula los ingresos generados por cada libro (precio × cantidad vendida).

    Muestra los autores que han publicado más de un libro.