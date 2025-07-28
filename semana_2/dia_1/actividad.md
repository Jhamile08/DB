# 🧙 Mini Taller SQL – Gremio “Espada y Pizza”

##  Enunciado

El gremio de aventureros **“Espada y Pizza”** está modernizando su sistema. Hasta ahora, anotaban todo en hojas sueltas, y perdieron la cuenta de cuántas misiones fallaron por no llevar registro.

Tu misión es diseñar una base de datos que permita:

- Registrar aventureros con su clase y nivel.
- Administrar misiones con dificultad y recompensa.
- Llevar control de qué misiones ha hecho cada aventurero y con qué resultado.

---

##  Actividades

### 1. Crear la estructura de la base de datos (DDL)

Diseña y crea todas las tablas necesarias para representar correctamente la información del gremio. Asegúrate de pensar bien en las relaciones entre entidades.

---

### 2. Insertar datos (DML)

Agrega al menos:

- 3 aventureros  
- 3 misiones  
- Varios registros de qué misiones han hecho los aventureros (con diferentes resultados)

---

### 3. Consultas (DQL)

Responde las siguientes preguntas usando `SELECT`:

Responde las siguientes preguntas usando SELECT:

    ¿Qué aventurero ha completado más misiones con éxito?
    ¿Cuál es la misión más popular?
    ¿Cuánto oro ha ganado cada aventurero?
    ¿Qué aventurero ha fallado más misiones?
    ¿Cuántas misiones ha realizado cada aventurero, sin importar el resultado?
    ¿Cuál es el promedio de recompensa de todas las misiones completadas con éxito?
    ¿Cuál es la misión con mayor recompensa?
    ¿Cuántos aventureros hay por clase (guerrero, mago, etc.)?
    ¿Quiénes son los aventureros con nivel mayor o igual a 10?
    ¿Hay misiones que aún no han sido asignadas a ningún aventurero?

---

### 4. Seguridad básica (DCL)

- Crea un usuario llamado `aprendiz_mago` que **solo pueda consultar las misiones**, pero **no pueda modificarlas**.

---

Entregable:
- Debes entregar el modelo relacional y el codigo sql en donde se evidencie la creacion de la BD, las tablas y las consultas