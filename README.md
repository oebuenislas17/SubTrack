# SubTrack

## Descripción

SubTrack es un sistema que ayuda a las personas a controlar sus suscripciones, conocer cuánto gastan y recordar las fechas de sus próximos cobros.

## Problemática

Actualmente las personas utilizan diferentes servicios de suscripción como plataformas de streaming, música, videojuegos, almacenamiento en la nube y otras aplicaciones.

Al tener varias suscripciones, puede ser difícil recordar cuánto se paga por cada una, cuándo se realizará el próximo cobro y cuáles servicios se siguen utilizando.

Esto puede provocar gastos innecesarios o cobros inesperados.

## Objetivo

Desarrollar un sistema que permita a los usuarios registrar y organizar sus suscripciones para tener un mejor control de sus gastos y fechas de pago.

## Usuarios

### Usuario

El usuario podrá:

- Registrar sus suscripciones.
- Consultar cuánto gasta.
- Consultar sus próximas fechas de cobro.
- Recibir recordatorios.
- Modificar sus suscripciones.
- Marcar suscripciones como canceladas.
- Consultar su historial.

### Administrador

El administrador podrá:

- Administrar los servicios disponibles.
- Administrar categorías.
- Mantener actualizada la información general del sistema.
- Supervisar el funcionamiento del sistema.

## Reglas de negocio

- Una suscripción debe tener un costo y una fecha de cobro.
- Una suscripción cancelada debe conservar su historial.
- Las suscripciones canceladas no deben generar nuevos recordatorios.
- Si cambia el precio de una suscripción, los pagos anteriores deben conservar su precio original.

## Alcance

SubTrack permitirá administrar y dar seguimiento a las suscripciones del usuario.

El sistema no realizará pagos reales ni cancelará directamente servicios externos.
