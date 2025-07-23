# Actividad 2: Construcción del DER y del Modelo Relacional

## Contexto

En la **actividad anterior**, cada equipo diseñó la estructura lógica de una base de datos relacional, identificando las entidades, sus atributos y las relaciones entre ellas.  
Ahora, en esta segunda actividad, **vamos a representar gráficamente esa estructura** en dos niveles:

1. Un **Diagrama Entidad-Relación (DER)** conceptual.
2. Su equivalente técnico: el **Modelo Relacional**.

Esto les permitirá visualizar cómo se conecta cada parte del sistema, y prepararse para crear físicamente la base de datos más adelante.

---

## Objetivo

- Aplicar los conceptos aprendidos sobre diseño de bases de datos.
- Construir el **DER** y el **Modelo Relacional** a partir de los datos obtenidos en la actividad 1.
- Comprender la diferencia entre representación conceptual (DER) y representación técnica (Modelo Relacional).

---

## Instrucciones

### Paso 1: Dibujar el Diagrama Entidad-Relación (DER)

- Representen **cada entidad** como un rectángulo.
- Agreguen los **atributos** como elipses conectadas a su entidad.
- Subrayen el atributo que será la **clave primaria (PK)**.
- Si hay **relaciones** entre entidades, represéntenlas con rombos.
- Usen conectores para mostrar la **cardinalidad** de cada relación (1:1, 1:N, N:M).

**Recomendación de herramienta:** [https://draw.io](https://draw.io)

---

### Paso 2: Construir el Modelo Relacional

- Para cada entidad del DER, escriban su **tabla equivalente** con los siguientes elementos:
  - Nombre de la tabla.
  - Lista de columnas (atributos).
  - Indicación de la **clave primaria**.
  - Indicación de **claves foráneas**, si existen.


### Paso 3: Crear la base de datos y tablas en mysql

- Vamos crear nuestra base de datos y nuestras tablas a traves de la terminal
**Formato sugerido:**

```sql
Tabla: Clientes
- id_cliente (PK)
- nombre
- correo
- telefono

Tabla: Reservas
- id_reserva (PK)
- fecha
- hora_inicio
- hora_fin
- id_cliente (FK)
- id_cancha (FK)
```
## Productos esperados
Cada grupo debe entregar:

- Imagen o archivo del Diagrama Entidad-Relación (DER).
- Lista o tabla del Modelo Relacional correspondiente.
- Una breve explicación escrita (máx. 5 líneas) de cómo conectaron ambas representaciones.

## Evaluación
Se evaluará:

- Claridad del DER (entidades, atributos, relaciones bien representadas).
- Coherencia entre el DER y el modelo relacional.
- Uso correcto de claves primarias y foráneas.
- Presentación limpia y ordenada.


ejemplo de sql:
` ` `  sql
-- Tabla de libros
CREATE TABLE libros (
    id INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(255) NOT NULL,
    autor VARCHAR(100),
    anio_publicacion INT
);

-- Tabla de usuarios
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    correo VARCHAR(100) UNIQUE
);

-- Tabla de préstamos (relaciona usuarios con libros)
CREATE TABLE prestamos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    fecha_prestamo DATE NOT NULL,
    fecha_devolucion DATE,
    libro_id INT,
    usuario_id INT,
    FOREIGN KEY (libro_id) REFERENCES libros(id),
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id)
);
` ` ` 
