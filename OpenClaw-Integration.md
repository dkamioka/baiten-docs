# 🔌 Integração OpenClaw + Kimi

Guia para integrar o Baiten MCP Server com **OpenClaw** (agente WhatsApp) usando **Kimi** (Moonshot AI) como LLM.

## 📋 Pré-requisitos

1. OpenClaw instalado e configurado
2. Token de acesso da API Baiten
3. Node.js 20+ no servidor

## 🚀 Configuração Passo a Passo

### 1. Deploy do MCP Server no VPS

```bash
# SSH no servidor
ssh root@72.60.49.106

# Criar diretório do MCP
cd /var/www
mkdir -p baiten-mcp
cd baiten-mcp

# Copiar os arquivos (de outro terminal, via scp)
scp -r ./mcp-server/* root@72.60.49.106:/var/www/baiten-mcp/

# No servidor, instalar dependências
npm install
npm run build

# Testar execução
BAITEN_API_TOKEN=seu_token node dist/index.js
```

### 2. Configurar Systemd (opcional)

```bash
# Criar serviço
sudo tee /etc/systemd/system/baiten-mcp.service << 'EOF'
[Unit]
Description=Baiten MCP Server
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/var/www/baiten-mcp
Environment="BAITEN_API_URL=https://72.60.49.106"
Environment="BAITEN_API_TOKEN=seu_token_aqui"
ExecStart=/usr/bin/node /var/www/baiten-mcp/dist/index.js
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl daemon-reload
sudo systemctl enable baiten-mcp
sudo systemctl start baiten-mcp
```

### 3. Configurar OpenClaw

No arquivo de configuração do OpenClaw (geralmente `config.json` ou similar):

```json
{
  "llm": {
    "provider": "kimi",
    "api_key": "sua_api_key_moonshot",
    "model": "kimi-latest"
  },
  "mcp_servers": {
    "baiten": {
      "command": "/usr/bin/node",
      "args": ["/var/www/baiten-mcp/dist/index.js"],
      "env": {
        "BAITEN_API_URL": "https://72.60.49.106",
        "BAITEN_API_TOKEN": "seu_token_jwt"
      }
    }
  },
  "system_prompt": "Você é um atendente virtual do Baiten, um sistema de comandas.\n\nVocê tem acesso às seguintes ferramentas:\n- criar_pessoa: Criar novo cliente e comanda\n- listar_produtos: Ver cardápio\n- adicionar_consumo: Adicionar itens na comanda\n- consultar_saldo: Ver gastos e limite\n- registrar_pagamento: Registrar pagamentos\n- listar_comandas: Listar comandas\n\nSempre seja educado e profissional. Confirme as ações realizadas."
}
```

### 4. Fluxo de Conversa Esperado

```
[WhatsApp] Cliente: "Oi, quero fazer um pedido"
   ↓
[OpenClaw] Detecta mensagem
   ↓
[Kimi] Recebe: "Oi, quero fazer um pedido"
   ↓
[Kimi] Chama ferramenta: criar_pessoa({nome: "Cliente WhatsApp"})
   ↓
[MCP Server] Executa → Cria pessoa + comanda
   ↓
[Kimi] Responde: "Olá! Sua comanda foi aberta. ID: ABC-123"
   ↓
[WhatsApp] Cliente recebe mensagem
```

## 🛠️ Variáveis de Ambiente

| Variável | Descrição | Obrigatório |
|----------|-----------|-------------|
| `BAITEN_API_URL` | URL da API Baiten | Sim |
| `BAITEN_API_TOKEN` | Token JWT de autenticação | Sim |
| `NODE_ENV` | Ambiente (development/production) | Não |

## 🔍 Testando Localmente

```bash
# Antes de conectar ao OpenClaw, teste o MCP:
cd mcp-server

# Configurar token
export BAITEN_API_URL=https://72.60.49.106
export BAITEN_API_TOKEN=$(curl -s -X POST https://72.60.49.106/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@baiten.com.br","senha":"admin123"}' \
  --insecure | jq -r '.data.access_token')

# Executar
node dist/index.js
```

## 📱 Exemplos de Conversa

### Pedido Completo
```
Cliente: "Quero 2 cervejas e 1 porção de batata"

Agente:
1. listar_produtos → encontra cerveja (R$ 8) e batata (R$ 25)
2. adicionar_consumo → cerveja x2 = R$ 16
3. adicionar_consumo → batata x1 = R$ 25
4. consultar_saldo → Total: R$ 41

Resposta: "Pedido registrado! 🍺🍺🍟\nTotal: R$ 41,00"
```

### Pagamento
```
Cliente: "Quero pagar R$ 50 no cartão"

Agente:
1. registrar_pagamento → R$ 50 via cartao_credito
2. consultar_saldo → Saldo restante: R$ 0

Resposta: "Pagamento de R$ 50,00 no cartão registrado! ✅"
```

## ⚠️ Troubleshooting

### "Error: Cannot find module"
```bash
# Reinstalar dependências
rm -rf node_modules package-lock.json
npm install
npm run build
```

### "BAITEN_API_TOKEN não configurado"
```bash
# Obter novo token
curl -X POST https://72.60.49.106/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@baiten.com.br","senha":"admin123"}' \
  --insecure
```

### "Connection refused" no MCP
Verifique se o Node.js está instalado e acessível:
```bash
which node
node --version
```

## 📚 Links Úteis

- [Documentação OpenClaw](https://github.com/openclaw)
- [Documentação Kimi/Moonshot](https://platform.moonshot.cn/docs)
- [API Baiten Swagger](https://72.60.49.106/docs)
