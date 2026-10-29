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
