## Pipeline com git lab

```MERMAID
flowchart TD
    A[Abrir um Merge Request] --> B
    B[stages: Build] --> C
    C[stages: Lint] --> D
    D[stages: Rodar Testes] --> E
    E[ação (build job): Guardar Relatórios no build] --> F
    F[ação (build job): Enviar Resultado] --> G
    G[ação (build job): chat slack]
```
- Acessar projetos para ver os repositórios
- Criar novo projeto em branco
- Criar projeto
- Set up CI/CD
- Configurar pipeline
- Caso trave por não ter um plano pro, cadastre os dados de pagamento para liberar. (A princípio não será cobrado nada)
- Vai aparecer a tela de editor de configurações para gerar o arquivo .yml
  1. declarar os stages (fluxos que vão existir na build) que no caso aqui são Lints e Rodar Testes
  2. declarar os build-job (ações) com scripts (comandos de terminal para executar)

```SHELL
stages:
  - build
  - lint
  - teste
build-job:
  stage: build # é esse nome que conecta ao stage build
  script:
      - echo "build executando"
lint-job:
  stage: lint # é esse nome que conecta ao stage lint
  script:
      - echo "lint executando"
teste-job:
  stage: teste # é esse nome que conecta ao stage teste
  script:
      - echo "teste executando"
```
- defina uma mensagem
- a branch
- Commit changes
<img width="733" height="546" alt="image" src="https://github.com/user-attachments/assets/6dd0c536-5113-4112-b175-cc55db4eff46" />



  

