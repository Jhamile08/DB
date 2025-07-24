# Comandos SQL – Clasificación y Uso

En SQL, los comandos se agrupan en diferentes categorías según su función. A continuación se explican cada uno con ejemplos y su utilidad.

---

## 📘 1. DDL – Data Definition Language (Lenguaje de Definición de Datos)

Estos comandos definen la estructura de la base de datos, como tablas, columnas o índices.

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `CREATE` | Crea una nueva tabla, base de datos, vista, etc. | `CREATE TABLE libros (id INT, titulo VARCHAR(100));` |
| `DROP` | Elimina una tabla o base de datos. | `DROP TABLE libros;` |
| `ALTER` | Modifica una tabla existente (agrega/borra columnas, cambia tipos). | `ALTER TABLE libros ADD autor VARCHAR(100);` `ALTER TABLE prestamos
CHANGE COLUMN fecha_prestamo nueva_fecha DATE NOT NULL;` |
| `TRUNCATE` | Borra todos los datos de una tabla pero mantiene su estructura. | `TRUNCATE TABLE libros;` |

---

## 📘 2. DML – Data Manipulation Language (Lenguaje de Manipulación de Datos)

Estos comandos permiten insertar, actualizar o eliminar datos dentro de las tablas.

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `INSERT` | Agrega nuevos registros. | `INSERT INTO libros (id, titulo) VALUES (1, 'El Principito');` |
| `UPDATE` | Modifica registros existentes. | `UPDATE libros SET titulo = '1984' WHERE id = 1;` |
| `DELETE` | Elimina registros. | `DELETE FROM libros WHERE id = 1;` |
| `SELECT` | Consulta datos (también se clasifica como DQL). | `SELECT * FROM libros;` |

---

## 📘 3. DCL – Data Control Language (Lenguaje de Control de Datos)

Controla los permisos de los usuarios sobre la base de datos.

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `GRANT` | Concede permisos a un usuario. | `GRANT SELECT ON libros TO 'usuario1';` |
| `REVOKE` | Revoca permisos otorgados. | `REVOKE SELECT ON libros FROM 'usuario1';` |

---

## 📘 4. TCL – Transaction Control Language (Lenguaje de Control de Transacciones)

Administra las transacciones en la base de datos (confirmaciones y cancelaciones de cambios).

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `COMMIT` | Confirma los cambios realizados en la transacción. | `COMMIT;` |
| `ROLLBACK` | Revierte los cambios si hay errores. | `ROLLBACK;` |
| `SAVEPOINT` | Marca un punto dentro de una transacción para hacer rollback parcial. | `SAVEPOINT punto1;` |

---

## 📘 5. DQL – Data Query Language (Lenguaje de Consulta de Datos)

Permite hacer consultas para recuperar información.

| Comando | Descripción | Ejemplo |
|--------|-------------|---------|
| `SELECT` | Recupera datos de una o más tablas. | `SELECT * FROM libros WHERE autor = 'Gabriel García Márquez';` |

---

>  **Consejo práctico:** Aunque `SELECT` aparece en DML y DQL, oficialmente pertenece a **DQL** por ser una consulta pura que no modifica datos.

