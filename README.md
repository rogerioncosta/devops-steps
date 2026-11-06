# docker-steps 2022
## Baixar uma imagem (definições do que precisa no projeto, como apps e frameworks), e subir ela em um container (estância criada e executada na máquina) no docker hub que vai rodar a imagem
- Executar container
- Através dele a imagem é montada
- baixar imagem pronta
- subir ela em um container/estância em nossa máquina
- acessar o container
- modificar o container
- por commit sobe a imagem em nossa conta do docker hub

## Passos para instalar uma imagem e rodar um container
- Entrar no docker hub e pesquisar pela imagem pronta do aplicativo a ser baixado (baixar com a tag "DOCKER OFFICIAL IMAGE")
- no terminal
- colar o comando de instalação "docker pull appium/appium" (exemplo do app appium)
- no docker desktop
- imagem: vemos a imagem baixada
- run
- run (configs depois)
- em containers deve estar running

## Analisar a imagem e o seu conteúdo e instalar apps adicionais
- listando containers em execução em minha máquina: docker ps -a com nome aleatório devido não configuração inicial
- copie o NAME
- Executar o docker no container a seguir: docker exec -it NOMEDOCONTAINER /bin/bash
- root@CONTAINERID:~# devemos estar dentro do container para verificar seu conteúdo e modifica-lo
- verificar se tem o app instalado e sua versão: appium -v
- no caso aqui somente o appium não resolve, pois para testes automatizados mobile, é necessário outros programas para rodar como java_home, android_home e node
- npm -v, node -v
- para verificar se tudo está ok e instalado para um projeto com appium, é necessário o appium doctor
- rode appium-doctor dentro da imagem (se não tiver instalado, precisamos instalar dentro do container e não em nossa máquina principal. Após instalar tudo o que falta, enviamos o container para o docker hub)
- npm install appium-doctor -g
- appium-doctor verifica se o container tem tudo pra funcionar ou não
`Se deletar o container, quando subir um novo, vai vir zerado`




