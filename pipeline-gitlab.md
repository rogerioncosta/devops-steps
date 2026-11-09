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
      - echo "build executando" # somente printa essa string
lint-job:
  stage: lint # é esse nome que conecta ao stage lint
  script:
      - echo "lint executando"
teste-job:
  stage: teste # é esse nome que conecta ao stage teste
  script:
      - echo "teste executando" # não tem projeto de teste, somente imprime essa string (`o arquivo .gitlab-ci.yml gerado pode ser incluído no projeto de teste quando houver`
```
- defina uma mensagem
- a branch
- Commit changes
<img width="733" height="546" alt="image" src="https://github.com/user-attachments/assets/6dd0c536-5113-4112-b175-cc55db4eff46" />
- se não declarar/chamar uma imagem docker pra esse build, vai setar uma padrão do git lab como runner
- toda vez que editarmos o arquivo, vai executar a pipeline toda novamente (devemos criar uma condição para executar só se o merge request for aberto e não executar toda vez que houver um o commit

### Chamando uma imagem docker como runner
- edite a pipeline
- no começo das configurações
```SHELL image: docker.io/usuario/imagem e o git vai baixar a imagem ```
- pra verificar se está chamando a imagem correta, podemos executar um comando pra verificar se dentro dela existe uma aplicação que instalamos na criação da imagem
- edite a pipe
```SHELL
build-job:
    stage: build # é esse nome que conecta ao stage build
    script:
      - appium-doctor # ao invés de printar algo, executa esse comando que verifica se tudo está configurado na imagem pra rodar o appium
```
- Lembrando que ao commitar vai rodar a pipe novamente, e isso vai acumulando builds. ### Não é aconselhável pois para empresas há cobranças
>[!NOTE] Nas empresas há o gitlab da própria empresa com uma conta empresarial. gitlab.com/ipServidorDaempresa que monta um servidor com gitlab
Nesse caso aqui é uma conta normal do gitlab
- Ao verificar os logs, deve ter registrado o comando executado
      
### Rodando a pipeline apenas quando abrir o Merge Request
**Only merge request**
```SHELL
    teste-job:
        stage: teste
        script:
            - echo "teste executando"
        only: [merge_request] ## aqui colocamos a instrução
```
### Verificando se a sintaxe das instruções estão corretas
- copie as instruções do editor
- CI/CD
- pipelines
- CI lint
- cole
- Validar

### Simulando merge request
- na pipeline
- + new branch
- defina um nome
- create from main
- create branch
- na pergunta "you pushed to develop just now" 
- clique em create merge request
- 
