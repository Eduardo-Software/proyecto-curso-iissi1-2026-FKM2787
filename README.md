# SoundStudio Sevilla

## Miembros del grupo L6-DF-2 

1. Borreguero Rodríguez, Arturo
1. Rondán García, Eduardo
1. Soler Sánchez, Yeray
1. Alonso Montes de Oca, Gonzalo

## 1. Introducción al problema

SoundStudio Sevilla es un sistema para organizar la actividad de un estudio de música. Permite gestionar usuarios, salas, reservas, instrumentos y pagos. En una reserva se indica el periodo de uso, el número de personas, la sala asignada y, si se necesitan, los instrumentos y sus cantidades.

El sistema debe ayudar a coordinar las reservas para evitar que una sala se asigne a dos clientes en horarios que se solapen. También debe comprobar que el número de personas no supera la capacidad de la sala, calcular los importes y gestionar las cancelaciones.

Los usuarios del sistema son los clientes, que realizan reservas, y los gestores, que administran la información del estudio y supervisan su actividad.

 
<img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/3736c4ef-fb25-4803-aee4-62be701508f1" />  <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/3b4f1995-5874-4020-95f8-e32001ef0a44" />




## 2. Glosario de términos

- Fianza: cantidad calculada según los instrumentos incluidos en una reserva.
- Línea de alquiler: asociación entre una reserva y un instrumento; guarda la cantidad solicitada.
- Precio estimado: importe calculado según la duración de la reserva y el precio por hora de la sala.
- Precio total: precio estimado más la fianza.
- Reserva: solicitud de uso de una sala durante un periodo determinado.
- Sala: espacio del estudio que se asigna a una reserva.
- Stock total: cantidad total disponible de un tipo de instrumento.

  
  <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/95ee859f-bb81-43ea-9ecc-c515d64334c9" /> <img width="350" height="200" alt="image" src="https://github.com/user-attachments/assets/93b0d14a-bf96-498e-8176-6db89fd9a546" />



## 3. Visión general del sistema

### 3.1. Requisitos generales
**R.G.01. Gestión de usuarios**. 

Como usuario, 

quiero acceder al sistema con mi cuenta 

para utilizar las funciones correspondientes a mi tipo de usuario.

**R.G.02. Gestión de salas**. 

Como gestor, 

quiero mantener la información de las salas

para utilizarlas en las reservas.

**R.G.03. Gestión de reservas**. 

Como cliente, 

quiero realizar y consultar reservas 

para organizar el uso del estudio.

**R.G.04. Gestión de instrumentos**. 

Como gestor, 

quiero mantener la información de los instrumentos 

para conocer sus características y su valor de fianza.

**R.G.05. Gestión de pagos y cancelaciones**. 

Como gestor, 

quiero registrar pagos y cancelaciones 

para llevar el control económico de las reservas.

### 3.2. Usuarios del sistema
- Cliente: realiza reservas y puede incluir instrumentos en ellas.

- Gestor: administra la información de salas e instrumentos y supervisa las reservas.

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales
**R.F.01. Acceso de usuarios**

Como usuario 

quiero acceder con mi email y contraseña 

para utilizar el sistema según mi perfil.

**Prueba de aceptación**

- El usuario accede con el email y la contraseña registrados.
- El usuario es Cliente o Gestor, según su tipo en el sistema.

**R.F.02. Gestión de salas e instrumentos**

Como gestor 

quiero registrar y modificar la información de salas e instrumentos 

para mantener actualizado el catálogo del estudio.

**Prueba de aceptación**

- Una sala guarda nombre, capacidad y precio por hora.
- Un instrumento guarda nombre, categoría, stock total y valor de fianza.
- Solo un Gestor puede crear o modificar la información de salas e instrumentos. Se aplica **R.N.03.**

**R.F.03. Creación de una reserva**

Como cliente 

quiero reservar una sala indicando el periodo y el número de personas 

para organizar el uso del estudio.

**Prueba de aceptación**

- La reserva guarda la fecha y hora de inicio, la fecha y hora de fin y el número de personas.
- La reserva queda asociada al Cliente que la realiza.
- El número de personas no supera la capacidad de la sala. Se aplica **R.N.02.**
- La sala no tiene otra reserva con un periodo de uso solapado. Se aplica **R.N.01**.

**R.F.04. Inclusión de instrumentos en una reserva**

