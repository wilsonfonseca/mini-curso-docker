!SLIDE center transition=scrollUp

# Debbuging
![docker](images/debbuging-logo.png)

!SLIDE commandline incremental transition=scrollUp
# DOCKER PS

Os containers em execução podem ser listados utilizando o comando docker ps: 

    $ docker ps
	CONTAINER ID        IMAGE           COMMAND          	 ...	NAMES
	b4dcd19a02be        nginx:latest    "nginx -g 'daemon"   ...	pensive_mirzakhani

.callout.info `Neste exemplo existe apenas um container rodando o Nginx em execução`

!SLIDE transition=scrollUp
# Pull de Imagens

Outra categoria de erros muito comuns são erros relacionados ao pull de imagens:

- Em situações onde estiver ocorrendo erros no processo de pull de imagem uma mensagem similar a mensagem abaixo será apresentada:

    @@@shel
    Unable to find image 'ubuntu:test' locally
    docker: Error response from daemon: manifest for ubuntu:test not found.
    See 'docker run --help'.

.callout.warning `Verificar o caminho para imagem do container e as permissões de acesso no Registry ( Em nosso caso o Dockerhub ) pode ser um bom começo para entender esse erro`

.callout.info  `Outro processo útil é executar o pull manualmente em outro host utilizando docker, não se esqueça que, caso o repositório seja privado um token de autenticação será necessário para executar o pull da imagem`

!SLIDE commandline incremental transition=scrollUp
# Verificação de Logs

Dentro das pods é possível verificar logs de containers de forma similar ao processo executado via Docker logs:

***sintaxe:***

	$ docker logs ${CONTAINER_NAME}

***Exemplo:***

	$ docker logs hello_spring:version1.0


!SLIDE commandline incremental transition=scrollUp
# Executando Comandos

Em alguns cenários pode ser necessário atuar dentro da Pod, esse processo pode ser executado via "docker exec":**

	$ docker exec -it ${CONTAINER_NAME} {COMMAND}

***Exemplo:***opção

	$ docker exec -it hello_spring:version1.0 ls

.callout.info `Substitua o /bin/sh pelo comando a ser executado dentro do container, caso a Pod possua apenas um container a  -c ${CONTAINERNAME} pode ser omitida`