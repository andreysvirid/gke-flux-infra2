### 1. Що потрібно зробити (Flowchart)

```mermaid
flowchart TD
    A[Розробник комітить код] --> B[GitHub репозиторій]
    B --> C[Налаштувати HelmRelease для kbot]
    C --> D[GitHub Actions: build Docker image]
    D --> E[Push образ у DockerHub]
    E --> F[Оновити HelmRelease у GitHub]
    F --> G[FluxCD підтягує зміни]
    G --> H[GKE: застосунок kbot оновлено]
2. Як це працює (Sequence diagram)
mermaid
Копировать код
sequenceDiagram
    participant Dev as Developer
    participant GH as GitHub
    participant Actions as GitHub Actions
    participant Docker as DockerHub
    participant Flux as FluxCD
    participant GKE as GKE Cluster

    Dev->>GH: Push code / HelmRelease changes
    GH->>Actions: Trigger workflow
    Actions->>Docker: Build & push Docker image
    Actions->>GH: Update HelmRelease with new image tag
    GH->>Flux: Commit new HelmRelease
    Flux->>GKE: Apply manifests
    Docker->>GKE: Provide image for Deployment
    GKE-->>Dev: kbot app updated