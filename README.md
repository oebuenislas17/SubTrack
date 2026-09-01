# SubTrack

## Descripción

SubTrack es un sistema que ayuda a las personas a controlar sus suscripciones, conocer cuánto gastan y recordar las fechas de sus próximos cobros.

## Problema y usuarios

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
## Alcance

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

## Tipo de sistema y restricciones

### Tipo de sistema

SubTrack es un **Sistema de Información**, ya que su función principal es registrar, consultar, modificar y organizar información relacionada con las suscripciones de los usuarios, como costos, fechas de cobro, categorías e historial.

### Atributos de calidad

| Atributo | Aplicación en SubTrack |
|---|---|
| **Usabilidad** | SubTrack debe ser fácil de entender y utilizar para registrar y consultar suscripciones. |
| **Integridad de los datos** | Los costos, fechas, estados e historial de las suscripciones deben mantenerse correctos y consistentes. |
| **Trazabilidad** | El sistema debe conservar información relevante sobre cambios, como modificaciones de precios y cancelaciones. |
| **Control de acceso** | Cada usuario podrá acceder y modificar únicamente sus propias suscripciones, mientras que el administrador tendrá permisos para gestionar información general. |

### Reglas de negocio

| Regla | Descripción |
|---|---|
| **Suscripción válida** | Una suscripción debe tener nombre, costo, fecha de próximo cobro y frecuencia de pago. |
| **Cancelación** | Una suscripción cancelada dejará de generar recordatorios de futuros cobros. |
| **Historial** | Al cancelar una suscripción, su historial se conservará. |
| **Cambio de precio** | Si cambia el precio de una suscripción, los registros anteriores conservarán su precio original. |
| **Próximo cobro** | La fecha del próximo cobro se determinará de acuerdo con la frecuencia de pago registrada. |
| **Acceso** | Un usuario solamente podrá consultar y modificar sus propias suscripciones. |

## 5. Ciclo de vida

### Modelo seleccionado: Ágil

Para el desarrollo de SubTrack se utilizará un **modelo Ágil**, ya que los requisitos pueden cambiar conforme el sistema sea desarrollado y probado por los usuarios.

Este modelo permitirá desarrollar SubTrack en pequeñas etapas, obtener retroalimentación, detectar problemas y realizar cambios sin tener que esperar hasta que todo el sistema esté terminado.

Además, las funciones podrán desarrollarse progresivamente, comenzando con las más importantes, como el registro de usuarios y suscripciones, para después incorporar el control de gastos, recordatorios e historial.

### ¿Por qué le conviene a SubTrack?

| Criterio | SubTrack |
|---|---|
| **Requisitos** | Pueden cambiar conforme se pruebe el sistema y aparezcan nuevas necesidades. |
| **Usuario/cliente** | Puede participar durante el desarrollo y dar retroalimentación sobre las funciones. |
| **Riesgo** | El principal riesgo es crear funciones que no sean útiles o fáciles de utilizar para el usuario. |
| **Evolución** | El sistema puede mejorar y agregar funciones según la experiencia y necesidades de los usuarios. |

### Alternativas descartadas

| Modelo | Razón para descartarlo |
|---|---|
| **Cascada** | Funciona mejor cuando los requisitos son estables y conocidos desde el principio. En SubTrack pueden aparecer cambios conforme los usuarios prueben el sistema. |
| **Modelo V** | Está orientado principalmente a sistemas críticos o regulados que necesitan una verificación formal. SubTrack no es un sistema crítico y utilizar este modelo agregaría procesos que no son necesarios para el alcance del proyecto. |


