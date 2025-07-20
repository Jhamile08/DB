# Pasos para Diseñar una Base de Datos Relacional

Este es un resumen estructurado de los pasos para diseñar una base de datos relacional desde cero, basado en un caso práctico de reservas de canchas deportivas.

---

## Paso 1: Entender los Requisitos

- Analiza el contexto del sistema: ¿qué se va a almacenar y por qué?
- Identifica procesos clave: ¿qué información se intercambia?
- Haz preguntas como:
  - ¿Qué datos debo guardar?
  - ¿Qué acciones realiza el usuario?
  - ¿Qué eventos necesita registrar la base de datos?
- Documenta las ideas: usa notas, esquemas o mapas mentales.

---

## Paso 2: Identificar las Entidades

- Divide la información en conceptos principales llamados **entidades**.
- Una **entidad** representa un objeto del mundo real del cual queremos guardar información.
- Ejemplos de entidades:
  - Clientes
  - Canchas
  - Reservas
  - Tipos de Canchas
- Representa las entidades en un **Diagrama Entidad-Relación (DER)**.  
  Un **DER** es un dibujo que muestra las entidades, sus propiedades (atributos), y cómo se conectan entre sí.  
  En este diagrama:
  - Las entidades se dibujan como **rectángulos**.
  - Las relaciones se conectan con líneas o rombos.
  - Los atributos se añaden como **elipses** alrededor de la entidad.

---

## Paso 3: Identificar los Atributos

- Agrega las características específicas que describen a cada entidad (por ejemplo: nombre, fecha, tipo).
- Cada **atributo** se representa como una elipse conectada a su entidad en el DER.
- Buenas prácticas al definir atributos:
  - No repitas la misma información con nombres diferentes.
  - Usa nombres claros y específicos (por ejemplo: `correo_electronico` en vez de `dato1`).
  - No incluyas atributos que se pueden calcular (como `total` si ya tienes `precio` y `cantidad`).
  - Decide qué atributos son **obligatorios** (siempre deben tener valor) y cuáles **opcionales**.

### ¿Qué es una clave primaria?

Una **clave primaria** es un atributo que **identifica de forma única** a cada registro de una entidad.  
Por ejemplo, en la entidad `Clientes`, el atributo `id_cliente` puede ser la clave primaria porque cada cliente tendrá un número diferente.

---

## Paso 4: Identificar las Relaciones

- Determina cómo se conectan las entidades entre sí.
- Para representar estas conexiones en el DER, usamos **líneas** entre entidades que indican relaciones.

### ¿Qué es una clave foránea?

Una **clave foránea** es un atributo que **conecta una entidad con otra**, copiando el valor de la clave primaria de la entidad relacionada.  
Por ejemplo, si una reserva pertenece a un cliente, en la entidad `Reservas` se guarda el `id_cliente` como clave foránea.

### Tipos de relaciones (cardinalidad):

- **1:1 (uno a uno):** Un elemento se relaciona con uno solo en otra entidad.
- **1:N (uno a muchos):** Un registro puede estar relacionado con muchos en otra entidad.
- **N:M (muchos a muchos):** Muchos registros pueden relacionarse entre sí. Se resuelve con una **tabla intermedia**.

### Ejemplos:

- Un cliente puede tener muchas reservas → relación 1:N entre `Clientes` y `Reservas`.
- Una cancha puede ser reservada varias veces → relación 1:N entre `Canchas` y `Reservas`.
- Un tipo de cancha (por ejemplo: sintética) puede aplicarse a varias canchas → relación 1:N entre `Tipos de Canchas` y `Canchas`.

---

## Paso 5: Revisión y Refinamiento

- Revisa todo tu diseño para asegurarte de que sea:
  - Claro
  - Sin repeticiones innecesarias
  - Con conexiones lógicas
- Asegúrate de:
  - Tener **entidades fuertes**, es decir, que pueden existir por sí solas (como Clientes).
  - Tener bien definidas las **entidades débiles**, que dependen de otras (como Reservas).
  - Aplicar correctamente **claves primarias** y **claves foráneas**.
- Haz ajustes si notas errores o ambigüedades.

---

## Conclusión

- Un diseño bien hecho es la base para una base de datos ordenada, eficiente y fácil de mantener.
- El **DER** te permite visualizar cómo está estructurada tu base de datos antes de implementarla en un sistema.
- Es normal que el diseño evolucione cuando surgen nuevos requerimientos.
- El siguiente paso será aplicar la **normalización**, un proceso que ayuda a reducir errores, duplicaciones y a mejorar el rendimiento.

