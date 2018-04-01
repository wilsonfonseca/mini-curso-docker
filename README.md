# Docker Run Class

Mini curso de Docker focado em conceitos para quem está começando a conehcer o assunto;

---

## Acesso ao Material

Para instalação do Docker de acordo com sua distro verifique a documentação oficial em:

- [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)

Já a imagem com o curso pronto para acesso pode ser obitdia via Docker:

```sh
docker run -p 8080:8080 helcorin/mini-curso-docker
```

Basta rodar o projeto com export da porta 8080 para a porta local a partir da qual pretende acessar o conteúdo;

Você também pode acessar a [versão em PDF Neste Repositório](https://github.com/fiapsecdevops/mini-curso-docker/raw/master/_files/Docker-Run-Class.pdf)

---

## Como rodar o Docker?

Para executar os testes relativos a este conteúdo é necessário a execução do Docker, trata-se da aplicação que será responsável pelo processo de criação e execução de containers, o Docker está disponível para várias plataformas e pode ser instalado seguindo a documentação oficial do projeto referente ao seu sistema operacional:

[Instalação do Docker](https://docs.docker.com/install/);

**Execução em núvem:**

Esse template foi criado para lançamento de uma instância na AWS utilizando Cloud Formation, esta instância "nasce" com o Docker Community instalado na versão 17 e com acesso configurado para um usuário local;

Clique no link abaixo caso deseja utilizar este template:

[![cf-template](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/new?stackName=sandboxDocker&templateURL=https://s3.us-east-2.amazonaws.com/cf-templates-fiaplabs/dockermachine-aws-tmpl.json)

***Importante:***

Para utilizar o template é necessário acesso a uma conta válida na AWS, se for necessário o uso fora dos laboratórios de aula será necessário o cadastro de uma [Free Tier](https://aws.amazon.com/pt/free/) ou de algum outro modelo de conta disponivel. 

---

## Referências e bases para Sistemas Linux:

 - Uma opção interessante é consultar o material do [Gomex](https://github.com/gomex) publicado em seu github no repositório [docker-para-desenvolvedores](https://github.com/gomex/docker-para-desenvolvedores);

- Este projeto foi criado com base na plataforma showoff da [Puppetlabs](https://github.com/puppetlabs/showoff);

---

**Free Software, Hell Yeah!**