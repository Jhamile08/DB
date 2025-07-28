# ¿Qué es SQL?

**SQL** (Structured Query Language) es un lenguaje de programación diseñado para **gestionar y manipular bases de datos relacionales**. Es el lenguaje estándar que utilizan los sistemas de gestión de bases de datos (SGBD) como MySQL, PostgreSQL, SQL Server, Oracle, entre otros.

---

## 🔍 ¿Para qué se utiliza SQL?

SQL permite realizar operaciones como:

- **Crear** estructuras de bases de datos (tablas, índices, vistas).
- **Insertar**, **modificar** y **eliminar** datos.
- **Consultar** información con condiciones específicas.
- **Controlar permisos** y usuarios.
- **Administrar transacciones** para asegurar integridad de los datos.

---

##  Principales comandos SQL

| Categoría | Comandos comunes                          | Descripción                                       |
|----------|-------------------------------------------|--------------------------------------------------|
| DDL      | `CREATE`, `ALTER`, `DROP`, `TRUNCATE`     | Definen y modifican estructuras de la base de datos. |
| DML      | `INSERT`, `UPDATE`, `DELETE`              | Manipulan los datos dentro de las tablas.        |
| DQL      | `SELECT`                                  | Permite consultar y leer los datos.              |
| DCL      | `GRANT`, `REVOKE`                         | Gestionan permisos de acceso.                    |
| TCL      | `COMMIT`, `ROLLBACK`, `SAVEPOINT`         | Controlan transacciones y consistencia de datos. |

** Podrás ver estos comandos a profundidad en comandos.md
---

## Ventajas de SQL

- Estándar reconocido y utilizado mundialmente.
- Fácil de aprender y entender.
- Potente para manejar grandes volúmenes de datos.
- Compatible con numerosos sistemas de bases de datos.

---

##  ¿Qué es un SGBD?

Un **Sistema de Gestión de Bases de Datos (SGBD)** es un software que permite crear, gestionar y consultar bases de datos. SQL es el lenguaje que usamos para interactuar con ellos.

### Ejemplos de SGBD:

- MySQL
- PostgreSQL
- Oracle
- SQL Server
- SQLite


## Tipos de datos comunes en SQL

```sql
| Tipo de Dato     | Descripción                                             | Ejemplo                 |
|------------------|---------------------------------------------------------|-------------------------|
| `INT`            | Número entero (positivo o negativo)                     | 42                      |
| `TINYINT`        | Entero pequeño (-128 a 127)                             | 100                     |
| `SMALLINT`       | Entero mediano (-32,768 a 32,767)                       | 1200                    |
| `MEDIUMINT`      | Entero más amplio                                       | 500000                  |
| `BIGINT`         | Entero muy grande                                       | 9223372036854775807     |
| `DECIMAL(p,s)`   | Número decimal con precisión                            | 10.99                   |
| `FLOAT`          | Número decimal de punto flotante                        | 3.1416                  |
| `DOUBLE`         | Mayor precisión que `FLOAT`                             | 2.718281828             |
| `CHAR(n)`        | Cadena de texto fija de n caracteres                    | 'ABC'                   |
| `VARCHAR(n)`     | Cadena de texto variable de hasta n caracteres          | 'Hola mundo'            |
| `TEXT`           | Texto largo                                             | 'Este es un texto...'   |
| `DATE`           | Fecha (AAAA-MM-DD)                                      | '2025-07-28'            |
| `DATETIME`       | Fecha y hora (AAAA-MM-DD HH:MM:SS)                      | '2025-07-28 15:30:00'   |
| `TIMESTAMP`      | Fecha y hora con zona UTC                              | '2025-07-28 15:30:00'   |
| `TIME`           | Hora (HH:MM:SS)                                         | '14:00:00'              |
| `BOOLEAN`        | Verdadero o falso                                       | TRUE / FALSE            |
```
## Restricciones SQL
| Restricción           | Descripción                                                                    |
|-----------------------|--------------------------------------------------------------------------------|
| `PRIMARY KEY`         | Identifica de forma única cada fila en la tabla. Solo puede haber una por tabla. |
| `FOREIGN KEY`         | Crea una relación con una columna en otra tabla.                                |
| `NOT NULL`            | No permite que el campo esté vacío.                                             |
| `UNIQUE`              | Evita que se repitan los valores en esa columna.                               |
| `DEFAULT`             | Asigna un valor por defecto si no se especifica uno.                            |
| `AUTO_INCREMENT`      | Incrementa automáticamente el valor para claves primarias numéricas.            |
| `CHECK`               | Valida que los datos cumplan una condición.                                     |
| `ON UPDATE`           | Actualiza el valor (normalmente una fecha/hora) al modificar el registro.       |
| `ON DELETE`           | Define qué hacer si un registro relacionado se elimina.                         |
| `ON UPDATE`           | Define qué hacer si un registro relacionado se actualiza.                       |


## 📘 Notaciones comunes en modelos entidad-relación

| Notación | Significado                                     | Uso común o ejemplo                             |
|----------|-------------------------------------------------|--------------------------------------------------|
| PK       | Primary Key (Clave primaria)                    | `id_usuario` identifica de forma única al usuario |
| FK       | Foreign Key (Clave foránea)                     | `id_rol` en usuarios referencia a `roles.id`     |
| N        | Muchos (en relaciones 1:N)                      | Un autor tiene N libros                          |
| 1        | Uno (en relaciones 1:N o 1:1)                   | Un país tiene 1 capital                          |
| AI       | Auto Increment                                  | `id INT AUTO_INCREMENT`                          |
| NN       | Not Null (No permite valores nulos)            | `nombre VARCHAR(50) NOT NULL`                    |
| U      | Unique (Valor único)                           | `correo UNIQUE`                                  |
| DF       | Default (Valor por defecto)                    | `estado VARCHAR DEFAULT 'activo'`                |
| CHK      | Check (Restricción de validación)              | `edad INT CHECK (edad >= 18)`                    |
| IX       | Index (Índice para mejorar consultas)          | `CREATE INDEX idx_nombre ON clientes(nombre)`    |
| 1:1      | Relación Uno a Uno                             | Un usuario tiene un solo perfil                  |
| 1:N      | Relación Uno a Muchos                          | Una categoría tiene muchos productos             |
| N:M      | Relación Muchos a Muchos                      | Muchos estudiantes en muchos cursos              |

