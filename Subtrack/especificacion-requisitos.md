------------------------------------------------------------------------

# Especificación de requisitos

**Sistema:** SubTrack  
**Autor:** Omar Enrique Buenrostro Islas  
**Versión:** 1.0  
**Fecha de la última actualización:** 28 de septiembre de 2026


------------------------------------------------------------------------

**Propósito del documento:**

Este documento define los requisitos funcionales y no funcionales de SubTrack. Su propósito es establecer de manera clara y verificable las funciones, restricciones y atributos de calidad que deberá cumplir el sistema durante su desarrollo.

**Alcance del sistema:**

SubTrack permitirá a los usuarios registrar y administrar sus suscripciones en un solo lugar. El sistema permitirá consultar próximos cobros, conocer los gastos relacionados con suscripciones y generar recordatorios.

El sistema incluirá:

- Registro y administración de suscripciones.
- Registro de costo, frecuencia de pago y fecha del próximo cobro.
- Consulta de próximos cobros.
- Cálculo del gasto total mensual y anual en suscripciones.
- Recordatorios configurables de próximos cobros.
- Administración de servicios y categorías.
- Control de acceso a la información de cada usuario.

**Fuera del alcance:**

- Realizar pagos desde SubTrack.
- Cancelar directamente una suscripción con un proveedor externo.
- Acceder a cuentas bancarias del usuario.
- Detectar automáticamente cargos bancarios.
- Contratar servicios externos desde SubTrack.
- Realizar reembolsos.
- Administrar métodos de pago reales.
- Conservar suscripciones canceladas dentro del historial de suscripciones activas.

El acceso a cuentas bancarias y la realización de pagos quedan fuera del alcance porque SubTrack tiene como objetivo organizar y dar seguimiento a las suscripciones, no funcionar como una aplicación bancaria.



------------------------------------------------------------------------

## 2. Usuarios y su contexto

| Usuario | Qué hace hoy sin el sistema | Qué espera del sistema |
|---|---|---|
| **Usuario** | Revisa diferentes aplicaciones, correos o movimientos de su tarjeta para conocer cuánto está gastando y cuándo será el siguiente cobro. | Tener sus suscripciones organizadas en un solo lugar, consultar sus próximos cobros, elegir cuándo recibir recordatorios y conocer su gasto total mensual y anual. |
| **Administrador** | La información general de servicios y categorías debe mantenerse organizada por separado. | Mantener organizada y actualizada la información general utilizada por SubTrack. |

### Contexto identificado durante la entrevista

La entrevista permitió confirmar que el usuario necesita controlar sus suscripciones sin tener que consultar diferentes aplicaciones, correos o movimientos bancarios.

También se confirmó que el usuario quiere elegir con cuánta anticipación recibir un recordatorio y considera suficientes el nombre, costo, frecuencia y próximo cobro para registrar una suscripción.

Durante la entrevista se identificó que el usuario no desea conservar las suscripciones canceladas en el historial porque podrían confundirse con las suscripciones que siguen activas.

Además, surgió la necesidad de mostrar cuánto dinero se gastó en total durante el mes y contemplar también el gasto anual.

### Conflictos identificados entre usuarios

El usuario necesita libertad para registrar y modificar sus propias suscripciones, mientras que el administrador necesita mantener controlada y organizada la información general del sistema.

Por esta razón, cada usuario tendrá control sobre sus propias suscripciones y el administrador tendrá permisos para gestionar la información general de servicios y categorías.



------------------------------------------------------------------------

## 3. Requisitos funcionales

### 3.1 Resumen

| ID | Nombre | Prioridad | Origen |
|---|---|---|---|
| **RF-001** | Registrar una suscripción | Imprescindible | Visión del producto / Entrevista 22/09/2026 |
| **RF-002** | Programar recordatorios de cobro | Importante | Entrevista 22/09/2026 |
| **RF-003** | Consultar gasto mensual | Imprescindible | Entrevista 22/09/2026 |
| **RF-004** | Cancelar el seguimiento de una suscripción | Imprescindible | Visión del producto / Entrevista 22/09/2026 |
| **RF-005** | Consultar gasto anual | Importante | Entrevista 22/09/2026 |

### 3.2 Fichas

#### RF-001 · Registrar una suscripción

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permitirá al usuario registrar una suscripción indicando nombre del servicio, costo, frecuencia de pago y fecha del próximo cobro. |
| **Origen** | Visión del producto y entrevista con usuario, 22/09/2026. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al ingresar nombre, costo mayor a cero, frecuencia de pago y fecha del próximo cobro, la suscripción queda registrada y puede ser consultada posteriormente. Si falta alguno de los cuatro datos, el sistema no guarda la suscripción. |
| **Relacionado con** | RNF-USA-001, RNF-INT-001, RNF-ACC-001 |

