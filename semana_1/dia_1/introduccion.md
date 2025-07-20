# Introducción a las Bases de Datos

## 1. ¿Qué son los datos?

Los datos representan piezas de información como la edad de una persona, el nombre, la cédula, el teléfono, etc.  
Cuando se unen todas estas piezas, se forma una base de datos: un lugar donde se agrupa y organiza información completa.

## 2. ¿Por qué son importantes las bases de datos para las empresas?

Para una empresa, una base de datos no solo representa información: representa todo lo que conforma su operación.  
Allí se almacenan registros de ventas, clientes, empleados, entre otros.  
Gracias a esto, las empresas pueden responder preguntas clave:

- ¿Qué productos se están vendiendo?
- ¿Cuáles no se venden?
- ¿Qué cliente es el más frecuente?

En otras palabras: saber es poder. Con esta información, la empresa puede conocer mejor su mercado y tomar decisiones importantes.

## 3. ¿Qué pasa si solo tengo una base de datos?

Las bases de datos por sí solas solo **guardan información**.  
Para poder **manipularla, consultarla o modificarla**, necesitamos un **motor de base de datos** y un **gestor (DBMS)**.

## Analogía: la biblioteca

Imagina una **librería**:

- La **librería** representa el **motor de base de datos**.
- Es el lugar físico donde se almacenan todos los libros (los datos).
- Tiene estanterías bien organizadas, clasificaciones y etiquetas, pero por sí sola **no sabe cómo atender a las personas** ni quién puede sacar un libro.

### El motor de base de datos se encarga de:

- Guardar los libros (almacenar datos).
- Buscar libros cuando alguien los necesita (consultar).
- Agregar o quitar libros (insertar, eliminar).
- Asegurar que los libros estén en orden (integridad y eficiencia).

### El bibliotecario representa el DBMS (gestor de base de datos):

- Se comunica contigo, entiende lo que quieres y usa el sistema interno (el motor) para darte acceso al libro correcto.
- Lleva el control de quién entra, qué se presta, qué se devuelve y a quién se le permite acceder.

### El DBMS se encarga de:

- Recibir tus solicitudes y traducirlas para el motor (por ejemplo, ejecutar una consulta SQL).
- Validar si tienes permiso para hacer esa acción (seguridad).
- Mostrarte los resultados de forma comprensible.
- Llevar el control de los cambios (registro de transacciones).
- Facilitarte la interacción con el sistema (interfaz amigable o comandos).

## Recapitulación con analogía

| Elemento técnico         | Analogía en la librería           | ¿Qué representa?                                  |
|--------------------------|------------------------------------|--------------------------------------------------|
| Base de datos (BD)       | Los libros                         | La información o datos reales almacenados.       |
| Motor de base de datos   | La estructura interna de la librería | El sistema que almacena, organiza y recupera los datos. |
| DBMS (gestor)            | El bibliotecario                   | El programa que te permite interactuar con la BD.|
| Usuario o programador    | El visitante de la librería        | Quien consulta, modifica o administra la información.|

---

# Tipos de Bases de Datos – SQL y NoSQL

## ¿Cómo se organizan los datos en una base de datos?

Antes de hablar de los tipos de bases de datos, es importante entender cómo se estructuran los datos.

Imagina una tabla como una **hoja de cálculo (Excel)**:

- Las **columnas** representan los **tipos de datos** (por ejemplo: nombre, edad, dirección).
- Las **filas** representan **registros individuales** (por ejemplo: un cliente con todos sus datos).
- Cada tabla guarda un tipo de información específica: una tabla de clientes, una tabla de productos, etc.

---

## Bases de datos SQL (Structured Query Language)

Las bases de datos SQL son **estructuradas** y usan **tablas relacionadas entre sí**.  
Este modelo se llama **relacional**, porque una tabla puede conectarse con otra mediante **claves**.

### Relación entre tablas:

- **Uno a uno**: un cliente tiene una cuenta bancaria.
- **Uno a muchos**: un dueño puede tener muchas mascotas.
- **Muchos a muchos**: muchos estudiantes pueden estar en muchos cursos.

### Ejemplo práctico

Imagina una veterinaria. Podrías tener estas tablas:

**Tabla Dueños**

| ID | Nombre | Teléfono |
|----|--------|----------|
| 1  | Ana    | 123456   |

**Tabla Mascotas**

| ID | Nombre | DueñoID |
|----|--------|---------|
| 1  | Rocky  | 1       |

Aquí vemos que la dueña Ana (ID 1) tiene una mascota llamada Rocky.  
Si Ana tuviera 3 mascotas, todas estarían en la tabla **Mascotas**, con **DueñoID: 1**.

Estas relaciones permiten mantener los datos organizados, conectados y fáciles de consultar.

---

## Bases de datos NoSQL (Not Only SQL)

Las bases de datos NoSQL **no usan tablas ni relaciones tradicionales**.  
En su lugar, usan **colecciones de documentos**, que se parecen mucho a archivos en formato JSON.

### ¿Cómo se ve?

Un documento típico puede lucir así:

```json
{
  "nombre": "Ana",
  "telefono": "123456",
  "mascotas": [
    { "nombre": "Rocky", "especie": "Perro" },
    { "nombre": "Michi", "especie": "Gato" }
  ]
}
```
Todo está guardado junto en un solo documento.
No hace falta conectar varias tablas, lo cual es útil cuando los datos cambian mucho o no necesitan relaciones complejas.

# Ejemplo práctico
En la misma veterinaria, en lugar de tener dos tablas separadas, cada dueño tendría su propio documento, que incluye los datos de sus mascotas.