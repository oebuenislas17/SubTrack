# ADR-001: Monolito modular en lugar de microservicios

## Estado

Aceptada, 29 de octubre de 2026

## Contexto

SubTrack es un sistema SaaS para gestionar suscripciones digitales. El sistema permite registrar, consultar, modificar y cancelar suscripciones, consultar gastos, gestionar próximos cobros y conservar el historial de suscripciones y precios.

La aplicación requiere organizar diferentes responsabilidades, como suscripciones, cobros, próximos cobros y recordatorios. También necesita manejar reglas de negocio para las frecuencias de cobro mensual y anual y para los recordatorios relacionados con cambios y próximos cobros.

## Decisión

Construimos SubTrack como un **monolito modular**: una sola aplicación desplegable que contiene los módulos de Suscripciones, Cobros, Próximos cobros y Recordatorios, con una base de datos compartida y separación lógica de los datos por usuario.

Dentro de la aplicación se utilizarán límites entre módulos para mantener separadas sus responsabilidades. Para las frecuencias de cobro se utiliza el patrón Strategy, mientras que para los cambios y próximos cobros se utiliza el patrón Observer para gestionar los avisos internos.

## Consecuencias

El sistema tendrá un solo despliegue y una estructura más sencilla de desarrollar, probar y mantener. Los módulos permiten organizar las responsabilidades sin introducir servicios independientes.

Los módulos no podrán escalarse ni desplegarse de manera independiente. Además, la base de datos es compartida, por lo que se debe mantener la separación lógica de los datos correspondientes a cada usuario.

Si en el futuro el sistema crece lo suficiente como para requerir despliegues o escalamiento independientes, los límites definidos entre los módulos permitirán evaluar una posible separación en servicios independientes.