#### RF-002 · Programar recordatorios de cobro

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permitirá al usuario elegir con cuánta anticipación desea recibir un recordatorio antes del próximo cobro de una suscripción activa. |
| **Origen** | Entrevista con usuario, 22/09/2026. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al establecer un periodo de anticipación para una suscripción activa, el sistema genera el recordatorio antes de la fecha de cobro según el periodo seleccionado. |
| **Relacionado con** | RF-001, RF-004, RNF-INT-001 |

#### RF-003 · Consultar gasto mensual

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema calculará y mostrará el gasto total realizado por el usuario en sus suscripciones durante el mes consultado. |
| **Origen** | Necesidad identificada durante la entrevista con usuario, 22/09/2026. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al consultar un mes, el sistema muestra un total que corresponde a la suma de los costos de las suscripciones consideradas para ese periodo. |
| **Relacionado con** | RF-001, RF-005, RNF-INT-001 |

#### RF-004 · Cancelar el seguimiento de una suscripción

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema permitirá al usuario marcar una de sus suscripciones activas como cancelada dentro de SubTrack. |
| **Origen** | Visión del producto y entrevista con usuario, 22/09/2026. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al marcar una suscripción como cancelada, esta deja de aparecer entre las suscripciones activas y deja de generar recordatorios de próximos cobros. Esta acción no cancela el servicio directamente con el proveedor externo. |
| **Relacionado con** | RF-002, RNF-TRZ-001, RNF-ACC-001 |

#### RF-005 · Consultar gasto anual

| Campo | Contenido |
|---|---|
| **Descripción** | El sistema calculará y mostrará el gasto total realizado por el usuario en sus suscripciones durante el año consultado. |
| **Origen** | Necesidad identificada durante la entrevista con usuario, 22/09/2026. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al consultar un año, el sistema muestra el total correspondiente a los gastos de suscripciones registrados durante ese periodo. |
| **Relacionado con** | RF-001, RF-003, RNF-INT-001 |         

------------------------------------------------------------------------

## 4. Requisitos no funcionales

### 4.1 Resumen

| ID | Atributo | Nombre | Prioridad | Origen |
|---|---|---|---|---|
| **RNF-USA-001** | Usabilidad | Registro sencillo de suscripciones | Importante | Tipo de sistema / Entrevista |
| **RNF-INT-001** | Integridad de los datos | Validación de datos de suscripción | Imprescindible | Tipo de sistema / Entrevista |
| **RNF-INT-002** | Integridad de los datos | Validación del costo | Imprescindible | Entrevista 22/09/2026 |
| **RNF-TRZ-001** | Trazabilidad | Registro correcto del estado de suscripción | Importante | Tipo de sistema |
| **RNF-ACC-001** | Control de acceso | Separación de información por usuario | Imprescindible | Tipo de sistema |

### 4.2 Fichas

### Usabilidad

#### RNF-USA-001 · Registro sencillo de suscripciones

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Usabilidad |
| **Descripción** | El registro básico de una suscripción requerirá cuatro campos obligatorios: nombre, costo, frecuencia de pago y próximo cobro. |
| **Métrica** | Número de campos obligatorios para registrar una suscripción: 4. |
| **Origen** | Derivado del atributo de usabilidad y confirmado durante la entrevista del 22/09/2026. |
| **Prioridad** | Importante |
| **Por qué importa** | La entrevista confirmó que estos cuatro datos son suficientes para registrar una suscripción sin solicitar información adicional innecesaria. |
| **Afecta a** | RF-001 |

### Integridad de los datos

#### RNF-INT-001 · Validación de datos obligatorios

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Integridad de los datos |
| **Descripción** | El sistema rechazará el registro de una suscripción si falta alguno de los cuatro datos obligatorios. |
| **Métrica** | 100% de los intentos de registro con al menos un campo obligatorio vacío deberán ser rechazados. |
| **Origen** | Derivado del atributo de integridad de los datos y de la entrevista del 22/09/2026. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Los cálculos de gastos y recordatorios dependen de que la información necesaria esté completa. |
| **Afecta a** | RF-001, RF-002, RF-003, RF-005 |

#### RNF-INT-002 · Validación del costo

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Integridad de los datos |
| **Descripción** | El sistema rechazará el registro de una suscripción cuyo costo sea menor o igual a cero. |
| **Métrica** | 100% de los intentos de registro con costo menor o igual a cero deberán ser rechazados. |
| **Origen** | Entrevista con usuario, 22/09/2026. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | La entrevista confirmó que las suscripciones registradas deben tener un costo mayor a cero. |
| **Afecta a** | RF-001, RF-003, RF-005 |
### Trazabilidad

#### RNF-TRZ-001 · Registro correcto del estado de suscripción

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Trazabilidad |
| **Descripción** | El sistema mantendrá identificado el estado actual de cada suscripción como activa o cancelada mientras esta permanezca registrada en el sistema. |
| **Métrica** | 100% de las suscripciones registradas deberán tener un estado identificable como activa o cancelada. |
| **Origen** | Derivado del tipo de sistema de información y del atributo de trazabilidad. |
| **Prioridad** | Importante |
| **Por qué importa** | Permite diferenciar las suscripciones que deben generar próximos cobros y recordatorios de aquellas que fueron canceladas. |
| **Afecta a** | RF-002, RF-004 |