Como cliente 

quiero indicar los instrumentos y las cantidades que necesito 

para usarlos durante mi reserva.

**Prueba de aceptación**

- Cada instrumento incluido queda relacionado con la reserva mediante una línea de alquiler.
- La línea de alquiler guarda la cantidad solicitada.

**R.F.05. Cálculo de los importes**

Como cliente 

quiero conocer los importes de mi reserva 

para saber cuánto cuesta.

**Prueba de aceptación**

- La duración se calcula restando la fecha y hora de inicio a la fecha y hora de fin.
- El precio estimado se calcula multiplicando la duración por el precio por hora de la sala.
- La fianza se calcula según las cantidades de instrumentos y sus valores de fianza.
- El precio total se calcula sumando el precio estimado y la fianza.

**R.F.06. Registro del pago**

Como gestor 

quiero registrar el pago asociado a una reserva 

para mantener constancia del importe abonado.

**Prueba de aceptación**

- El pago guarda el monto y la fecha.
- El pago queda asociado a una reserva.

**R.F.07. Cancelación de una reserva**

Como cliente 

quiero cancelar mi reserva 

para comunicar que ya no utilizaré la sala.

**Prueba de aceptación**

- Al cancelar, la reserva pasa al estado Cancelado.
- Se registra la fecha y hora de cancelación. Se aplica R.N.03.
- Una reserva cancelada no puede volver a Pendiente ni a Confirmado. Se aplica **R.N.04.**
- Si faltan menos de 24 horas para el inicio, la fianza queda retenida y no se devuelve. **Se aplica R.N.05.**

#### 4.1.1. Requisitos de información

**R.I.01. Información de usuarios**

Como gestor 

quiero consultar los datos de los usuarios

para identificar quién utiliza el sistema.

**Prueba de aceptación**

- Usuario guarda email y contraseña.
- Cliente guarda nombre y teléfono.
- Gestor guarda nombre y teléfono.
- Cada usuario es Cliente o Gestor.

**R.I.02. Información de salas**

Como gestor

quiero consultar los datos de las salas 

para asignarlas a las reservas.

**Prueba de aceptación**

- Sala guarda nombre, capacidad y precio por hora.

**R.I.03. Información de reservas**

Como cliente o gestor 

quiero consultar los datos de una reserva

para conocer su periodo, estado y precio.

**Prueba de aceptación**

- Reserva guarda fecha y hora de inicio, fecha y hora de fin y número de personas.
- El estado utiliza el enum EstadoReserva, con los valores definidos en el mapa: Pendiente, Confirmado, Cancelado y Financiado.
- Si la reserva se cancela, se guarda la fecha y hora de cancelación.
- Se muestran el precio estimado y el precio total.
- La reserva está asociada al Cliente que la realizó.

**R.I.04. Información de instrumentos y líneas de alquiler**

Como gestor 

quiero consultar los instrumentos y sus cantidades reservadas 

para conocer qué incluye cada reserva.

**Prueba de aceptación**

- Instrumento guarda nombre, categoría, stock total y valor de fianza.
- Línea de alquiler guarda la cantidad del instrumento asociada a la reserva.

**R.I.05. Información de pagos**

Como gestor 

quiero consultar los pagos 

para conocer el importe abonado y cuándo se realizó.

**Prueba de aceptación**

- Pago guarda el monto y la fecha.
- El pago está asociado a una reserva.
- La fianza asociada se calcula a partir de los instrumentos y las cantidades incluidas en la reserva.
#### 4.1.2. Reglas de negocio
**R.N.01. Sin solapamiento de salas**

Una misma sala no puede estar asignada a dos reservas cuyos periodos de uso se solapen.

**R.N.02. Límite de capacidad de la sala**

El número de personas de una reserva no puede superar la capacidad de la sala asignada.

**R.N.03. Registro de la fecha de cancelación**

Si una reserva está en estado Cancelado, debe tener registrada su fecha y hora de cancelación. Si no está cancelada, ese dato debe quedar vacío.

**R.N.04. Reserva cancelada no reactivable**

Una reserva cuyo estado sea Cancelado no puede volver a los estados Pendiente ni Confirmado.

**R.N.05. Penalización por cancelación**

Si una reserva se cancela con menos de 24 horas de antelación, la fianza queda retenida y no se devuelve.

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


