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

SubTrack se enfocará en ayudar a los usuarios a organizar y controlar sus suscripciones, sus fechas de cobro y el dinero que destinan a ellas. El sistema funcionará como una herramienta de seguimiento y organización, por lo que no realizará operaciones directamente con bancos o proveedores externos.

| Sí incluye | Queda fuera |
|---|---|
| Registro e inicio de sesión de usuarios. | Realizar pagos desde SubTrack. |
| Registrar suscripciones. | Cancelar directamente una suscripción con el proveedor. |
| Modificar y marcar suscripciones como canceladas. | Acceder a cuentas bancarias de los usuarios. |
| Registrar costo, fecha y frecuencia de pago. | Detectar automáticamente cargos bancarios. |
| Clasificar suscripciones por categorías. | Modificar cuentas de servicios externos. |
| Mostrar los próximos cobros. | Contratar nuevas suscripciones desde SubTrack. |
| Generar recordatorios de próximos cobros. | Administrar métodos de pago reales. |
| Consultar el historial de suscripciones. | Realizar reembolsos. |
| Calcular el gasto total en suscripciones. | Garantizar los precios de servicios externos. |

### Razón de una exclusión

SubTrack no tendrá acceso directo a cuentas bancarias ni realizará pagos porque esto aumentaría considerablemente la complejidad y los riesgos de seguridad del sistema. El objetivo principal del proyecto es ayudar al usuario a organizar y controlar sus suscripciones, no funcionar como una aplicación bancaria.