### Control de acceso

#### RNF-ACC-001 · Separación de información por usuario

| Campo | Contenido |
|---|---|
| **Atributo de calidad** | Control de acceso |
| **Descripción** | Un usuario no podrá consultar ni modificar las suscripciones pertenecientes a otro usuario. |
| **Métrica** | 100% de los intentos de acceso a suscripciones pertenecientes a otro usuario deberán ser rechazados. |
| **Origen** | Derivado del tipo de sistema de información y del atributo de control de acceso. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | La información de las suscripciones debe permanecer separada entre las diferentes cuentas del sistema. |
| **Afecta a** | RF-001, RF-002, RF-003, RF-004, RF-005 |           

------------------------------------------------------------------------

## 5. Casos de uso

| ID | Caso de uso | Actor | Requisitos relacionados |
|---|---|---|---|
| **CU-01** | Registrar una suscripción | Usuario | RF-001 |
| **CU-03** | Consultar sus suscripciones | Usuario | RF-001, RF-004 |
| **CU-04** | Cancelar el seguimiento de una suscripción | Usuario | RF-004 |
| **CU-05** | Consultar los próximos cobros | Usuario | RF-002 |
| **CU-06** | Consultar sus gastos en suscripciones | Usuario | RF-003, RF-005 |
| **CU-07** | Programar recordatorios de cobro | Usuario | RF-002 |

------------------------------------------------------------------------

## 6. Trazabilidad

| Requisito | Origen | Caso de uso | Elemento del prototipo |
|---|---|---|---|
| **RF-001** | Visión del producto / Entrevista 22/09/2026 | CU-01 Registrar una suscripción | Formulario de registro de suscripción |
| **RF-002** | Entrevista 22/09/2026 | CU-07 Programar recordatorios de cobro | Configuración de recordatorios |
| **RF-003** | Entrevista 22/09/2026 | CU-06 Consultar sus gastos en suscripciones | Resumen de gasto mensual |
| **RF-004** | Visión del producto / Entrevista 22/09/2026 | CU-04 Cancelar el seguimiento de una suscripción | Detalle de suscripción |
| **RF-005** | Entrevista 22/09/2026 | CU-06 Consultar sus gastos en suscripciones | Resumen de gasto anual |
| **RNF-USA-001** | Tipo de sistema / Entrevista | CU-01 | Formulario de registro |
| **RNF-INT-001** | Tipo de sistema / Entrevista | CU-01 | Validación del formulario |
| **RNF-INT-002** | Entrevista 22/09/2026 | CU-01 Registrar una suscripción | Validación del costo |
| **RNF-TRZ-001** | Tipo de sistema | CU-04 | Estado de suscripción |
| **RNF-ACC-001** | Tipo de sistema | CU-01, CU-03, CU-04, CU-05, CU-06, CU-07 | Control de acceso del usuario |

------------------------------------------------------------------------

## 7. Registro de cambios

| Fecha | Requisito | Qué cambió | Por qué |
|---|---|---|---|
| 22/09/2026 | RF-002 | Se confirmó que el usuario podrá elegir la anticipación de los recordatorios. | Supuesto confirmado durante la entrevista. |
| 22/09/2026 | RF-001 | Se confirmaron nombre, costo, frecuencia y próximo cobro como datos necesarios para registrar una suscripción. | Supuesto confirmado durante la entrevista. |
| 22/09/2026 | RF-005 anterior | Se descartó conservar las suscripciones canceladas en el historial. | El entrevistado indicó que podría confundirlas con las suscripciones activas. |
| 22/09/2026 | RF-003 | Se especificó la consulta del gasto total mensual. | Necesidad identificada durante la entrevista. |
| 22/09/2026 | RF-005 | Se agregó la consulta del gasto total anual. | Necesidad identificada durante la entrevista. |
| 29/09/2026 | Documento completo | Se actualizó la especificación a la versión 1.1. | Incorporación de los resultados de la entrevista de elicitación. |
                                   

------------------------------------------------------------------------

## Antes de entregar

-   [ ] Todos los requisitos tienen identificador único y ninguno está
    repetido
-   [ ] Cada requisito expresa una sola idea
-   [ ] Cada requisito funcional tiene criterio de aceptación
    comprobable
-   [ ] Cada requisito no funcional tiene una métrica, no solo un
    adjetivo
-   [ ] El campo Origen distingue lo confirmado por el cliente de lo que
    sigo suponiendo
-   [ ] Hay al menos un requisito no funcional por cada atributo de
    calidad que impone mi tipo de sistema
-   [ ] Ningún requisito impone una solución técnica
-   [ ] Todos los requisitos caben dentro del alcance declarado
-   [ ] La tabla de trazabilidad está completa
-   [ ] Mi dupla revisó el documento y su revisión está registrada
-   [ ] Borré los ejemplos y las instrucciones en cursiva
