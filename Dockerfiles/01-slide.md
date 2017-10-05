!SLIDE center transition=scrollUp

# Dockerfiles 
![docker](images/registry.png)


!SLIDE transition=scrollUp
# Criando imagens

**Como criar um Dockerfile para entregar seu código?**

- A estratégia mais simples e eficiente para geração de uma imagem é a construção de um Dockerfile, 

- Um Dockerfile é basicamente um arquivo texto contendo uma relação de instruções de linha de comando que farão a composição da imagem de seu container;

- A imagem é baseada em uma imagem base pré existente no [Dockerhub](https://hub.docker.com/_/openjdk/), neste exemplo utilizaremos uma imagem com openjdk rodando [Alpine](https://alpinelinux.org/);

!SLIDE transition=scrollUp
# Criando imagens

Como primeiro exemplo crie um arquivo com o nome "Dockerfile";

Adicione as duas linhas abaixo e salve o conteudo;

    @@@shell
    FROM httpd:2.4
    COPY ./public-html/ /usr/local/apache2/htdocs/

.download coffe-template.zip

!SLIDE transition=scrollUp
# Criando imagens

- O processo de build é utilizado para criar uma imagem apartir de um Dockerfile;

- Neste exemplo utilizaremos uma imagem do apache com base na documentação [https://hub.docker.com/_/httpd/](https://hub.docker.com/_/httpd/);

- O Conteúdo do diretório public-html pode ser definido por você, se achar necessário utilize um [template css do w3schools](https://www.w3schools.com/w3css/tryit.asp?filename=tryw3css_templates_cafe);

!SLIDE commandline incremental transition=scrollUp
# Criando imagens

Execute o comando docker build para criar sua imagem:

    $ docker build -t my-apache2 .
    $ docker images

Teste seu novo container rodando o seguinte:

    $ docker run -dit  -p 80:80 --name my-running-app my-apache2

!SLIDE transition=scrollUp
# Executando o Upload de uma imagem

A imagem criada localmente pode ser enviada a um registry e disponibilizada para acesso de terceiros;

O Dockerhub é uma estrtura de registry publico usada para armazenamento e disponibilização de imagens;

![docker](images/dockerhub.png)

!SLIDE commandline incremental transition=scrollUp
# Executando o Upload de uma imagem

Acesse o Dockerhub pelo endereço [https://hub.docker.com/](https://hub.docker.com/) e crie uma conta gratuita;

Voltando ao o docker faça o login no registry:

    $ docker login

Crie uma nova tag para sua imagem com base em sua conta no dockerhub:

    $ docker tag helcorin/my-apache2

Em seguida faça o upload da imagem:

    $ docker push helcorin/my-apache2

.callout.info `Acesse o dockerhub novamente e verifique se a imagem foi adicionada;`

!SLIDE transition=scrollUp
# Criando uma imagem com Java

**Criando um Dockerfile:**

    @@@shell
    FROM openjdk:8-jdk-alpine
    ADD target/gs-spring-boot-docker-0.1.0.jar app.jar
    ENV JAVA_OPTS="-Xmx256m -Xms128m"
    ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -jar /app.jar" ]

Esse exemplo foi baseado no [spring.io](https://spring.io/guides/gs/spring-boot-docker/) e pode ser baixado a partir [Deste Link](https://github.com/helcorin/docker-run-class/tree/master/_files/share);

.callout.warning `Não odeixe de ajustar os valores definidos na variável JAVA_OPTS de acordo com o sizing da sua aplicação.`

!SLIDE transition=scrollUp
# Criando uma imagem com Java

Neste exemplo o Dockerfile utilizou quatro instruções:

- FROM: A instrução FROM determina qual a imagem base que será usada no Build, essa imagem pode ser qualquer imagem válida armazenada no Dockerhub ou em outra plataforma de Registry;

No exemplo anterior a imagem utilizada é uma imagem do openjdk um projeto que mantém um pacote com o Java Runtime, ela pode ser acessada diretamente no [Repositório oficial do Projeto](https://hub.docker.com/_/openjdk/) no dockerhub; 

.callout.warning `Tome um certo cuidado ao escolher quais as imagens a serem usadas em seu desenvolvimento, prefira sempre imagens oficiais de cada Projeto, verique a origem e documentação referentes que geralmente estão referenciadas na página da imagem no dockerhub`

!SLIDE transition=scrollUp
# Criando uma imagem com Java

- ADD: Utilizamos essa instrução para copiar arquivos ou diretórios de uma origem \<src\> para dentro do Filesystem da imagem sendo executada em Docker \<dest\>

Sintaxe:

ADD \<src\> ... \<dest\>

- ENTRYPOINT: Esta instrução permite a configuração do container que executará seu código e comando exato a ser executado assim que o container for carregado;

.callout.info `No exemplo anterior o arquivo copiado foi um jar gerado via maven, este arquivo foi copiado de sua origem "target/gs-spring-boot-docker-0.1.0.jar" para o destino "app.jar`

.callout.info `Em seguida com o arquivo criado no dirtetório / do container oepnjdk, utilizamos o Entrypoint para rodar o comando java -jar executando o conteudo do arquivo criado.`


!SLIDE commandline incremental transition=scrollUp
# Criando uma imagem com Java

Acesse o diretório com o Projeto de Exemplo e em seguida faça o build do Projeto:
   
    $ docker build -t hello_spring:version1.0 .

O container será disponibilizado no seu ambiente local:

    $ docker images

.callout.info `O exemplo baseia-se no modelo proposto no ***spring.io***, Você encontrará a versão completa na [Documentação do Projeto](https://spring.io/guides/gs/spring-boot-docker/#initial)`

!SLIDE commandline incremental transition=scrollUp
# Criando uma imagem com Java

Com a imagem criada podemos iniciar o container:

    $ docker run -p 8080:8080 -t hello_spring:version1.0
    
Os parâmetros mais comuns na execução de containers foram listados abaixo;

![kubernetes](images/docker-run-table.png)