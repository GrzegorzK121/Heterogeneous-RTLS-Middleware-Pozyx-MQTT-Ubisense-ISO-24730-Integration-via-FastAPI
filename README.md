flowchart TB
    %% Styling
    classDef hardware fill:#1e293b,stroke:#334155,stroke-width:2px,color:#fff
    classDef parser fill:#3b82f6,stroke:#2563eb,stroke-width:2px,color:#fff
    classDef engine fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#fff
    classDef output fill:#10b981,stroke:#059669,stroke-width:2px,color:#fff
    classDef storage fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#fff
    classDef logic fill:#334155,stroke:#475569,stroke-width:2px,color:#fff

    subgraph Hardware_Layer [Hardware Layer]
        P[Pozyx System]:::hardware -->|MQTT / JSON payload| R1(MQTT Subscriber):::parser
        U[Ubisense System]:::hardware -->|UDP / Binary stream| R2(UDP Datagram Protocol):::parser
    end

    subgraph Data_Ingestion [Data Ingestion & Preprocessing]
        R1 --> P1[JSON Parser & Dynamic Offsetting]:::parser
        R2 --> P2[Struct Unpack & Static Offsetting]:::parser
        P1 --> CS[(In-Memory Current State)]:::storage
        P2 --> CS
    end

    subgraph Core_Fusion [Core Fusion Engine Loop]
        CS --> TO{Timeout Check < 1.5s}:::logic
        TO --> ZL{Zone Validation Logic}:::logic
        ZL -->|X < 20m| Z1[Pozyx Exclusive Zone]:::engine
        ZL -->|X > 23.5m| Z2[Ubisense Exclusive Zone]:::engine
        ZL -->|20m < X < 23.5m| Z3[Weighted Average Fusion]:::engine
        Z1 --> VTS[Virtual Tag State Calculation]:::engine
        Z2 --> VTS
        Z3 --> VTS
    end

    subgraph Distribution [Data Distribution & Export]
        VTS --> WSM((WebSocket Manager)):::output
        VTS --> DR[(Data Recorder)]:::storage
        WSM --> F1[Live Web Corridors HTML5]:::output
        WSM --> F2[Vertical Mobile Maps]:::output
        DR --> C1[Continuous CSV Logging]:::storage
        DR --> C2[ML Raw Data Record]:::storage
    end
