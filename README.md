# Docker Setup - Backend (Strapi) + Frontend (React)

Este projeto consiste em uma aplicação fullstack com um backend em Strapi 5 e um frontend em Next 15 com TypeScript, configurados para rodar em containers Docker.

## 🚀 Pré-requisitos

Antes de começar, você precisa ter instalado em sua máquina:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Git

## 📦 Estrutura do Projeto

.
├── docker-compose.yml
├── wm-backend/
│   ├── Dockerfile
│   └── ... (arquivos do Strapi)
└── wm-frontend/
├── Dockerfile
└── ... (arquivos do React)

Copy
## 🛠️ Configuração e Instalação

1. Clone o repositório:
```bash
git clone git@github.com:maverickanp/wm-backend.git
git clone git@github.com:maverickanp/wm-frontend.git

Construa e inicie os containers:

bashCopydocker compose up --build
Este comando irá:

Construir as imagens dos containers
Iniciar o backend na porta 1337
Iniciar o frontend na porta 3000

📝 Informações Importantes
Backend (Strapi)

URL: http://localhost:1337
Tecnologias:

Strapi 5
Node.js 18 (Alpine)
SQLite como banco de dados



Frontend (React)

URL: http://localhost:3000
Tecnologias:

React 18
TypeScript
Node.js 20



🔍 Monitoramento
Para verificar o status dos containers:
bashCopydocker compose ps
Para ver os logs dos containers:
bashCopy# Todos os containers
docker compose logs

# Apenas backend
docker compose logs wm-backend

# Apenas frontend
docker compose logs wm-frontend
🛑 Parando os Containers
Para parar os containers:
bashCopydocker compose down
🔧 Resolução de Problemas
Problemas comuns:

Portas em uso

Erro: "port is already allocated"
Solução: Verifique se as portas 1337 e 3000 estão livres

bashCopy# Windows/Linux
netstat -ano | findstr 1337
netstat -ano | findstr 3000

Problemas de permissão

Erro: "permission denied"
Solução: Execute os comandos com sudo (Linux/Mac)

bashCopysudo docker compose up

Erro de conexão entre containers

Verifique se a variável de ambiente NEXT_PUBLIC_STRAPI_URL está correta no docker-compose.yml



🔄 Atualizações e Manutenção
Para atualizar as imagens e reconstruir os containers:
bashCopydocker compose down
docker compose build --no-cache
docker compose up
