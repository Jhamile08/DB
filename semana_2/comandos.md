# Comandos SQL – Clasificación y Uso

En SQL, los comandos se agrupan en diferentes categorías según su función. A continuación se explican cada uno con su definición, uso y ejemplos prácticos.

---

## 📘 1. DDL – Data Definition Language (Lenguaje de Definición de Datos)

Define la estructura de la base de datos (tablas, columnas, índices).

| Comando   | Descripción                                                  | Ejemplo práctico                                                                 |
|-----------|--------------------------------------------------------------|----------------------------------------------------------------------------------|
| `CREATE`  | Crea una tabla, base de datos, vista, etc.                   | `CREATE TABLE libros (id INT PRIMARY KEY, titulo VARCHAR(100));`                |
| `DROP`    | Elimina una tabla o base de datos                            | `DROP TABLE libros;`                                                             |
| `ALTER`   | Modifica estructura de una tabla                             | `ALTER TABLE libros ADD autor VARCHAR(100);`                                     |
|           |                                                              | `ALTER TABLE libros CHANGE COLUMN titulo nombre_libro VARCHAR(150);`            |
| `TRUNCATE`| Borra todos los datos sin eliminar la tabla                  | `TRUNCATE TABLE libros;`                                                         |

---

## 📘 2. DML – Data Manipulation Language (Lenguaje de Manipulación de Datos)

Gestiona los datos dentro de las tablas.

| Comando   | Descripción                                                  | Ejemplo práctico                                                                 |
|-----------|--------------------------------------------------------------|----------------------------------------------------------------------------------|
| `INSERT`  | Inserta nuevos registros                                     | `INSERT INTO libros (id, titulo) VALUES (1, 'El Principito');`                  |
| `UPDATE`  | Modifica registros existentes                                | `UPDATE libros SET titulo = 'Cien años de soledad' WHERE id = 1;`               |
| `DELETE`  | Elimina registros                                             | `DELETE FROM libros WHERE id = 1;`                                               |
| `SELECT`  | Recupera datos (también se clasifica como DQL)               | `SELECT * FROM libros;`                                                          |

---

## 📘 3. DCL – Data Control Language (Lenguaje de Control de Datos)

Gestiona los permisos de acceso a la base de datos.

| Comando   | Descripción                                                  | Ejemplo práctico                                                                 |
|-----------|--------------------------------------------------------------|----------------------------------------------------------------------------------|
| `GRANT`   | Concede permisos a un usuario                                | `GRANT SELECT, INSERT ON libros TO 'usuario1'@'localhost';`                     |
| `REVOKE`  | Revoca permisos concedidos                                   | `REVOKE INSERT ON libros FROM 'usuario1'@'localhost';`                          |

---

## 📘 4. TCL – Transaction Control Language (Lenguaje de Control de Transacciones)

Controla las transacciones para mantener la integridad de los datos.

| Comando     | Descripción                                                | Ejemplo práctico                                                                 |
|-------------|------------------------------------------------------------|----------------------------------------------------------------------------------|
| `COMMIT`    | Guarda los cambios definitivos                             | `INSERT INTO libros VALUES (2, '1984'); COMMIT;`                                 |
| `ROLLBACK`  | Revierte los cambios no confirmados                        | `DELETE FROM libros WHERE id = 2; ROLLBACK;`                                     |
| `SAVEPOINT` | Crea un punto de restauración dentro de una transacción    | `SAVEPOINT antes_de_borrar; DELETE FROM libros WHERE id = 3;`                   |

---

## 📘 5. DQL – Data Query Language (Lenguaje de Consulta de Datos)

Permite hacer consultas sin modificar los datos.

| Comando   | Descripción                                                  | Ejemplo práctico                                                                 |
|-----------|--------------------------------------------------------------|----------------------------------------------------------------------------------|
| `SELECT`  | Recupera datos de una o más tablas                           | `SELECT titulo FROM libros WHERE autor = 'Gabriel García Márquez';`             |
|           | Con funciones agregadas                                      | `SELECT COUNT(*) AS total_libros FROM libros;`                                  |
|           | Con filtros y orden                                          | `SELECT * FROM libros WHERE id > 5 ORDER BY titulo ASC;`                         |

##  Guía para Armar Consultas SQL Avanzadas
 Estructura general de una consulta:

SELECT [funciones] [columnas] 
FROM [tabla] 
WHERE [condiciones]
GROUP BY [columnas]
HAVING [condiciones sobre agrupaciones]
ORDER BY [columna o alias] [ASC|DESC];

# Paso a Paso y Cuándo Usarlo
1. SELECT: ¿Qué quieres ver?
    Es obligatorio.

    Aquí defines qué columnas o funciones quieres mostrar.
    Puedes usar funciones como:

    -COUNT(*) – para contar registros.
    -AVG(columna) – para calcular promedios.
    -MAX(columna) – para el valor máximo.
    -MIN(columna) – para el valor mínimo.
    -SUM(columna) – para sumas.

    Puedes usar AS para renombrar la columna.

 Ejemplos:
```sql
SELECT nombre FROM usuarios;
SELECT COUNT(*) AS total FROM productos;
SELECT AVG(precio) AS promedio_precio FROM libros;
```
2. FROM: ¿De dónde lo tomas?

    Es obligatorio.
    Indica la tabla (o tablas) de la cual se extraen los datos.

 Ejemplo:
```sql
FROM libros
```
3. WHERE: ¿Qué condiciones deben cumplirse?

    Es opcional.
    Se usa para filtrar los registros antes de agrupar o contar.
    Puedes usar operadores:
        =, >, <, >=, LIKE, IN, BETWEEN, IS NULL, etc.

 Ejemplo:
```sql
WHERE precio > 20000 AND autor = 'Gabriel García Márquez'
```
4. GROUP BY: ¿Quieres agrupar por alguna columna?
    Se usa cuando usas funciones como COUNT, AVG, SUM, etc.
    Agrupa los datos por una o más columnas.

 Ejemplo:
```sql
GROUP BY autor
```
5. HAVING: ¿Qué condiciones deben cumplir los grupos?
    Se usa para filtrar los resultados agrupados (NO se usa con datos individuales).
    Se aplica después de GROUP BY.

 Ejemplo:
```sql
HAVING COUNT(*) > 2
```
6. ORDER BY: ¿En qué orden mostrar los resultados?

    Se usa para ordenar resultados al final.
    Puedes ordenar:

    - Ascendentemente: ASC (por defecto)
    - Descendentemente: DESC

    Puedes usar alias definidos con AS.

 Ejemplo:
```sql
ORDER BY promedio_precio DESC
```
# Ejemplo completo

¿Qué autores tienen más de 3 libros registrados? Ordénalos por cantidad, de mayor a menor.
```sql
SELECT autor, COUNT(*) AS cantidad
FROM libros
GROUP BY autor
HAVING cantidad > 3
ORDER BY cantidad DESC;
```
# Plantilla práctica
```sql
SELECT [columna o función agregada] AS [alias]
FROM [tabla]
WHERE [condición]
GROUP BY [columna]
HAVING [condición sobre agregados]
ORDER BY [columna o alias] [ASC|DESC];
```

---

> 🔍 **Nota:** Aunque `SELECT` también se menciona en DML, oficialmente pertenece a **DQL**, ya que consulta datos sin modificarlos.

---
