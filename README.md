# 🛒 API E-commerce NestJS

API REST de e-commerce desenvolvida com NestJS, TypeScript, PostgreSQL e autenticação JWT

## Funcionalidades

- ✅ **Autenticação de Usuários** - Registro e login com JWT
- ✅ **Gestão de Usuários** - Gerenciamento de perfil
- 🔄 **Catálogo de Produtos** - Em breve
- 🔄 **Carrinho de Compras** - Em breve
- 🔄 **Gestão de Pedidos** - Em breve
- 🔄 **Processamento de Pagamentos** - Em breve

## 🛠️ Stack Tecnológica

- **Framework:** NestJS
- **Linguagem:** TypeScript
- **Banco de Dados:** PostgreSQL
- **ORM:** TypeORM
- **Autenticação:** JWT + Passport
- **Validação:** class-validator
- **Documentação:** Swagger/OpenAPI

## 📋 Pré-requisitos

- Node.js (v16 ou superior)
- PostgreSQL
- npm ou yarn

## ⚡ Início Rápido

### 1. Clonar o repositório
```bash
git clone https://github.com/seu-usuario/nestjs-ecommerce-api.git
cd nestjs-ecommerce-api
```

### 2. Instalar dependências
```bash
npm install
```

### 3. Configuração do Banco de Dados
```bash
# Instalar PostgreSQL (Debian/Ubuntu)
sudo apt install postgresql postgresql-contrib

# Criar banco de dados e usuário
sudo -u postgres psql
CREATE USER ecommerce_user WITH ENCRYPTED PASSWORD 'sua_senha' CREATEDB;
CREATE DATABASE ecommerce_project OWNER ecommerce_user;
GRANT ALL PRIVILEGES ON DATABASE ecommerce_project TO ecommerce_user;
GRANT ALL ON SCHEMA public TO ecommerce_user;
GRANT CREATE ON SCHEMA public TO ecommerce_user;
\q
```

### 4. Configuração das Variáveis de Ambiente
Criar arquivo `.env` na raiz do projeto:
```env
# Banco de Dados
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=ecommerce_user
DB_PASSWORD=sua_senha
DB_DATABASE=ecommerce_project

# JWT
JWT_SECRET=sua-chave-secreta-jwt-super-segura
JWT_EXPIRES_IN=7d

# Aplicação
PORT=3000
NODE_ENV=development
```

### 5. Executar a aplicação
```bash
# Modo desenvolvimento
npm run start:dev

# Modo produção
npm run build
npm run start:prod
```

## 📖 Documentação da API

Quando a aplicação estiver rodando, acesse:
- **Swagger UI:** http://localhost:3000/api/docs
- **URL Base da API:** http://localhost:3000/api/v1

## 🔗 Endpoints Disponíveis

### Autenticação
- `POST /api/v1/auth/register` - Registrar novo usuário
- `POST /api/v1/auth/login` - Login do usuário

### Usuários
- `GET /api/v1/users/me` - Obter perfil do usuário atual (Protegido)

## 🧪 Testando a API

### Registrar novo usuário
```bash
curl -X POST http://localhost:3000/api/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "email": "usuario@exemplo.com",
    "name": "João Silva",
    "password": "123456"
  }'
```

### Fazer login
```bash
curl -X POST http://localhost:3000/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "usuario@exemplo.com",
    "password": "123456"
  }'
```

### Obter perfil do usuário (usar token do login)
```bash
curl -X GET http://localhost:3000/api/v1/users/me \
  -H "Authorization: Bearer SEU_TOKEN_JWT"
```

## Estrutura do Projeto

```
src/
├── main.ts                 # Ponto de entrada da aplicação
├── app.module.ts           # Módulo raiz
├── config/                 # Arquivos de configuração
│   └── database.config.ts
├── auth/                   # Módulo de autenticação
│   ├── auth.module.ts
│   ├── auth.service.ts
│   ├── auth.controller.ts
│   ├── dto/
│   ├── strategies/
│   └── guards/
└── users/                  # Módulo de usuários
    ├── users.module.ts
    ├── users.service.ts
    ├── users.controller.ts
    ├── entities/
    └── dto/
```

## Scripts Disponíveis

```bash
# Desenvolvimento
npm run start:dev          # Iniciar em modo watch
npm run start:debug        # Iniciar em modo debug

# Produção
npm run build              # Compilar a aplicação
npm run start:prod         # Iniciar servidor de produção

# Testes
npm run test               # Testes unitários
npm run test:e2e           # Testes end-to-end
npm run test:cov           # Cobertura de testes
```

## Contribuindo

1. Faça um fork do repositório
2. Crie sua branch de feature (`git checkout -b feature/funcionalidade-incrivel`)
3. Commit suas mudanças (`git commit -m 'Adiciona funcionalidade incrível'`)
4. Push para a branch (`git push origin feature/funcionalidade-incrivel`)
5. Abra um Pull Request

## Roadmap

- [ ] CRUD de Produtos
- [ ] Funcionalidade de Carrinho de Compras
- [ ] Gestão de pedidos
- [ ] Integração com pagamentos
- [ ] Endereços de usuário
- [ ] Painel administrativo
- [ ] Notificações por email
- [ ] Testes unitários/integração
