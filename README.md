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

### Modelo seleccionado: Cascada

Para el desarrollo de SubTrack se utilizará el **modelo Cascada**, ya que el proyecto cuenta con un alcance definido y los requisitos principales pueden establecerse antes de comenzar el desarrollo.

Este modelo permitirá trabajar de manera ordenada y secuencial, completando cada etapa antes de continuar con la siguiente. Primero se definirán los requisitos del sistema, después se realizará el diseño, posteriormente el desarrollo y las pruebas, hasta llegar a la entrega del producto final.

### ¿Por qué le conviene a SubTrack?

| Criterio | SubTrack |
|---|---|
| **Requisitos** | Los requisitos principales pueden definirse y documentarse antes de comenzar el desarrollo. |
| **Alcance** | El sistema tiene un alcance delimitado, enfocado en el registro y control de suscripciones. |
| **Riesgo** | El proyecto presenta un riesgo técnico relativamente bajo y utiliza funciones conocidas. |
| **Organización** | Permite avanzar de forma ordenada, terminando y documentando cada etapa antes de pasar a la siguiente. |

### Etapas del desarrollo

| Etapa | Aplicación en SubTrack |
|---|---|
| **1. Requisitos** | Definir las necesidades de los usuarios, requisitos funcionales, no funcionales y reglas de negocio. |
| **2. Diseño** | Diseñar la estructura del sistema, interfaces y base de datos. |
| **3. Implementación** | Desarrollar las funciones definidas para SubTrack. |
| **4. Pruebas** | Verificar que cada requisito se cumpla y corregir los errores encontrados. |
| **5. Entrega y mantenimiento** | Entregar el sistema terminado y realizar correcciones necesarias posteriormente. |

### Alternativas descartadas

| Modelo | Razón para descartarlo |
|---|---|
| **Ágil** | Está orientado a proyectos con requisitos cambiantes y retroalimentación continua. En SubTrack se busca definir previamente el alcance y los requisitos principales antes de comenzar el desarrollo. |
| **Prototipado** | Es más conveniente cuando los requisitos son difíciles de definir y es necesario experimentar constantemente con la interfaz. En SubTrack las funciones principales y el alcance pueden establecerse desde las primeras etapas. |

## 6. Requisitos

### Requisitos funcionales

| ID | Requisito |
|---|---|
| **RF-01** | El sistema permitirá al usuario registrar una suscripción indicando nombre del servicio, costo, frecuencia de pago y fecha del próximo cobro. |
| **RF-02** | El sistema generará un recordatorio para cada suscripción activa antes de la fecha del próximo cobro, según el periodo de anticipación configurado por el usuario. |
| **RF-03** | El sistema calculará y mostrará el gasto mensual total del usuario a partir de sus suscripciones activas y su frecuencia de pago. |
| **RF-04** | El sistema permitirá al usuario marcar una suscripción activa como cancelada. |
| **RF-05** | El sistema conservará el historial de una suscripción después de que sea marcada como cancelada. |

### Requisitos no funcionales

| ID | Atributo | Requisito |
|---|---|---|
| **RNF-01** | Control de acceso | El sistema deberá impedir que un usuario consulte o modifique suscripciones pertenecientes a otro usuario. |
| **RNF-02** | Usabilidad | El usuario deberá poder registrar una suscripción completando como máximo cuatro campos obligatorios. |
| **RNF-03** | Integridad de datos | El sistema deberá rechazar el registro de una suscripción cuando el costo ingresado sea menor o igual a cero. |



