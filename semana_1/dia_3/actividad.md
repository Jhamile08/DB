# Actividad 3: Aplicar la Normalización al Modelo Relacional

## Contexto

En las actividades anteriores:
- Diseñaron una base de datos identificando entidades, atributos y relaciones (Actividad 1).
- Representaron ese diseño en un **Diagrama Entidad-Relación (DER)** y lo tradujeron a un **Modelo Relacional** (Actividad 2).

Ahora, en esta tercera actividad, aprenderemos a **optimizar su modelo relacional aplicando las tres primeras formas normales (1FN, 2FN y 3FN)**.  
Esto garantizará que su base de datos esté bien estructurada, sin redundancias ni errores lógicos.

---

## Objetivo

- Analizar el modelo relacional construido en la actividad anterior.
- Aplicar correctamente la **Primera, Segunda y Tercera Forma Normal**.
- Mejorar el diseño de la base de datos eliminando duplicaciones y dependencias innecesarias.

---

## Instrucciones

### Paso 1: Verificar la Primera Forma Normal (1FN)

- Revisen que **todas las columnas de cada tabla contengan un solo valor por celda**.
- Si hay listas, valores múltiples o agrupaciones dentro de una celda, **divídanlas en varias filas**.

### Ejemplo incorrecto (sin 1FN):
| Cliente | Teléfonos         |
|---------|-------------------|
| Ana     | 3001234567, 3109876543 |

Aquí el campo "Teléfonos" contiene **dos valores en una sola celda**, lo cual viola la 1FN.

### Ejemplo corregido (cumple 1FN):
| Cliente | Teléfono     |
|---------|--------------|
| Ana     | 3001234567   |
| Ana     | 3109876543   |

---

### Paso 2: Aplicar la Segunda Forma Normal (2FN)

- Identifiquen si hay **tablas con claves primarias compuestas** (dos o más columnas como PK).
- Verifiquen que **todos los campos dependan completamente de toda la clave primaria**, no solo de una parte.
- Si detectan dependencia parcial, **separen la información en tablas distintas**.

#### Ejemplo antes de aplicar la 2FN

| EstudianteID | CursoID | NombreEstudiante | NombreCurso     |
|--------------|---------|------------------|-----------------|
| 1            | A1      | Ana              | Matemáticas     |
| 2            | A1      | Pedro            | Matemáticas     |
| 2            | B2      | Pedro            | Biología        |

- La clave primaria compuesta es `(EstudianteID, CursoID)`.
- `NombreEstudiante` depende solo de `EstudianteID`.
- `NombreCurso` depende solo de `CursoID`.
- Por lo tanto, **hay dependencias parciales**, lo que **viola la Segunda Forma Normal**.

---

#### Ejemplo después de aplicar la 2FN (normalizado)

**Tabla: Estudiantes**

| EstudianteID | NombreEstudiante |
|--------------|------------------|
| 1            | Ana              |
| 2            | Pedro            |

**Tabla: Cursos**

| CursoID | NombreCurso  |
|---------|---------------|
| A1      | Matemáticas   |
| B2      | Biología      |

**Tabla: Inscripciones**

| EstudianteID | CursoID |
|--------------|---------|
| 1            | A1      |
| 2            | A1      |
| 2            | B2      |

---

Con este diseño:

- Cada tabla tiene una clave primaria simple.
- Todos los campos dependen completamente de la clave de su tabla.
- Eliminamos la redundancia y facilitamos actualizaciones consistentes.

> Tip: Si un campo solo depende de una parte de la clave, muevelo a su propia tabla.

---

### Paso 3: Aplicar la Tercera Forma Normal (3FN)

- Revisen si **algún atributo depende de otro campo que no sea la clave primaria**.
- Si es así, eliminen esa columna y calculen su valor cuando se necesite o trasládenla a una nueva tabla.
- El objetivo es que **cada campo dependa solo de la clave primaria**.
si tienes `Precio` y `Impuesto`, y el impuesto es siempre el 19% de `Precio`, no guardes el impuesto: calcúlalo.

> Ejemplo sin normalizacion 3FN
| ProductoID | NombreProducto | Precio | Impuesto |
|------------|----------------|--------|----------|
| 1          | Pelota         | 10000  | 1900     |
| 2          | Raqueta        | 50000  | 9500     |

**Problema:**  
El campo `Impuesto` depende de `Precio`, no directamente de `ProductoID`.  
Esto viola la 3FN, ya que un atributo no debe depender de otro campo que no sea la clave primaria

> Con normalizacion
| ProductoID | NombreProducto | Precio |
|------------|----------------|--------|
| 1          | Pelota         | 10000  |
| 2          | Raqueta        | 50000  |

Ahora, si necesitas el impuesto, lo calculas desde el precio con una consulta

### Paso 4: Rediseñar el Modelo Relacional

- A partir de los ajustes en las formas normales, creen una **nueva versión del modelo relacional**, más limpia y optimizada.
- Escriban nuevamente las tablas, claves primarias y foráneas ya normalizadas.

---

## Productos esperados

Cada equipo debe entregar:

1. **Modelo relacional inicial (antes de la normalización)**.
2. **Modelo relacional final (después de aplicar 1FN, 2FN y 3FN)**.
3. Una **explicación corta (máx. 5 líneas)** de cada forma normal aplicada: qué detectaron, qué cambiaron y por qué.

---

## Evaluación

Se evaluará:

- Aplicación correcta de las tres formas normales.
- Capacidad para identificar redundancias o errores de dependencia.
- Claridad en la estructura final del modelo relacional.
- Justificación breve y comprensible de los cambios realizados.

---

Recuerda: una base de datos bien normalizada es como una casa bien construida — ordenada, firme y lista para crecer. ¡Adelante con la optimización!
