# ERP PNZ

Este projeto usa Docker Compose para subir os serviços de infraestrutura do ERP:

- PostgreSQL
- Redis

## Requisitos

- Docker
- Docker Compose

## Iniciar o ambiente

Na pasta do projeto, execute:

```bash
docker-compose up -d
```

Isso irá subir os containers em segundo plano.

## Verificar os serviços

```bash
docker-compose ps
```

### Verificar PostgreSQL

```bash
docker exec -it erp_postgres psql -U erp_user -d erp_core
```

### Verificar Redis

```bash
docker exec -it erp_redis redis-cli ping
```

Resultado esperado do Redis:

```bash
PONG
```

## Parar os serviços mantendo os dados

Para parar os containers sem remover os volumes persistidos:

```bash
docker-compose down
```

Isso mantém os dados do PostgreSQL e do Redis salvos nos volumes Docker.

## Reiniciar depois

```bash
docker-compose up -d
```

## Remover tudo (inclusive dados)

Se quiser apagar também os volumes e limpar os dados:

```bash
docker-compose down -v
```

> Atenção: isso remove permanentemente os dados armazenados no banco e no Redis.

## Variáveis de ambiente

O projeto usa um arquivo `.env` para configurar as credenciais e parâmetros locais. O arquivo `.env.example` serve como modelo.

Não commite o arquivo `.env` com dados reais.

## Estrutura principal

- `docker-compose.yml`: configuração dos containers
- `.env`: valores reais locais (não versionado)
- `.env.example`: exemplo de configuração
- `.gitignore`: ignora arquivos sensíveis
