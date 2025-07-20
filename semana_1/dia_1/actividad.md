# Ejercicio grupal: Pensando como una base de datos

## Objetivo

Identificar qué tipo de información necesita una empresa para operar, y cómo podría organizarse en una base de datos relacional (SQL) y documental (NoSQL).

---

## Instrucciones generales

- Formar equipos de **3 personas**.
- Cada equipo trabajará con una **temática diferente** (veterinarias, carnicerías, librerías, gimnasios, cafeterías, etc.).
- El docente asignará la temática a cada grupo.
- El equipo debe completar todos los pasos y preparar una presentación breve de sus conclusiones.

---

## Paso 1: Definir el negocio

Describan en 1 o 2 líneas qué hace su empresa.

**Ejemplo:**
> Nuestra carnicería vende productos cárnicos al detal y por encargo a domicilio.

---

## Paso 2: Pensar en los datos (Base de datos relacional - SQL)

1. Identifiquen **3 tablas** que su empresa necesitaría para funcionar.
2. Definan **mínimo 3 columnas por tabla**.
3. Indiquen si existen relaciones entre las tablas y de qué tipo (uno a uno, uno a muchos, muchos a muchos).

**Ejemplo:**

### Tablas:

- **Clientes**
  - ID (clave primaria)
  - Nombre
  - Teléfono

- **Pedidos**
  - ID
  - Fecha
  - ClienteID (clave foránea)

- **Productos**
  - ID
  - Nombre
  - Precio

### Relación:
- Un cliente puede tener muchos pedidos (relación uno a muchos).
- Un pedido puede incluir muchos productos (relación muchos a muchos, usando una tabla intermedia si es necesario).

---

## Paso 3: Pensar en los datos (Base de datos NoSQL)

1. Simulen cómo guardarían la información de un cliente y sus datos relacionados en un solo documento (como en MongoDB).
2. Representen un ejemplo en formato JSON.

**Ejemplo:**

```json
{
  "cliente": {
    "nombre": "Ana",
    "telefono": "123456",
    "pedidos": [
      { "fecha": "2024-07-20", "producto": "Carne molida", "cantidad": 2 },
      { "fecha": "2024-07-22", "producto": "Chorizo", "cantidad": 1 }
    ]
  }
}
```
## Paso 4: Conclusión del equipo
Responda brevemente:

- ¿Qué ventaja tiene guardar los datos en tablas?
- ¿Qué ventaja tiene tener todo junto en un documento?
- ¿Qué sistema sería mejor para su negocio y por qué?

## Entregables
Cada equipo debe entregar:

- Nombre del negocio.
- Listado de 3 tablas con sus columnas y relaciones (modelo SQL).
- Un ejemplo de documento en JSON (modelo NoSQL).
- Respuestas del paso 4.