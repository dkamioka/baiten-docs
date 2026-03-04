# ⚙️ Configuração do Ambiente

Guia técnico para configurar o ambiente de desenvolvimento e produção do Baiten ANC.

---

## 📋 Requisitos

### Para Desenvolvimento

| Requisito | Versão | Obrigatório |
|-----------|--------|-------------|
| Node.js | 20.x | Sim |
| npm | 10.x | Sim |
| PostgreSQL | 15+ | Sim |
| Git | 2.x | Recomendado |

### Para Produção (VPS)

| Requisito | Versão | Obrigatório |
|-----------|--------|-------------|
| Ubuntu/Debian | 22.04+ | Sim |
| Node.js | 20.x | Sim |
| PostgreSQL | 15+ | Sim |
| PM2 | Latest | Recomendado |
| Nginx | Latest | Recomendado |

---

## 🚀 Instalação Local (Desenvolvimento)

### 1. Clone o Repositório

```bash
git clone https://github.com/dkamioka/BaitenANC-backend.git
cd BaitenANC-backend
```

### 2. Instale as Dependências

```bash
npm install
```

### 3. Configure o Banco de Dados

```bash
# Instale o PostgreSQL localmente
# ou use Docker:
docker run -d \
  --name baiten-postgres \
  -e POSTGRES_USER=baiten \
  -e POSTGRES_PASSWORD=senha \
  -e POSTGRES_DB=baiten \
  -p 5432:5432 \
  postgres:15
```

### 4. Configure as Variáveis de Ambiente

```bash
cp .env.example .env
```

Edite o arquivo `.env`:

```env
# Database
DATABASE_URL="postgresql://baiten:senha@localhost:5432/baiten"

# JWT
JWT_SECRET="sua_chave_secreta_aqui"
JWT_EXPIRES_IN="15m"

# Server
PORT=3003
NODE_ENV=development
```

### 5. Execute as Migrações

```bash
npx prisma migrate dev
```

### 6. Inicie o Servidor

```bash
# Modo desenvolvimento
npm run dev

# Modo produção
npm run build
npm start
```

---

## 🌐 Deploy em VPS (Produção)

### 1. Preparação do Servidor

```bash
# Atualize o sistema
sudo apt update && sudo apt upgrade -y

# Instale dependências
sudo apt install -y curl git nginx postgresql postgresql-contrib

# Instale Node.js 20
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs

# Instale PM2
sudo npm install -g pm2
```

### 2. Configure o PostgreSQL

```bash
# Acesse o PostgreSQL
sudo -u postgres psql

# Crie o usuário e banco
CREATE USER baiten WITH PASSWORD 'senha_segura';
CREATE DATABASE baiten OWNER baiten;
\q

# Verifique conexão
psql -U baiten -d baiten -h localhost
```

### 3. Deploy da Aplicação

```bash
# Crie diretório
sudo mkdir -p /var/www/baitenanc
sudo chown -R $USER:$USER /var/www/baitenanc

# Clone o repositório
cd /var/www/baitenanc
git clone https://github.com/dkamioka/BaitenANC-backend.git .

# Instale dependências
npm install

# Build
npm run build

# Configure .env
sudo nano .env
```

Conteúdo do `.env`:
```env
DATABASE_URL="postgresql://baiten:senha_segura@localhost:5432/baiten"
JWT_SECRET="chave_super_secreta_aqui"
JWT_EXPIRES_IN="15m"
PORT=3003
NODE_ENV=production
```

### 4. Configure o PM2

```bash
# Inicie com PM2
pm2 start dist/server.js --name baitenanc

# Salve configuração
pm2 save
pm2 startup
```

### 5. Configure o Nginx

```bash
sudo nano /etc/nginx/sites-available/baitenanc
```

Configuração:
```nginx
server {
    listen 80;
    server_name seu-dominio.com;
    
    location / {
        proxy_pass http://localhost:3003;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

Ative:
```bash
sudo ln -s /etc/nginx/sites-available/baitenanc /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```

### 6. SSL (HTTPS) - Opcional mas Recomendado

```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d seu-dominio.com
```

---

## 🤖 Deploy do MCP Server

### 1. Acesse o Diretório

```bash
cd /var/www/baiten-mcp
```

### 2. Instale Dependências

```bash
npm install --production
```

### 3. Configure o Token

Obtenha um token JWT válido:
```bash
curl -X POST https://72.60.49.106/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@baiten.com.br","senha":"admin123"}' \
  --insecure
```

Configure o `.env`:
```bash
sudo nano .env
```

```env
BAITEN_API_URL=https://72.60.49.106
BAITEN_API_TOKEN=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

### 4. Teste

```bash
node dist/index.js
```

---

## 🔄 Atualização

### Atualizar Aplicação Principal

```bash
cd /var/www/baitenanc

# Puxe as atualizações
git pull origin main

# Instale novas dependências
npm install

# Execute migrações
npx prisma migrate deploy

# Rebuild
npm run build

# Restart
pm2 restart baitenanc
```

### Atualizar MCP Server

```bash
cd /var/www/baiten-mcp

# Copie nova versão
git pull origin main

# Instale dependências
npm install --production

# Teste
node dist/index.js
```

---

## 🛠️ Troubleshooting

### Erro: "Cannot find module"

```bash
# Reinstale dependências
rm -rf node_modules package-lock.json
npm install
```

### Erro: "Database connection failed"

```bash
# Verifique PostgreSQL
sudo systemctl status postgresql

# Teste conexão
psql -U baiten -d baiten -h localhost

# Verifique variáveis de ambiente
cat .env | grep DATABASE_URL
```

### Erro: "Port already in use"

```bash
# Encontre processo usando a porta
sudo lsof -i :3003

# Mate o processo
sudo kill -9 <PID>
```

### Erro: "Permission denied"

```bash
# Corrija permissões
sudo chown -R $USER:$USER /var/www/baitenanc
chmod -R 755 /var/www/baitenanc
```

---

## 📊 Comandos Úteis

### PM2

```bash
# Listar processos
pm2 list

# Ver logs
pm2 logs baitenanc

# Monitorar
pm2 monit

# Restart
pm2 restart baitenanc

# Stop
pm2 stop baitenanc
```

### PostgreSQL

```bash
# Acessar banco
sudo -u postgres psql baiten

# Backup
pg_dump -U baiten baiten > backup.sql

# Restore
psql -U baiten baiten < backup.sql
```

### Nginx

```bash
# Testar configuração
sudo nginx -t

# Restart
sudo systemctl restart nginx

# Ver logs
sudo tail -f /var/log/nginx/error.log
```

---

## 🔗 Links Importantes

- [[MCP Server - Visão Geral]]
- [[OpenClaw Integration]]
- [[Deploy do MCP Server]]
- [API Swagger](https://72.60.49.106/docs)
- [Repositório GitHub](https://github.com/dkamioka/BaitenANC-backend)

---

*Documentação técnica para administradores de sistema.*
