# learn-docker

## CLI
`docker version`

docker = comando padrão do cli
version = exibe a versão do cli e do daemon do docker

### Criando container
`docker run <IMAGE_NAME>`

run = comando para criar um container

<IMAGE_NAME> = nome da imagem usada para criar o container

ex.: `docker run hello-world`

### Listando containers
`docker ps [-a]`

ps = comando para listar os containers

[-a] = parâmetro opcional para listar todos os containers incusive os que estão parados

### Listando imagens
`docker images`

images = exibe as imagens do repositório local
