# resumo-devops-6

## build_spec.yaml

O arquivo build_spec.yaml é um arquivo de configuração usado no serviço OCI DevOps (Oracle Cloud Infrastructure DevOps) — especificamente nas etapas de build pipeline.

### 💡 Função principal:

Ele define as instruções do processo de build, ou seja, descreve como o código deve ser compilado, testado e empacotado durante a execução do pipeline de build gerenciado pela OCI.

### 📘 Em outras palavras:

É o equivalente ao buildspec.yml do AWS CodeBuild ou ao arquivo Jenkinsfile do Jenkins.

### 🧩 Estrutura típica do build_spec.yaml:

```yaml

version: 0.1
component: build
timeoutInSeconds: 600
shell: bash

env:
  variables:
    BUILD_ENV: "prod"

steps:
  - type: Command
    name: "Install dependencies"
    command: |
      mvn clean install

  - type: Command
    name: "Run tests"
    command: |
      mvn test

outputArtifacts:
  - name: build_artifact
    type: BINARY
    location: target/myapp.jar

```

## 📦 OCI Container Registry

O que é:

- Registro de containers Docker
- Armazena imagens Docker prontas para execução
- Similar ao Docker Hub, mas privado na OCI

Uso:

```bash
docker push syd.ocir.io/tenancy/myapp:v1.0
docker pull syd.ocir.io/tenancy/myapp:v1.0
```

Relacionamento:

- Fonte de imagens para OKE, Container Instances
- Destino de builds do OCI DevOps


