# learn-docker

## CLI
`docker version`

docker = comando padrão do cli
version = exibe a versão do cli e do daemon do docker

### Parâmetros padrões

<IMAGE_NAME> = nome da imagem
<CONTAINER_NAME> = nome do container

### Criando container
`docker run <IMAGE_NAME>`

run = comando para criar um container

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

[TAG] = tag opcional atribuída a imagem a ser baixada, geralmente a versão da imagem

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
