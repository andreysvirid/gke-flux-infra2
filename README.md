### 1. Что нужно сделать (Flowchart)

```mermaid
flowchart TD
    A[Разработчик коммитит код] --> B[GitHub репозиторий]
    B --> C[Настроить HelmRelease для kbot]
    C --> D[GitHub Actions: build Docker image]
    D --> E[Push образ в DockerHub]
    E --> F[Обновить HelmRelease в GitHub]
    F --> G[FluxCD подтягивает изменения]
    G --> H[GKE: приложение kbot обновлено]