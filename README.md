# Docker Setup - Backend (Strapi) + Frontend (React)

Este projeto consiste em uma aplicação fullstack com um backend em Strapi 5 e um frontend em Next 15 com TypeScript, configurados para rodar em containers Docker.

## 🚀 Pré-requisitos

Antes de começar, você precisa ter instalado em sua máquina:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Git

## 📦 Estrutura do Projeto

```.
├── docker-compose.yml
├── wm-backend/
│   ├── Dockerfile
│   └── ... (arquivos do Strapi)
└── wm-frontend/
    ├── Dockerfile
    └── ... (arquivos do Next)
```

## 🛠️ Configuração e Instalação

Clone o repositório:

```bash
git clone git@github.com:maverickanp/wm-backend.git
git clone git@github.com:maverickanp/wm-frontend.git
```

Construa e inicie os containers:

```bash
docker compose up --build
```

Este comando irá:

Construir as imagens dos containers

- Iniciar o backend na porta 1337
- Iniciar o frontend na porta 3000

📝 Informações Importantes

## Backend (Strapi)

```bash
URL: http://localhost:1337
```

## Frontend (Next)

```bash
URL: http://localhost:3000
```

🔍 Monitoramento

## Para verificar o status dos containers:

```bash
docker compose ps
```

## Para ver os logs dos containers:

```bash
# Todos os containers
docker compose logs

# Apenas backend
docker compose logs wm-backend

# Apenas frontend
docker compose logs wm-frontend
```

🛑 Parando os Containers

## Para parar os containers:

```bash
docker compose down
```

🔧 Resolução de Problemas

## Problemas comuns:

- Portas em uso

Erro: "port is already allocated"

- Solução: Verifique se as portas 1337 e 3000 estão livres

```bash
# Windows/Linux
netstat -ano | findstr 1337
netstat -ano | findstr 3000
```

## Problemas de permissão

Erro: "permission denied"

- Solução: Execute os comandos com sudo (Linux/Mac)

Erro de conexão entre containers

- Verifique se a variável de ambiente NEXT_PUBLIC_STRAPI_URL está correta no .env.local do wm-frontend

```bash
NEXT_PUBLIC_STRAPI_URL=http://localhost:3000
```

Verifique se as variáveis de ambiente do Strapi está correta no .env do wm-backend, use o .env.example como parametro, por padrao foi configurado o sqlite como banco de dados

```bash
sudo docker compose up
```

🔄 Atualizações e Manutenção

## Para atualizar as imagens e reconstruir os containers:

```bash
docker compose down
docker compose build --no-cache
docker compose up
```
