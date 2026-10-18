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
**R.G.01. Gestión de usuarios**

Como gestor,

quiero gestionar las cuentas de usuario

para organizar el acceso al sistema.

**R.G.02. Gestión de salas**

Como gestor,

quiero gestionar las salas

para mantener actualizada la información del estudio.

**R.G.03. Gestión de reservas**

Como cliente,

quiero realizar y consultar reservas

para organizar el uso del estudio.

**R.G.04. Gestión de instrumentos**

Como gestor,

quiero gestionar los instrumentos

para mantener actualizado el catálogo del estudio.

**R.G.05. Gestión de pagos**

Como gestor,

quiero gestionar los pagos

para llevar el control de los importes abonados.

**R.G.06. Gestión de cancelaciones**

Como cliente,

quiero cancelar mis reservas

cuando no pueda asistir y conocer qué ocurre con la fianza.
### 3.2. Usuarios del sistema
- Cliente: realiza reservas y puede incluir instrumentos en ellas.

- Gestor: administra la información de salas e instrumentos y supervisa las reservas.

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales
**R.F.01.01. Creación de usuario** 

Como usuario,

quiero crear una cuenta

para acceder al sistema.

**Prueba de aceptación**

- La cuenta guarda email y contraseña.
- El usuario se registra como Cliente o Gestor.

**R.F.01.02. Listado de usuarios** 

Como gestor,

quiero obtener el listado de usuarios

para organizar las cuentas del sistema.

**Prueba de aceptación**

- El listado muestra los usuarios y su tipo: Cliente o Gestor.

**R.F.01.03. Edición de usuario**  

Como usuario,

quiero editar mis datos

para mantenerlos actualizados.

**Prueba de aceptación**

- Se pueden modificar los datos disponibles de la cuenta.
- Los cambios aparecen en el listado.

**R.F.01.04. Borrado de usuario** 

Como gestor,

quiero borrar cuentas que ya no deban estar en el sistema,

para mantener actualizado el registro de usuarios.

**Prueba de aceptación**

- Se puede borrar una cuenta que no esté asociada a reservas.
- No se puede borrar una cuenta que tenga reservas asociadas.

#### Requisitos asociados a R.G.02. Gestión de salas

**R.F.02.01. Creación de sala**

Como gestor,

quiero crear salas

para incluirlas en el sistema.

**Prueba de aceptación**

- La sala guarda nombre, capacidad y precio por hora.

**R.F.02.02. Listado de salas**  

Como gestor,

quiero obtener el listado de salas

para organizar las reservas.

**Prueba de aceptación**

- El listado muestra nombre, capacidad y precio por hora de cada sala.

**R.F.02.03. Edición de sala**  

Como gestor,

quiero editar los datos de una sala

para mantenerlos actualizados.

**Prueba de aceptación**

- Se pueden modificar el nombre, la capacidad y el precio por hora.
- Los cambios aparecen en el listado.

**R.F.02.04. Borrado de sala** 

Como gestor,

quiero borrar salas que ya no se utilicen,

para mantener actualizado el catálogo de salas.

**Prueba de aceptación**

- Se puede borrar una sala que no esté asociada a reservas.
- No se puede borrar una sala que tenga reservas asociadas.

**R.F.03.01. Creación de reserva**  

Como cliente,

quiero crear una reserva

para utilizar una sala durante un periodo determinado.

**Prueba de aceptación**

- La reserva guarda el cliente, la sala, la fecha y hora de inicio, la fecha y hora de fin y el número de personas.
- El número de personas no supera la capacidad de la sala. Se aplica **R.N.02**.
- La sala no tiene otra reserva cuyo horario se solape. Se aplica **R.N.01**.
- El precio estimado se calcula como `Duración × Sala.PrecioHora`.
- La fianza se calcula como `Σ (LíneaAlquiler.Cantidad × Instrumento.ValorFianza)`.
- El precio total se calcula como `PrecioEstimado + Fianza`.

**R.F.03.02. Listado de reservas**  

Como cliente,

quiero obtener el listado de mis reservas

para organizar el uso del estudio.

**Prueba de aceptación**

- El listado muestra las reservas asociadas al cliente.
- Cada reserva muestra sala, periodo, número de personas y estado.

**R.F.03.03. Edición de reserva**

Como cliente,

quiero editar los datos de una reserva

para corregirlos o actualizarlos.

**Prueba de aceptación**

- Se pueden modificar los datos de la reserva.
- Tras la edición se siguen cumpliendo **R.N.01** y **R.N.02**.

**R.F.03.04. Borrado de reserva**  

Como cliente,

quiero borrar una reserva que ya no necesite,

para eliminarla de mis reservas.

**Prueba de aceptación**

- La reserva borrada deja de aparecer en el listado.
- También se borran las líneas de alquiler y el pago asociados a esa reserva.

**R.F.04.01. Creación de instrumento**  

Como gestor,

quiero crear instrumentos

para añadirlos al catálogo.

**Prueba de aceptación**

- El instrumento guarda nombre, categoría, stock total y valor de fianza.

