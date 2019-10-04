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
`docker run -d --name <CONTAINER_NAME> <IMAGE_NAME>:[TAG]`

run = comando para criar um container

-d = roda o container em background

--name = flag para indicar o nome do container que será criado

ex.: `docker run hello-world`

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

### Exibir alterações realizadas em um container
`docker diff <CONTAINER_NAME>`

diff = exibe as alterações realizadas no container

### Exibir help de um comando
`docker <COMMAND> --help`

<COMMAND> = comando do docker cli

--help = exibe o help do comando

### Criando uma imagem a partir de um container
`docker commit <CONTAINER_NAME> <NEW_IMAGE_NAME>:[TAG]`

commit = commita uma imagem a partir de um container

<CONTAINER_NAME> = container base para criação da imagem

<NEW_IMAGE_NAME> = nome da imagem que será criada
