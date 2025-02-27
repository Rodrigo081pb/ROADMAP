## Docker 

### O que é Docker ? 

- Uma plataforma que permite criar, implantar e executar aplicações dentro de um container.

- - Container: 

    É um pacote que contém tudo o que a aplicação precisa:

    Sistema operacional, base, dependências, bibliotecas e o próprio código.

### Por que usar o Docker? 

- Pela sua portabilidade, conseguimos rodar em qualquer lugar que tenha Docker instalado (Máquina local, servidor, cloud).

- Cada container tem seu próprio ambiente, contendo suas depêndencias e variáveis, evitando conflito de versão.

- Pela sua escalabilidade já que é fácil replicar contêineres (subir mais instâncias) para lidar com maior carga.

- Simplifica a configuração do ambiente de desenvolvimento (tua aplicação e dependências vão juntas para o contêner)

- Link para instalação (https://www.docker.com/products/docker-desktop)

Após a instalação você pode executar o docker run hello-world

### Conceitos

1.0 - Imagens e Contêineres 

- Imagem: É uma "foto" do sistema de arquivos + configuração que vai ser usada para criar contêneres.

- Contêiner: É a imagem em execução, tipo a instância de uma imagem

### Comandos:

- docker pull <imagem>: Baixa uma imagem do Docker Hub ou de outro registry.

- docker images: Lista as imagens baixadas na máquina.

- docker run <imagem>: Cria e executa um contêiner baseado na imagem.

- docker ps: Lista os contêineres em execução.

- docker ps -a: Lista todos os contêineres, inclusive parados.

- docker stop <container_id>: Para um contêiner.

- docker rm <container_id>: Remove um contêiner.

- docker rmi <imagem>: Remove uma imagem.

### DockerFile

- Arquivo de texto com instruções para construir uma imagem

Comandos comuns do DockerFile:

- FROM: define a imagem base (ex: FROM python:3.9-slim).

- COPY ou ADD: copia arquivos da tua máquina para o contêiner.

- RUN: executa comandos durante a construção da imagem (instalar libs, criar pastas etc.).

- EXPOSE: documenta a porta exposta pela aplicação (opcional, mas recomendado).

- CMD ou ENTRYPOINT: define qual comando será executado quando o contêiner iniciar.

