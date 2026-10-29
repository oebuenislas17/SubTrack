## Diagrama 1 — Contexto

```mermaid
flowchart LR
    %% Diagrama 1 — Contexto
    U["Usuario de SubTrack"]
    S["SubTrack<br/>Sistema SaaS de gestión de suscripciones digitales"]

    U -->|Registra y administra manualmente sus propias suscripciones| S
    S -->|Muestra suscripciones, gastos, próximos cobros e historial; entrega recordatorios| U

    classDef persona fill:#eef2ff,stroke:#818cf8
    classDef sistema fill:#f0fdfa,stroke:#2dd4bf
    class U persona
    class S sistema
```
Descripción
Se mantiene únicamente al Usuario de SubTrack y al sistema SubTrack, sin tecnologías ni sistemas externos.
- Usuario de SubTrack: ingresa y administra manualmente sus propias suscripciones.
- SubTrack: permite consultar suscripciones, gastos, próximos cobros e historial y recibir recordatorios.
- Relaciones: representan las acciones del usuario y la información que devuelve el sistema; no establecen un canal específico de notificación.

## Diagrama 2 — Contenedores

```mermaid
flowchart LR
    %% Diagrama 2 — Contenedores
    U["Usuario de SubTrack"]

    subgraph ST["SubTrack — Sistema SaaS"]
        APP["Aplicación SubTrack<br/>Contenedor: monolito modular<br/>Concentra las reglas de negocio"]
        DB[("Base de Datos<br/>Contenedor de persistencia compartida<br/>Datos separados por usuario<br/>Historial de suscripciones y precios")]
    end

    U -->|Registra, modifica y consulta sus propios datos| APP
    APP -->|Presenta resultados y recordatorios| U
    APP -->|Lee y escribe datos del usuario correspondiente| DB

    classDef persona fill:#eef2ff,stroke:#818cf8
    classDef modulo fill:#f0fdfa,stroke:#2dd4bf
    classDef datos fill:#f5f3ff,stroke:#a78bfa
    class U persona
    class APP modulo
    class DB datos
```
Descripción
Diagrama 2 — Contenedores. SubTrack contiene exactamente dos contenedores: la Aplicación SubTrack y la Base de Datos. Los módulos internos no aparecen como aplicaciones desplegables independientes.
- Usuario: se comunica con la aplicación, no directamente con la base de datos.
- Aplicación SubTrack: es una única unidad desplegable que contiene todos los módulos y las reglas de negocio.
- Base de Datos: conserva la información de los usuarios en un modelo compartido, con separación lógica por usuario, incluidos los historiales de suscripciones y precios.
- Límite SubTrack: agrupa los dos contenedores del sistema.
- Comunicación: el usuario opera mediante la aplicación y esta accede a los datos correspondientes. No se especifican protocolos ni tecnologías.
