<p align="center">
  <a href="" rel="noopener">
 <img width=200px height=200px src="https://img.mandic.com.br/blog/2015/01/homepage-docker-logo.png" alt="Project logo"></a>
</p>

<h3 align="center">Módulo DevOps - Aula 01</h3>


## 📝 Conteúdo

- [Getting Started](#getting_started)
- [Comandos Linux](#comandos_linux)
- [Para lembrar](#para_lembrar)

## 🚀 PRIMEIROS PASSOS COM O DOCKER

Ao infinito e além!

## 🏁 EXECUTANDO CONTAINERS <a name = "getting_started"></a>

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See [deployment](#deployment) for notes on how to deploy the project on a live system.

### 1. Vamos criar nosso primeiro container utilizando a imagem nginx

```
    $ docker run nginx
    Veja que nesse caso criamos nosso container utilizando a imagem Nginx porém "perdemos" nosso terminal

    $ docker run -d nginx
    Veja que nesse caso criamos um container utilizando a imagem Nginx "liberando nosso terminal"
    a função "-d" informa ao Docker que queremos desatachar nosso terminal, ou seja rodar o container em backgroud e printar o ID do container

    $ docker run -d --name nginx1 nginx
    Veja que nesse caso foi criado um container utilizando a imagem Nginx e também damos um nome ao nosso container.
    A função "--name" nos possibilita nomear o container que iremos criar

    $ docker run -d -p 8080:80 --name nginx2 nginx
    Veja que nesse caso foi criado um container utilizando a imagem Nginx fazendo um "bind" da porta 8080 do nosso host (computador) e a porta (80) do container que está rodando a aplicação
    Se abrirmos o endereço http://localhost:8080 em nosso navegador iremos visualizar a página "Welcome to Nginx"
    A função "-p" permite publicar a porta do container para o nosso host

    $ docker run -it -d --name nginx3 nginx /bin/bash
    Veja que nesse caso foi criado um container utilizando a imagem Nginx de modo interativo e estaremos no terminal dentro do container
    A função -it permite criarmos um container em modo interativo passando a ação /bin/bash ou bash que permitirá estarmos dentro do container assim que ele foi criado
    ps: para sair do container podemos utilizar o comando Ctrl+D

    $ docker exec -it <ID_CONTAINER> ou <NOME_CONTAINER> bash
    Permite que executemos nosso container em modo interativo com o bash (entrar no container e utilizar o terminal)
```

### 2. Vamos listar nossos containers

```
    $ docker ps / docker container ls
    Esse comando permite visualizar todos nossos containers em execução

    $ docker ps -a / docker container ls -a 
    Esse comando permite visualizar todos os containers até mesmo os containers que não estão em execução
```

### 3. Imagens

```
    $ docker pull <NOME_DA_IMAGEM>
    Esse comando permite baixar uma imagem do DockerHub ou de um determinado repositorio
    ex: docker pull nginx (baixa a imagem oficial do Nginx no DockerHub)

    $ docker push <NOME_DA_IMAGEM>
    Esse comando faz upload de uma imagem para um repositorio
    ex: docker push minhaimagem:1.0

    $ docker image ls
    Esse comando exibe todas as imagens baixadas ou criadas localmente em nossa máquina

    $ docker image prune
    Esse comando deleta todas as imagens penduradas que estão em nossa máquina

    $ docker image prune -a 
    Esse comando deleta todas as imagens que não estão em uso em nossa máquina

    $ docker imagem rm <ID_DA_IMAGEM> / docker rmi <NOME_DA_IMAGEM>
    Esse comando deleta uma imagem

    $ docker build <DIRETORIO>
    Utilizamos esse comando para fazer um build da nossa imagem docker a partir do nosso Dockerfile
    ex: docker build minha-imagem-docker . (atenção ao "." executamos esse comando dentro do diretório onde está nossa aplicação)

    $ docker build -t <NOME_DA_IMAGEM> <NOME_DA_IMAGEM_TAG>
    Esse comando faz o build da imagem colocando uma tag a partir do nosso Dockerfile
    ex: docker build -t minha-imagem-docker

    $ docker tag <IMAGEM> <NOVA_IMAGEM>
    Esse comando coloca uma tag em uma imagem
    ex: docker tag ubuntu ubuntu:v1
```
### 4. Start/Stop de containers

```
    $ docker stop <ID_CONTAINER>
    Esse comando pausa o container que está em execução

    $ docker start <ID_CONTAINER>
    Esse comando starta o container que estava em pausa
```
### 5. Informações e Status

```
    $ docker logs <ID_CONTAINER>
    Esse comando exibe os logs do container

    $ docker stats
    Esse comando exibe o stats dos containers em execução

    $ docker top <ID_CONTAINER>
    Esse comando exibe os processos em execução do container

    $ docker inspect <NOME_CONTAINER>
    Esse comando exibe em detalhes todas as informações sobre o container

    $ docker port <ID_CONTAINER>
    Esse comando mapeia as portas de um container

    $ docker version
    Esse comando exibe a versão do Docker que está instalada em nossa máquina
```

### 6. Removendo containers

```
    $ docker rm <ID_CONTAINER> ou <NOME_CONTAINER>
    Esse comando permite remover um container

    $ docker rm -f <ID_CONTAINER> ou <NOME_CONTAINER>
    Esse comando permite remover o container em execução de modo forçado
```
## ✍️ COMANDOS BASICOS DE LINUX <a name="comandos_linux"></a>
```
    $ apt-get update
    Esse comando atualiza o banco de dados e informa ao seu sistema se há pacotes mais novos disponíveis ou não

    $ apt-get install iputils-ping -y
    Esse comando instala o "ping"
    O comando "ping" é usado para medir o tempo de resposta da conexão entre dispositivos na rede local ou Internet
    ex: ping www.google.com 

    $ apt-get install curl -y
    Esse comando instala o pacote "Curl"
    Os comandos Curl são destinados para funcionar como uma forma de verificar a conectividade da URL, além de ser uma ótima ferramenta de transferência de dados
    ex: curl www.google.com 

```

## 🎉 RELEMBRAR É VIVER!!! <a name = "para_lembrar"></a>

```
$ docker run / docker container run => Starta um novo container a partir de uma imagem Docker
$ docker run <IMAGEM> (nginx)
$ docker exec -it => Inicia o Shell dentro do container em execução
$ docker ps / docker container ls => Exibe a lista de containers sendo executados
$ docker ps -a / docker container ls -a => Exibe a lista de containers (até os containers que não estão em "Running")
$ docker rm <ID_CONTAINER> => Remove o container
$ docker rm -f <ID_CONTAINER> => Remove o container em execução (de modo forçado)
$ docker stop <ID_CONTAINER> => Para o container que está em execução
$ docker start <ID_CONTAINER => Inicia o container que estava parado
$ docker container prune => Deleta todos os containers parados
$ docker image ls => Exibe a lista de todas as imagens baixadas do registry local da máquina
$ docker image prune => Remove todas as imagens penduradas do registry local da máquina
$ docker image prune -a => Remove todas as imagens que não estão em uso do registry local da máquina
$ docker logs => Esse comando exibe os logs do container
$ docker inspect => Esse comando exibe em detalhes todas as informações sobre o container
```
