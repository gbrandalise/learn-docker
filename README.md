# learn-docker

## CLI
`docker version`

docker = comando padrão do cli
version = exibe a versão do cli e do daemon do docker

### Parâmetros padrões

<IMAGE_NAME> = nome da imagem
[TAG] = parâmetro opcional da tag atribuída a imagem, geralmente a versão
<CONTAINER_NAME> = nome do container

### Criando container
`docker run -d --name <CONTAINER_NAME> [-p] [HOST_PORT]:[CONTAINER_PORT] [--link] [<ANOTHER_CONTAINER_NAME>] [-v] [HOST_PATH]:[CONTAINER_PATH] <IMAGE_NAME>:[TAG]`

run = comando para criar um container

-d = roda o container em background

--name = flag para indicar o nome do container que será criado

[-p] = flag opcional para mapear as portas expostas pelo container com portas do host (podem ser substituidos por apenas -P maiúsculo, indicando que todas as portas expostas pelo container serão mapeadas para as mesmas portas no host)

[HOST_PORT] = porta do host que responderá pela porta do container

[CONTAINER_PORT] = porta exposta do container que será mapeada na porta do host

[--link] = flag usada para indicar links entre os containers, para que um possa enxergar o outro

[ANOTHER_COTNAINER_NAME] = nome do outro container que ficará acessível

[-v] = flag usada para mapear diretórios expostos pela imagem para o host

[HOST_PATH] = diretório que será mapeado no host

[CONTAINER_PATH] = diretório no container que é exposto pela imagem e que será usado para mapear em um diretório no host

ex.: `docker run -d --name primeiro_container -p 38080:8080 -v c:\Users\admin\tomcat_logs:/home/tomcat/webapps tomcat:latest`

### Listando containers
`docker ps [-a]`

ps = comando para listar os containers

[-a] = parâmetro opcional para listar todos os containers incusive os que estão parados

### Listando imagens
`docker images`

images = exibe as imagens do repositório local

### Baixando uma imagem
`docker pull <IMAGE_NAME>:[TAG]`

pull = baixa uma imagem de um repositório público ou privado

ex.: docker pull ubuntu:18.04

### Inspecionando informações de um container
`docker inspect <CONTAINER_NAME>`

inspect = inspeciona informações do container

ex.: docker inspect container_apache

### Parar um container
`docker stop <CONTAINER_NAME>`

stop = parar um container

ex.: docker stop apache

### Iniciar um container
`docker start <CONTAINER_NAME>`

start = iniciar um container

ex.: docker start artifactory

### Entrar em um container
`docker attach <CONTAINER_NAME>`

attach = entra em um container

ex.: docker attach debian

### Exibir alterações realizadas em um container
`docker diff <CONTAINER_NAME>`

diff = exibe as alterações realizadas no container

ex.: docker diff tomcat

### Exibir help de um comando
`docker <COMMAND> --help`

<COMMAND> = comando do docker cli

--help = exibe o help do comando

ex.: docker run --help

### Criando uma imagem a partir de um container
`docker commit <CONTAINER_NAME> <NEW_IMAGE_NAME>:[TAG]`

commit = commita uma imagem a partir de um container

<CONTAINER_NAME> = container base para criação da imagem

<NEW_IMAGE_NAME> = nome da imagem que será criada

ex.: docker commit apache/minha_imagem apache

### Removendo um container
`docker rm <CONTAINER_NAME>`

rm = removendo um container

ex.: docker rm meu_container

### Removendo uma imagem
`docker rmi <IMAGE_NAME>:[TAG]`

rmi = removendo uma imagem

ex.: docker rmi ubuntu:18.06

### Criando imagem a partir de um Dockerfile
`docker build [-t] [IMAGE_NAME]:[TAG] <DOCKERFILE_PATH>`

build = comando usado para criar uma imagem a partir de um Dockerfile

[-t] = flag opcional para indicar o nome e a tag da imagem a ser criada

<DOCKERFILE_PATH> = diretório em que se encontra o Dockerfile, pode-se usar . (ponto) se o arquivo estiver no diretório atual

### Exibir histório de comandos de uma imagem
`docker history <IMAGE_NAME>`

history = exibe o histórico de comandos executados em uma imagem

ex.: docker history tomcat:latest

### Executar comandos dentro de um container
`docker exec <CONTAINER_NAME> <COMMAND>`

exec = executa um comando dentro de um container

ex.: docker exec meu_tomcat cat test.txt


## Dockerfile

Dockerfile = arquivo usado para executar vários comandos e ao final criar imagens configuradas conforme a necessidade

### FROM
`FROM <IMAGE_NAME>:[TAG]`

FROM = comando do Dockerfile qeu indica qual imagem será usada como base para a criação da nova imagem

ex.: FROM tomcat:8.0

### MAINTAINER
`MAINTAINER <EMAIL>`

MAINTAINER = comando usado para indicar o e-mail do mantenedor dessa imagem

<EMAIL> = e-mail do mantenedor

ex.: MAINTAINER giovanny.brandalise@gmail.com

### RUN
`RUN <COMMAND>`

RUN = comando usado para executar comandos dentro da imagem antes de gerar a nova imagem, pode-se ter vários comandos RUN em um mesmo Dockerfile intercalados com outros comandos

<COMMAND> = comando que será executado dentro da imagem

ex.: RUN mkdir /var/www
    RUN echo "testando echo"
    
### VOLUME
`VOLUME <PATH1> <PATH2>`

VOLUME = comando usado para expor diretórios da imagem para serem mapeados pelos containers

<PATH1> <PATH2> = diretórios que serão expostos pela imagem
    
ex.: VOLUMNE /var/www

### EXPOSE
`EXPOSE <PORT1> <PORT2>`

EXPOSE = comando usado para expor portas da imagem a serem mapeadas pelos containers

<PORT1> <PORT2> = portas que serão expostas pela imagem
    
ex.: EXPOSE 80 8080

### WORKDIR
`WORKDIR <PATH>`

WORKDIR = comando usado para indicar o diretório inicial da imagem que serão executados os comandos

<PATH> = diretório inicial da imagem
    
ex.: WORKDIR /var/www

### COPY
`COPY <HOST_PATH> <IMAGE_PATH>`

COPY = comando usado para copiar diretórios e arquivos para dentro da imagem que será criada

<HOST_PATH> = diretório/arquivo origem do host que será copiado

<IMAGE_PATH> = diretório destino do diretório/arquivo dentro da imagem que será criada

ex.: COPY C:\Users\admin\run.sh /home/admin/app/

### ENV
`ENV <ENV_VAR>=<ENV_VALUE>`

ENV = comando usado para criar variáveis de ambiente e/ou atribuir valor a elas

<ENV_VAR> = nome da variável de ambiente

<ENV_VALUE> = valor atribuído à variável

ex.: ENV MYSQL_HOME=/opt/tools/mysql

### ENTRYPOINT
`ENTRYPOINT ["<COMMAND>"]`

ENTRYPOINT = comando que será executado quando iniciar o container baseado na imagem que será criada

<COMMAND> = comando que será executado ao iniciar o container

ex.: ENTRYPOINT ["/home/admin/run.sh"]
