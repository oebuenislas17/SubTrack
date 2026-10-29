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
