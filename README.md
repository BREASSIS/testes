flowchart TD
    %% Camadas principais do ResilienceLab

    subgraph TARGET["Target Services / Modules ⚫"]
        CoreVault["CoreVault Service"]
        PredictGo["PredictGo Service"]
        SyncGate["SyncGate Service"]
    end

    subgraph APPLICATION["Application / Microservice 🟠"]
        AppController["Experiment Controller"]
        APIGateway["API / gRPC Gateway"]
    end

    subgraph FAULTS["Fault Injector Core 🔵"]
        Policies["Policies Module"]
        Simulation["Simulation Module"]
        Observability["Observability Module"]
    end

    subgraph METRICS["Metrics & Logging 🟣"]
        Prometheus["Prometheus Metrics"]
        Loki["Loki Logs"]
        Tracing["OpenTelemetry Traces"]
    end

    subgraph REPORTS["Reports UI (Angular / Grafana) 🟢"]
        Dashboard["Grafana Dashboard / Angular UI"]
    end

    %% Fluxo de comunicação

    Dashboard -->|visualiza métricas| Prometheus & Loki & Tracing
    Prometheus & Loki & Tracing -->|coleta de dados| Observability
    AppController -->|orquestra falhas| Policies & Simulation
    Policies & Simulation -->|injetam falhas| CoreVault & PredictGo & SyncGate
    Observability -->|exporta métricas/logs| Prometheus & Loki & Tracing
    APIGateway -->|distribui comandos| AppController
