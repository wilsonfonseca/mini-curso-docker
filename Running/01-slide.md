!SLIDE commandline incremental transition=scrollUp
# Rodando Comandos

Existem três 

- Execução de Comandos em Foreground;
- Execução de Comandos com interação em Foreground;
- Execução de Comandos em longos em Background;  

!SLIDE commandline incremental transition=scrollUp
# Rodando Comandos

***Execução de Comandos em Foreground:***

Começando pelo básico:

    $ docker run debian ls

.callout.info `No exemplo acima executamos um comando simples dentro do container Debian, você verá como retorno uma lista dos diretórios dentro do container, após executar a solicitação o docker devera parar o container`

!SLIDE commandline incremental transition=scrollUp
# Rodando Comandos

Após a execução você conseguirá ver o container ( Que neste momento já foi finalizado ) com o comando do docker ps -a:

    $ docker ps -a

.callout.info `Como trata-se de um container que já executou a tarefa solicitada ( um simples comando ls ) o container não mais encontra-se em execução, por isso o uso do "-a" para verificar todos os containers, inclusive os que não estão rodando`

!SLIDE commandline incremental transition=scrollUp
# Rodando Comandos

Como o comando já foi finalizado o container pode ser removido executando o comando docker rm, para isso primeiro localizar o id do container:

    $ docker ps -a
    CONTAINER ID        IMAGE               COMMAND
    8c52b4a18f3c        debian:latest       "ls"                

Depois remova o container com base em seu id:

    $ docker rm 8c52b4a18f3c

!SLIDE commandline incremental transition=scrollUp
# Rodando Comandos

É possível remover um container automaticamente após sua execução:

    $ docker run --rm debian ping google.com

.callout.info `Finalize a execução utilizando um "Ctrl^C" procure pela imagem executando um "docker ps" o ping que estava sendo executado está rodando dentro do container`

!SLIDE commandline incremental transition=scrollUp
# Rodando Comandos

***Execução de Comandos interação em Foreground:***

Outra possibilidade para a execução de comandos é o uso do formato interativo a partir da emulação de um terminal como o "bash" ou o "sh":

    $ docker run --rm -i -t debian bash

.callout.info `Ao rodar comandos no modo interativo estamos efetivamente acessando o container, neste caso a partir do comando bash`

!SLIDE commandline incremental transition=scrollUp
# Rodando Comandos

***Execução de Comandos em longos em Background:***

Finalizando é possível executar containers em Background utilizando a opção "-d" neste exemplo o container a ser executado é uma nginx:

    $ docker run -d -p 8080:80 nginx

.callount.info `A opção "-p 8080:80" refere-se ao bind da porta 8080 do host local na porta 80 do container`

.callout.info `Como o container está sendo executado em uma camada de rede criada dentro do  host hospedeiro é necessário export da porta para acesso a aplicação`

!SLIDE commandline incremental transition=scrollUp
# Listando Containers

Abra um segundo terminal, visualize a lista de containers rodando:

    $ docker ps
    CONTAINER ID     IMAGE       COMMAND                   ...
    7b058f5b8a2c     nginx...    "nginx -g 'daemon ..."    ...

A relação de parâmetros para esse comando pode ser consultada abaixo:

![docker-ls-table](images/docker-ls-table.png)


!SLIDE commandline incremental transition=scrollUp
# Exibição de Logs

É possível obter logs de containers em execução com o comando docker logs 

***sintaxe:*** docker logs ${OPTIONS} ${CONTAINER_NAME}

    $ docker logs 7b058f5b8a2c
    
.callout.info `Uma boa prática ligada ao uso de containers indica que aplicações não devem gerenciar ou rotear arquivos de log, esse logs devem ser depositados sem qualquer esquema de buffer na saída padrão (STDOUT);`

.callout.info `Fica por conta de uma infraestrutura externa à aplicação o armazenamento e gerenciamento desses dados;`