**R.F.04.02. Listado de instrumentos**  

Como gestor,

quiero obtener el listado de instrumentos

para organizar el catálogo.

**Prueba de aceptación**

- El listado muestra nombre, categoría, stock total y valor de fianza.

**R.F.04.03. Edición de instrumento**  

Como gestor,

quiero editar los datos de un instrumento 

para mantenerlos actualizados.

**Prueba de aceptación**

- Se pueden modificar nombre, categoría, stock total y valor de fianza.
- Los cambios aparecen en el listado.

**R.F.04.04. Borrado de instrumento**  

Como gestor,

quiero borrar instrumentos que ya no formen parte del catálogo,

para mantener actualizado el catálogo de instrumentos.

**Prueba de aceptación**

- Se puede borrar un instrumento que no esté asociado a líneas de alquiler.
- No se puede borrar un instrumento que aparezca en líneas de alquiler

**R.F.05.01. Listado de pagos**  

Como gestor,

quiero obtener el listado de pagos

para llevar el control de los importes abonados.

**Prueba de aceptación**

- El listado muestra el monto, la fecha y la reserva asociada a cada pago.

**R.F.05.02.Realización de pago**  

Como gestor,

quiero registrar un pago

para dejar constancia del abono de una reserva.

**Prueba de aceptación**

- El pago guarda monto y fecha.
- El pago queda asociado a una reserva.

**R.F.05.03. Edición de pago**  

Como gestor,

quiero editar un pago

para corregir sus datos.

**Prueba de aceptación**

- Se pueden modificar el monto y la fecha.
- Los cambios aparecen en el listado.

**R.F.05.04. Borrado de pago** 

Como gestor,

quiero borrar un pago registrado por error,

para corregir la información de los pagos.

**Prueba de aceptación**

- El pago deja de aparecer en el listado.
- La reserva asociada se mantiene.

**R.F.06.01. Listado de cancelaciones**  

Como gestor,

quiero obtener el listado de reservas canceladas

para organizar su seguimiento.

**Prueba de aceptación**

- El listado incluye las reservas con estado `Cancelado` y su fecha y hora de cancelación.

**R.F.06.02.Realización de cancelación por el Cliente**  

Como cliente,

quiero cancelar una reserva

para comunicar que no voy a utilizar la sala.

**Prueba de aceptación**

- La reserva pasa al estado `Cancelado`.
- Al cancelarla, se registra la fecha y hora de cancelación.
- Si faltan menos de 24 horas para el inicio, la fianza queda retenida y no se devuelve. Se aplica **R.N.04**.

**R.F.06.03. Edición de cancelación**  

Como gestor,

quiero corregir la fecha y hora de una cancelación registrada,

para mantener correcta la información de la reserva cancelada.

**Prueba de aceptación**

- Se puede corregir la fecha y hora de cancelación.
- La reserva conserva el estado `Cancelado` y no vuelve a `Pendiente` ni a `Confirmado`. Se aplica **R.N.03**.

**R.F.06.04.Realización de cancelación por el Gestor**  

Como gestor,

quiero registrar una cancelación comunicada por un cliente

para mantener actualizada la reserva.

**Prueba de aceptación**

- La reserva pasa al estado `Cancelado`.
- Se registra la fecha y hora de cancelación.
- Si faltan menos de 24 horas para el inicio, la fianza queda retenida y no se devuelve. Se aplica **R.N.04**.

#### 4.1.1. Requisitos de información

**R.I.01. Información de usuarios**

Como gestor,

quiero consultar los datos de los usuarios

para identificar quién utiliza el sistema.

**Prueba de aceptación**

- Usuario guarda email y contraseña.
- Cliente guarda nombre y teléfono.
- Gestor guarda nombre y teléfono.
- Cada usuario es Cliente o Gestor.

**R.I.02. Información de salas**

Como gestor,

quiero consultar los datos de las salas 

para asignarlas a las reservas.

**Prueba de aceptación**

- Sala guarda nombre, capacidad y precio por hora.

**R.I.03. Información de reservas**

Como cliente o gestor,

quiero consultar los datos de una reserva

para conocer su periodo, estado y precio.

**Prueba de aceptación**

- Reserva guarda fecha y hora de inicio, fecha y hora de fin y número de personas.
- El estado utiliza el enum EstadoReserva, con los valores definidos en el mapa: Pendiente, Confirmado, Cancelado y Financiado.
- Si la reserva se cancela, se guarda la fecha y hora de cancelación.
- Se muestran el precio estimado y el precio total.
- La reserva está asociada al Cliente que la realizó.

**R.I.04. Información de instrumentos y líneas de alquiler**

Como gestor,

quiero consultar los instrumentos y sus cantidades reservadas 

para conocer qué incluye cada reserva.

**Prueba de aceptación**

- Instrumento guarda nombre, categoría, stock total y valor de fianza.
- Línea de alquiler guarda la cantidad del instrumento asociada a la reserva.

**R.I.05. Información de pagos**

Como gestor, 

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


