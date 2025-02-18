# Deploy to Amazon EKS

Este workflow utiliza **GitHub Actions** para automatizar o processo de atualização da infraestrutura no **Amazon EKS**.

---

## Pré-requisitos

- **AWS Account** com permissões para acessar o EKS.
- **DockerHub** para autenticação e pull de imagens.
- Configuração de **secrets** no repositório:
  - `AWS_ACCESS_KEY_ID`
  - `AWS_SECRET_ACCESS_KEY`
  - `DOCKERHUB_TOKEN`

---

## ⚙️ Estrutura do Workflow

O workflow realiza as seguintes etapas:

1. **Checkout do código**  
   Faz o download do código fonte do repositório.

2. **Configuração das credenciais AWS**  
   Configura as credenciais da AWS para acessar o cluster EKS.

3. **Atualização do Kubeconfig**  
   Atualiza o `kubeconfig` com as informações do cluster.

4. **Login no DockerHub**  
   Autentica no DockerHub para pull de imagens privadas, se necessário.

5. **Aplicação de ConfigMap e Secrets**  
   Aplica as configurações iniciais do Kubernetes.

6. **Deploy da aplicação**  
   Aplica o Deployment e Service YAML no cluster EKS.

---

## Trigger

O workflow é acionado nas seguintes situações:

- **Push** para a branch `main`
- **Pull Request** direcionado para a branch `main`

---

## Como usar

1. Garanta que os **secrets** estão configurados no repositório.  
2. Adicione os arquivos de configuração (YAML) na raiz do projeto.  
3. Faça **push** das alterações no repositório ou crie um **Pull Request**.  
4. O workflow será executado automaticamente.

---

## Estrutura dos arquivos

- **configmap.yaml**: Configurações da aplicação.
- **secrets.yaml**: Credenciais sensíveis.
- **app-deployment.yaml**: Deployment da aplicação.
- **app-svc.yaml**: Configuração do Service.

---

## Resultado esperado

Após a execução do workflow, a infraestrutura no cluster **Amazon EKS** será atualizada com sucesso.

---
