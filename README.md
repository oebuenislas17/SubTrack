# SubTrack

## Descripción

SubTrack es un sistema que ayuda a las personas a controlar sus suscripciones, conocer cuánto gastan y recordar las fechas de sus próximos cobros.

## 2. Problema y usuarios

Actualmente, las personas pueden tener varias suscripciones contratadas al mismo tiempo y perder fácilmente el control de cuánto están gastando, cuándo se realizará cada cobro o incluso olvidar que siguen pagando por un servicio que ya no utilizan.

Sin SubTrack, las personas tienen que revisar sus estados de cuenta, consultar cada servicio por separado, utilizar recordatorios en su celular o simplemente tratar de recordar las fechas de sus pagos. Esto puede provocar cobros inesperados y gastos en servicios que ya no utilizan.

### Usuarios del sistema

| Tipo de usuario | ¿Quién es? | ¿Qué necesita? |
|---|---|---|
| **Usuario** | Persona que tiene una o varias suscripciones. | Registrar sus suscripciones, consultar cuánto gasta, conocer sus próximas fechas de cobro y recibir recordatorios. |
| **Administrador** | Persona encargada de mantener organizada la información general de SubTrack. | Administrar los servicios y categorías, mantener la información actualizada y evitar datos incorrectos o duplicados. |

### Necesidades en conflicto

| Usuario | Necesidad |
|---|---|
| **Usuario** | Quiere tener libertad para registrar y modificar la información de sus suscripciones. |
| **Administrador** | Necesita mantener controlada y organizada la información general para evitar datos incorrectos o duplicados. |

**Decisión de diseño:** cada usuario podrá modificar libremente sus propias suscripciones, pero solo el administrador podrá modificar la información general de servicios y categorías.
## 3. Alcance

SubTrack permitirá a los usuarios registrar y administrar sus suscripciones en un solo lugar, consultar sus próximos cobros y conocer cuánto dinero destinan a estos servicios.

Para mantener el proyecto dentro de un alcance realista, se establece lo siguiente:

| Sí incluye | No incluye |
|---|---|
| Registro e inicio de sesión de usuarios. | Realizar pagos desde SubTrack. |
| Registrar suscripciones. | Cancelar directamente una suscripción con el proveedor. |
| Modificar y marcar suscripciones como canceladas. | Acceder a cuentas bancarias de los usuarios. |
| Registrar costo, fecha y frecuencia de pago. | Detectar automáticamente cargos bancarios. |
| Clasificar suscripciones por categorías. | Modificar cuentas de servicios externos. |
| Mostrar próximos cobros. | Controlar los precios establecidos por servicios externos. |
| Generar recordatorios de próximos pagos. | Contratar nuevas suscripciones desde SubTrack. |
| Consultar el historial de suscripciones. | Administrar métodos de pago reales. |
| Calcular el gasto total en suscripciones. | Realizar reembolsos de suscripciones. |
| Administrar servicios y categorías. | Garantizar la disponibilidad de servicios externos. |

