# SoundStudio Sevilla

## Miembros del grupo L6-DF-2 (sustituir)

1. Borreguero Rodríguez, Arturo
1. Rondán Garcíua, Eduardo
1. Soler Sánchez, Yeray
1. Alonso Montes de Oca, Gonzalo

## 1. Introducción al problema

SoundStudio Sevilla es un sistema para organizar la actividad de un estudio de música. Permite gestionar usuarios, salas, reservas, instrumentos y pagos. En una reserva se indica el periodo de uso, el número de personas, la sala asignada y, si se necesitan, los instrumentos y sus cantidades.

El sistema debe ayudar a coordinar las reservas para evitar que una sala se asigne a dos clientes en horarios que se solapen. También debe comprobar que el número de personas no supera la capacidad de la sala, calcular los importes y gestionar las cancelaciones.

Los usuarios del sistema son los clientes, que realizan reservas, y los gestores, que administran la información del estudio y supervisan su actividad.

 
<img  width="400">
<img  <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/3b4f1995-5874-4020-95f8-e32001ef0a44" />



## 2. Glosario de términos

- Cliente: usuario que realiza reservas de salas y puede incluir instrumentos.
- Fianza: cantidad calculada según los instrumentos incluidos en una reserva.
- Gestor: usuario que administra salas, instrumentos y reservas.
- Instrumento: equipo musical que puede incluirse en una reserva.
- Línea de alquiler: asociación entre una reserva y un instrumento; guarda la cantidad solicitada.
- Pago: registro del importe abonado y de la fecha del pago.
- Precio estimado: importe calculado según la duración de la reserva y el precio por hora de la sala.
- Precio total: precio estimado más la fianza.
- Reserva: solicitud de uso de una sala durante un periodo determinado.
- Sala: espacio del estudio que se asigna a una reserva.
- Stock total: cantidad total disponible de un tipo de instrumento.
- Usuario: persona con una cuenta en el sistema; puede ser Cliente o Gestor.

## 3. Visión general del sistema

### 3.1. Requisitos generales

### 3.2. Usuarios del sistema

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01. Título requisito funcional

Como [tipo de usuario]
quiero [servicio]
para [razón]

**Prueba de aceptación**
- Descripción de la primera comprobación a realizar
- Descripción de la segunda comprobación a realizar
- Se debe aplicar la regla de negocio R.N.XX.
- ...

#### 4.1.1. Requisitos de información

##### R.I.01. Título requisito de información

Como [tipo de usuario]
quiero [servicio]
para [razón]

**Prueba de aceptación**
- Descripción de la primera comprobación a realizar
- Descripción de la segunda comprobación a realizar
- ...

#### 4.1.2. Reglas de negocio
-

##### R.N.01. Título regla negocio

Descripción de la regla de negocio.

### 4.2. Mapa de historias de usuario (opcional)

### 4.3. Requisitos no funcionales (opcional)

**R.N.F. 01. Título requisito no funcional**
Como [tipo de usuario]
quiero [servicio]
para [razón]

-- fin entregable 1 --

## 5. Modelo conceptual

### 5.1. Diagramas de clases UML

- con restricciones.

### 5.2. Escenarios de prueba

- con descripción textual y diagrama de objetos UML.

## 6. Matrices de trazabilidad

- Matriz de trazabilidad entre los elementos del modelo conceptual y los requisitos.

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:------|:-----------|:-----------|:-----------|:-----------|
| RI-1  | X          | X          | X          | X          |
| RI-2  |            | X          |            | X          |
| RF-1  |            | X          |            | X          |
| RF-2  | X          |            | X          | X          |
| RN-1  |            | X          |            |            |
| RN-2  | X          | X          | X          |            |
| ...   |            |            |            |            |

-- fin entregable 2 --

## 7. Modelo relacional en 3FN

- Relaciones obtenidas al aplicar la transformación del modelo conceptual.

### 7.1.  Justificación de la estrategia de transformación de jerarquías

- si se identificaron jerarquías en el MC.


### 8. Matriz de trazabilidad MC/SQL (opcional):

- Restricciones sobre el MC / Elementos del modelo tecnológico (SQL) (Triggers, checks, etc.)
- Incluir Reglas de negocio — Constraints/Triggers en las matrices de trazabilidad para el entregable 3

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:-------|:-------|:-------|:-------|:-------|
| TABLA-1 |        |        |        |        |
| TABLA-2 |        |        |        |        |
| TABLA-3 |        |        |        |        |
| TABLA-4 |        |        |        |        |
| TRIG-1 |        |        |        |        |
| TRIG-2 | X      | X      |        | X      |
| TRIG-3 |        | X      |        | X      |
| TRIG-4 |        |        | X      |        |
| CONST-1 |        |        |        |        |
| CONST-2 | X      | X      |        | X      |
| CONST-3 |        | X      |        | X      |
| CONST-4 |        |        | X      |        |

Se consideran todo tipo de constraints declarativas (aquellas definidas durante el CREATE TABLE).
-- fin entregable 3 --

## Referencias


