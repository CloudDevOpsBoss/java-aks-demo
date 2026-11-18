# Java-end-to-end-project

Enterprise Project Stack
| Layer        | Technology                     |
| ------------ | ------------------------------ |
| Source Code  | Azure Repos / GitHub           |
| Language     | Java 17                        |
| Framework    | Spring Boot 3                  |
| Build Tool   | Gradle                         |
| Database     | MySQL 8                        |
| Code Quality | SonarQube                      |
| CI/CD        | Azure DevOps                   |
| Container    | Docker                         |
| Registry     | Azure Container Registry (ACR) |
| Kubernetes   | Azure Kubernetes Service (AKS) |
| Monitoring   | Prometheus                     |
| Dashboard    | Grafana                        |
| Logging      | Azure Monitor / ELK (optional) |


End-to-End Architecture

                  Developer
                      │
                Git Push (main)
                      │
              Azure Repos / GitHub
                      │
             Azure DevOps Pipeline
                      │
        ┌───────────────────────────────────────┐
        │ Checkout Source Code                  │
        │ Gradle Clean Build                    │
        │ Unit Tests                            │
        │ SonarQube Code Analysis               │
        │ Build Docker Image                    │
        │ Push Image to Azure Container Registry│
        └───────────────────────────────────────┘
                      │
                Azure Kubernetes Service
          ┌──────────────┬──────────────┐
          │              │              │
     Spring Boot      MySQL         Prometheus
          │                             │
          └──────────────┬──────────────┘
                         │
                     Grafana
                         │
                    Application Metrics



Project Structure

hello-gradle-project/

├── build.gradle
├── settings.gradle
├── Dockerfile
├── azure-pipelines.yml
├── sonar-project.properties
├── src/
│   ├── main/java/
│   ├── main/resources/
│   └── test/java/
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── ingress.yaml
│   ├── mysql-deployment.yaml
│   ├── mysql-service.yaml
│   └── configmap.yaml
└── monitoring/
    ├── prometheus.yaml
    └── grafana-dashboard.json




# Docker build
docker build -t java-demo:v1 .

docker images

docker run -d -p 8080:8080 --name java-app java-demo:v1
http://localhost:8080
http://localhost:8080/health
                    
