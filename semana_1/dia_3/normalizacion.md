# Normalización en Bases de Datos Relacionales

La **normalización** es un proceso que se aplica al diseño de bases de datos para **organizar los datos de forma eficiente**.  
Su objetivo principal es **eliminar la redundancia**, **evitar errores** y **garantizar la integridad de los datos**.

---

## ¿Por qué es importante normalizar?

Sin normalización, podrías tener datos repetidos, inconsistentes y difíciles de mantener.  
Con normalización, divides los datos en **tablas bien estructuradas** que se relacionan entre sí, lo cual:

- Reduce la duplicación de información.
- Mejora el rendimiento y la organización.
- Facilita las actualizaciones y consultas.

---

# Formas Normales (FN)

La normalización se realiza en etapas llamadas **formas normales**.  
A continuación, explicamos las tres primeras, que son las más comunes y necesarias.

---

## Primera Forma Normal (1FN)

**Regla:**  
Cada campo debe contener **un solo valor** y no debe haber listas ni datos repetidos en una sola celda.

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

## Segunda Forma Normal (2FN)

**Regla:**  
Debe cumplir con la 1FN **y además**, **todos los atributos deben depender completamente de la clave primaria**.

> Esta regla se aplica cuando tienes una **clave primaria compuesta** (es decir, que usa **más de una columna** para identificar un registro).

### Ejemplo incorrecto (sin 2FN):

Supón esta tabla de una base de datos de cursos:

| EstudianteID | CursoID | NombreEstudiante | CursoNombre |
|--------------|---------|------------------|-------------|
| 1            | A1      | Ana              | Matemáticas |
| 2            | A1      | Pedro            | Matemáticas |

- La clave primaria compuesta sería: `(EstudianteID, CursoID)`
- El campo `NombreEstudiante` **depende solo de EstudianteID**, y `CursoNombre` **solo de CursoID**
- Por tanto, hay **dependencia parcial**, lo cual **viola la 2FN**.

### Solución (cumple 2FN):
Separar en tres tablas:

**Estudiantes**
| EstudianteID | NombreEstudiante |
|--------------|------------------|
| 1            | Ana              |
| 2            | Pedro            |

**Cursos**
| CursoID | CursoNombre |
|---------|-------------|
| A1      | Matemáticas |

**Inscripciones**
| EstudianteID | CursoID |
|--------------|---------|
| 1            | A1      |
| 2            | A1      |

Ahora cada campo depende completamente de su clave primaria.

---

## Tercera Forma Normal (3FN)

**Regla:**  
Debe cumplir con 2FN **y además**, **los atributos no deben depender de otros atributos que no sean la clave primaria**.

> Es decir, los campos **solo deben depender de la clave primaria**, y no entre ellos.

### Ejemplo incorrecto (sin 3FN):

| ProductoID | NombreProducto | Precio | Impuesto |
|------------|----------------|--------|----------|
| 1          | Pelota         | 10000  | 1900     |

Supongamos que el impuesto **siempre es el 19% del precio**.  
Entonces, el campo `Impuesto` **se puede calcular** a partir de `Precio`, y **no depende directamente del ProductoID**, lo cual **viola la 3FN**.

### Solución (cumple 3FN):

Eliminar el atributo derivado `Impuesto` y calcularlo solo cuando se necesite mediante la consulta sql

## Resumen de las Formas Normales

| Forma Normal | ¿Qué evita?                    | Reglas clave                                                                 |
|--------------|--------------------------------|------------------------------------------------------------------------------|
| 1FN          | Datos agrupados o repetidos    | Cada celda debe tener un solo valor                                         |
| 2FN          | Dependencia parcial            | Todos los campos deben depender completamente de la clave primaria compuesta |
| 3FN          | Dependencia entre atributos    | Ningún campo debe depender de otro que no sea la clave primaria             |
