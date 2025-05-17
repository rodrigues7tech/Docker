# 📦 Docker

## 🛠️ O que é Docker?
Docker é uma plataforma que permite criar, gerenciar e executar containers. Containers são ambientes isolados que contêm tudo o que um aplicativo precisa para funcionar, tornando fácil o desenvolvimento, teste e deploy.

### 🚀 Instalação do Docker


### Instale e inicie o Docker Desktop.

📌 Linux
```sh
curl -fsSL https://get.docker.com | sudo bash
sudo systemctl enable --now docker
```

Verifique a instalação:

```sh
docker --version
```

# 🏗️ Comandos Essenciais do Docker
### 1. Gerenciamento de Containers
#### Criar e rodar um container

```sh
docker run -d --name meu_container nginx
```
##### -d: Roda o container em segundo plano (detached mode).

##### --name meu_container: Define um nome personalizado para o container.

##### nginx: Usa a imagem oficial do Nginx para criar o container.

#### Parar um container

```sh
docker stop meu_container
``` 

##### Remover um container
```sh
docker rm meu_container
```

##### Listar containers ativos
```sh
docker ps
```

##### Listar todos os containers (inclusive parados)
```sh
docker ps -a
```

### 1. Gerenciamento de Imagens
##### Baixar uma imagem do Docker Hub
```sh
docker pull ubuntu
```

##### Listar imagens disponíveis
```sh
docker images
```

##### Remover uma imagem específica
```sh
docker rmi ubuntu
```

##### Criar uma imagem personalizada usando um Dockerfile
```sh
docker build -t minha_imagem .
```

### 3. Volumes - Persistência de Dados
##### Criar um volume
```sh
docker volume create meu_volume
```

##### Listar volumes disponíveis
```sh
docker volume ls
```

##### Montar um volume em um container
```sh
docker run -d --name meu_container -v meu_volume:/data nginx
```

Montar um volume em Windows
```sh
docker run -d --name meu_container -v "C:/meus-arquivos:/data" nginx
```


### 4. Docker Networks - Comunicação entre Containers
##### Criar uma rede personalizada
```sh
docker network create minha_rede
```

##### Rodar um container dentro da rede
```sh
docker run -d --name app --network minha_rede nginx
```

##### Listar todas as redes disponíveis
```sh
docker network ls
```

### 5. Docker Compose - Orquestração de Containers
##### Exemplo de docker-compose.yml:
```sh
version: '3.8'

services:
  app:
    image: nginx
    ports:
      - "8080:80"
    volumes:
      - ./dados:/data
    networks:
      - minha_rede

networks:
  minha_rede:
    driver: bridge
```

##### Rodar containers com Docker Compose
```sh
docker-compose up -d
```

##### Parar e remover containers criados pelo Compose
```sh
docker-compose down
```

### 6. Gerenciamento de Logs e Processos
##### Exibir logs de um container
```sh
docker logs meu_container
```

##### Monitorar processos dentro de um container
```sh
docker top meu_container
```

##### Executar comandos dentro de um container
```sh
docker exec meu_container ls /data
```

##### Acessar um container em modo interativo
```sh
docker exec -it meu_container bash
```

### 7. Limpeza de Containers e Imagens
##### Remover containers parados
```sh
docker container prune
```

##### Remover imagens não utilizadas
```sh
docker image prune
```

##### Remover tudo (containers, volumes e redes não usados)
```sh
docker system prune -a
```

### 8. Publicar Imagens no Docker Hub
##### Autenticar-se no Docker Hub
```sh
docker login
```

##### Criar uma nova imagem
```sh
docker build -t meu_usuario/minha_imagem .
```

##### Enviar para o Docker Hub
```sh
docker push meu_usuario/minha_imagem
```

##### Para baixar essa imagem em outro computador:
```sh
docker pull meu_usuario/minha_imagem
```

### 9. Segurança e Controle de Recursos
##### Criar um container com usuário específico
```sh
docker run -d --user 1000:1000 --name seguro nginx
```

##### Isso evita que o container rode como root.

##### Definir limite de CPU para um container
```sh
docker run -d --cpus="0.5" nginx
```

##### Definir limite de memória
```sh
docker run -d --memory="500m" nginx
```

### 10. Docker Swarm - Escalabilidade
##### Inicializar o modo Swarm

```sh
docker swarm init
```

##### Criar e rodar serviços no Swarm
```sh
docker stack deploy -c docker-compose.yml minha_stack
```

##### Escalar um serviço para rodar em múltiplos containers
```sh
docker service scale meu_servico=5
```

#### 🎯 Conclusão
Docker é uma ferramenta poderosa para criar, gerenciar e escalar aplicações. Com essa documentação, você pode gerenciar containers, otimizar recursos e configurar ambientes de produção de maneira eficiente. 🚀