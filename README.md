# Projeto Docker Swarm com MySQL

Este repositório contém a configuração necessária para subir stacks Docker utilizando Docker Swarm, com MySQL, criação de banco de dados e usuário configurados automaticamente via script.

## Requisitos

- **Docker**: Certifique-se de ter o Docker e o Docker Swarm instalados e configurados na sua máquina.
- **Docker Compose**: Para facilitar a definição dos serviços.

## Primeiros Passos

### 1. Clone o repositório

Clone o repositório do GitHub para sua máquina local:
```bash
git clone git@github.com:seu-usuario/seu-repositorio.git
cd seu-repositorio
```
### 2. Configuração de Variáveis de Ambiente
Antes de iniciar, você precisará configurar o arquivo .env com as variáveis de ambiente necessárias para a configuração do MySQL.

Crie ou edite o arquivo .env:

```
MYSQL_DATABASE=seu_banco_de_dados
MYSQL_USER=seu_usuario
MYSQL_PASSWORD=sua_senha
MYSQL_ROOT_PASSWORD=sua_senha_root
TZ=UTC
```

### 3. Inicializar o Docker Swarm
Se o Docker Swarm ainda não foi inicializado na sua máquina, você pode iniciar com o seguinte comando:

```bash
docker swarm init --advertise-addr=IP_DO_SERVIDOR
```

### 4. Criando Network
Aqui você cria a rede que será usada para se comunicar com os containers da vps. No meu exemplo chamo de "web", mas voce pode criar como quiser pelo comando abaixo. Só lembrar de alterar nos arquivos docker-compose:

```bash
docker network create --driver=overlay web
```

### 5. Subir os Stacks com Docker Compose
Para subir os stacks do Docker definidos nos arquivos, execute:

```bash
docker stack deploy -c docker-compose.yml nome_do_stack
```
### 6. Listando as Stacks
```bash
docker stack ps infra_stack
```
### 7. Removendo Stacks
```bash
docker stack rm infra_stack
```
