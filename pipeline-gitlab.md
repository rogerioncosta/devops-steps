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
- 1 declarar os stages (fluxos que vão existir na build) que no caso aqui são Lints e Rodar Testes

