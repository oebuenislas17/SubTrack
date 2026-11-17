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
flowchart TD
    usuario([Usuario de SubTrack])

    subgraph sistema["SubTrack — Sistema SaaS"]
        app["Aplicación SubTrack<br/>Contenedor: monolito modular<br/>Tecnología propuesta: Node.js + Express<br/>Contiene las reglas de negocio y los módulos"]

        db[("Base de Datos<br/>Contenedor de persistencia compartida<br/>Tecnología propuesta: PostgreSQL<br/>Datos separados por usuario<br/>Historial de suscripciones y precios")]

        app -->|"SQL: lectura y escritura de datos"| db
    end

    usuario -->|"HTTPS: solicitudes a la aplicación"| app
    app -->|"HTTPS: resultados y recordatorios"| usuario
```

**Descripción**

SubTrack contiene exactamente dos contenedores: la Aplicación SubTrack y la Base de Datos. Los módulos internos permanecen dentro de la aplicación y no se despliegan como servicios independientes.

- **Usuario:** se comunica con la aplicación mediante HTTPS y no accede directamente a la base de datos.
- **Aplicación SubTrack:** es una única unidad desplegable con arquitectura de monolito modular. La tecnología propuesta es Node.js con Express y contiene las reglas de negocio y los módulos del sistema.
- **Base de Datos:** utiliza PostgreSQL como tecnología propuesta. Conserva la información compartida con separación lógica por usuario, incluidos los historiales de suscripciones y precios.
- **Límite SubTrack:** agrupa los dos contenedores del sistema.
- **Comunicación:** el usuario envía solicitudes mediante HTTPS y recibe resultados y recordatorios. La aplicación lee y escribe información en PostgreSQL mediante SQL.

*Nota: Node.js, Express y PostgreSQL son tecnologías propuestas para una futura implementación de SubTrack; actualmente se cuenta con un prototipo navegable.*

## Diagrama 3 — Componentes

```mermaid
flowchart TB
    %% Diagrama 3 — Componentes
    subgraph APP["Aplicación SubTrack — Contenedor: monolito modular"]
        subgraph MS["Módulo de Suscripciones"]
            GS["Gestión de suscripciones<br/>Registro, consulta, modificación y cancelación registrada<br/>Conservación del historial de suscripciones y precios<br/>Sujeto observable"]
        end

        subgraph MC["Módulo de Cobros"]
            GC["Gestión de cobros<br/>Consulta de gastos asociados a suscripciones"]
        end

        subgraph MP["Módulo de Próximos cobros"]
            PC["Próximos cobros<br/>Fechas de cobro y renovación<br/>Sujeto observable"]
            EF["Frecuencia de cobro<br/>Interfaz Strategy"]
            EM["Frecuencia mensual<br/>Estrategia concreta"]
            EA["Frecuencia anual<br/>Estrategia concreta"]
        end

        subgraph MR["Módulo de Recordatorios"]
            RN["Recordatorios y notificaciones<br/>Observer: observador<br/>Gestiona avisos de próximos cobros y cambios<br/>Detiene recordatorios al registrar una cancelación"]
        end
    end

    DB[("Base de Datos de SubTrack<br/>Contenedor de persistencia compartida<br/>Datos separados por usuario")]

    GS -->|Lee y conserva suscripciones e historial del usuario| DB
    GC -->|Consulta precios y frecuencias del usuario| DB
    PC -->|Consulta fechas, frecuencias y estados del usuario| DB

    PC -->|Utiliza según la frecuencia de la suscripción| EF
    EM -.->|Implementa| EF
    EA -.->|Implementa| EF

    GS -.->|Notifica cambios y cancelaciones al observador registrado| RN
    PC -.->|Notifica próximos cobros al observador registrado| RN

    classDef gestion fill:#f0fdfa,stroke:#2dd4bf
    classDef estrategia fill:#f5f3ff,stroke:#a78bfa
    classDef notificacion fill:#fff7ed,stroke:#fb923c
    classDef datos fill:#eef2ff,stroke:#818cf8
    class GS,GC,PC gestion
    class EF,EM,EA estrategia
    class RN notificacion
    class DB datos
```
Descripción
Diagrama 3 — Componentes. Amplía el contenedor Aplicación SubTrack y organiza sus responsabilidades en cuatro módulos internos. La Base de Datos permanece fuera de la aplicación como el otro contenedor ya mostrado.

| Elemento | Responsabilidad |
|---|---|
| **Suscripciones** | Registrar, consultar y modificar suscripciones; registrar cancelaciones y conservar los historiales de suscripciones y precios. |
| **Cobros** | Consultar los gastos asociados a las suscripciones; no ejecutar pagos ni cobrar dinero. |
| **Próximos cobros** | Gestionar las fechas de cobro y renovación según la frecuencia y el estado de la suscripción. |
| **Recordatorios** | Recibir avisos internos, gestionar notificaciones y detener los recordatorios de suscripciones canceladas. |
| **Interfaz Strategy** | Definir el comportamiento variable según la frecuencia de cobro. |
| **Estrategias mensual y anual** | Implementar las dos frecuencias definidas para SubTrack. |
| **Base de Datos** | Conservar la información compartida con separación lógica por usuario. |
## Imagen de Mermaid
<img width="1919" height="898" alt="image" src="https://github.com/user-attachments/assets/0ae8b813-819b-497e-b0b6-ac357cf4198a" />

## Diagrama UML — Clases
![Diagrama de clases](./doc/arch/diagrama-clases.png)

## Diagrama de secuencia

![Diagrama de secuencia](./diagrama%20de%20secuencias.png)
