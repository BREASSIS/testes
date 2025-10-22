# 🌐 Portfólio de Projetos Sênior

```mermaid
graph TD

%% ==== CAMADAS SIMPLIFICADAS ====
subgraph CORE
    direction TB
    CoreVault[core-corevault-clean-csharp]
    GoBridge[core-gobridge-hex-go]
    PredictGo[core-predictgo-serving-go]
    SyncGate[core-syncgate-api-csharp-angular]
    CloudFlow[core-cloudflow-orchestrator-mix]
    DataForge[core-dataforge-pipeline-python]
    InsightEngine[core-insightengine-ai-python]
    EventHubX[core-eventhubx-event-go]
end

subgraph INFRA
    direction TB
    CloudWeaver[infra-cloudweaver-iac-go]
    TraceMatrix[infra-tracematrix-mesh-python]
    ResilienceLab[infra-resiliencelab-fault-csharp]
end

subgraph PROD
    direction TB
    EdgeNodeX[prod-edgenodex-edge-go]
    AtlasUI[prod-atlasui-fullstack-angular-csharp]
end

subgraph LAB
    direction TB
    PyConfigOps[lab-pyconfigops-modular-python]
    PyAutoFlow[lab-pyautoflow-pipeline-python]
end

%% ==== CONEXÕES ====
CoreVault --> CloudFlow
CoreVault --> PredictGo
CoreVault --> SyncGate
CoreVault --> InsightEngine
CoreVault --> PyAutoFlow
CoreVault --> TraceMatrix

EventHubX --> CloudFlow
EventHubX --> PredictGo
EventHubX --> PyAutoFlow
EventHubX --> InsightEngine

DataForge --> CloudFlow
PyAutoFlow --> CloudFlow
DataForge --> InsightEngine
PyAutoFlow --> InsightEngine

CloudWeaver --> CoreVault
CloudWeaver --> EdgeNodeX
TraceMatrix --> CoreVault
TraceMatrix --> EdgeNodeX
ResilienceLab --> EdgeNodeX

EdgeNodeX --> PredictGo
AtlasUI --> SyncGate
AtlasUI --> CloudFlow

PyConfigOps --> CoreVault
PyConfigOps --> CloudWeaver
PyAutoFlow --> DataForge
