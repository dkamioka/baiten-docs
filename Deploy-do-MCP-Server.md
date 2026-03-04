# 📦 Deploy Manual do MCP Server

Guia passo a passo para instalar o Baiten MCP Server no VPS (72.60.49.106).

## 🔧 Passo 1: Preparar os Arquivos

No seu computador local, dentro do projeto:

```bash
# Compactar o mcp-server
tar -czf mcp-server-deploy.tar.gz mcp-server/

# Ou se preferir, copie apenas os arquivos necessários:
# - mcp-server/dist/
# - mcp-server/package.json
# - mcp-server/deploy.sh
```

## 🚀 Passo 2: Enviar para o VPS

Opção A - Via SCP (se tiver acesso SSH):
```bash
scp mcp-server-deploy.tar.gz root@72.60.49.106:/tmp/
```

Opção B - Via SFTP (FileZilla, etc):
- Host: 72.60.49.106
- Usuário: root
- Senha: [sua senha]
- Envie para: `/tmp/mcp-server-deploy.tar.gz`

Opção C - Upload via painel Hostinger:
- Use o gerenciador de arquivos do painel Hostinger
- Faça upload para `/tmp/`

## 🖥️ Passo 3: Instalar no VPS

Acesse o VPS via SSH ou terminal do painel Hostinger:

```bash
# Extrair arquivos
cd /tmp
tar -xzf mcp-server-deploy.tar.gz

# Mover para diretório de produção
sudo mkdir -p /var/www/baiten-mcp
sudo cp -r mcp-server/* /var/www/baiten-mcp/

# Entrar no diretório
cd /var/www/baiten-mcp

# Instalar dependências (sem devDependencies)
npm install --production

# Verificar se compilou
cat dist/index.js | head -5
```

## 🔑 Passo 4: Obter Token JWT

```bash
# Fazer login na API para obter token
curl -X POST https://72.60.49.106/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@baiten.com.br","senha":"admin123"}' \
  --insecure
```

Copie o valor do campo `access_token` da resposta.

## ⚙️ Passo 5: Configurar Ambiente

```bash
cd /var/www/baiten-mcp

# Criar arquivo .env
sudo tee .env << 'EOF'
BAITEN_API_URL=https://72.60.49.106
BAITEN_API_TOKEN=COLE_SEU_TOKEN_AQUI
EOF

# Verificar
sudo cat .env
```

## 🔧 Passo 6: Criar Serviço Systemd

```bash
# Criar arquivo de serviço
sudo tee /etc/systemd/system/baiten-mcp.service << 'EOF'
[Unit]
Description=Baiten MCP Server
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/var/www/baiten-mcp
Environment="BAITEN_API_URL=https://72.60.49.106"
Environment="BAITEN_API_TOKEN=COLE_SEU_TOKEN_AQUI"
ExecStart=/usr/bin/node /var/www/baiten-mcp/dist/index.js
Restart=on-failure
RestartSec=10
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
EOF

# Recarregar systemd
sudo systemctl daemon-reload

# Habilitar para iniciar automaticamente
sudo systemctl enable baiten-mcp

# Iniciar serviço
sudo systemctl start baiten-mcp

# Verificar status
sudo systemctl status baiten-mcp
```

## ✅ Passo 7: Verificar Instalação

```bash
# Ver logs
sudo journalctl -u baiten-mcp -f

# Deve aparecer:
# 🚀 Iniciando Baiten MCP Server...
# 📡 API: https://72.60.49.106
# ✅ Baiten MCP Server conectado e pronto!
```

## 🔌 Passo 8: Configurar OpenClaw

No arquivo de configuração do OpenClaw (onde você configura o agente WhatsApp):

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
        "BAITEN_API_TOKEN": "SEU_TOKEN_AQUI"
      }
    }
  },
  "system_prompt": "Você é um atendente virtual do Baiten, um sistema de comandas para restaurantes/bares.\n\nVocê tem acesso às seguintes ferramentas:\n- criar_pessoa: Criar novo cliente e abrir comanda automaticamente\n- listar_produtos: Ver cardápio/itens disponíveis\n- adicionar_consumo: Adicionar produtos na comanda do cliente\n- consultar_saldo: Mostrar gastos e limite de crédito\n- registrar_pagamento: Registrar pagamentos recebidos\n- listar_comandas: Ver comandas ativas\n\nInstruções:\n1. Sempre seja educado e profissional\n2. Confirme as ações realizadas com detalhes\n3. Se o cliente não tiver comanda, crie uma automaticamente\n4. Mostre valores em formato de moeda (R$)\n5. Informe o ID da comanda quando relevante"
}
```

## 🧪 Passo 9: Testar

1. Envie uma mensagem no WhatsApp: "Oi, quero fazer um pedido"
2. O agente deve:
   - Criar uma pessoa/comanda automaticamente
   - Responder com o ID da comanda
3. Envie: "Quero uma coca"
4. O agente deve:
   - Listar produtos e encontrar "Coca-Cola"
   - Adicionar na comanda
   - Confirmar o valor

## 📋 Comandos Úteis

```bash
# Ver logs em tempo real
sudo journalctl -u baiten-mcp -f

# Restartar o serviço
sudo systemctl restart baiten-mcp

# Parar o serviço
sudo systemctl stop baiten-mcp

# Verificar se está rodando
sudo systemctl is-active baiten-mcp

# Ver recursos utilizados
sudo systemctl status baiten-mcp
```

## 🛠️ Troubleshooting

### "Module not found"
```bash
cd /var/www/baiten-mcp
rm -rf node_modules
npm install --production
sudo systemctl restart baiten-mcp
```

### "BAITEN_API_TOKEN não configurado"
Verifique se o `.env` foi criado corretamente e o serviço foi reiniciado:
```bash
sudo cat /var/www/baiten-mcp/.env
sudo systemctl restart baiten-mcp
```

### "Permission denied"
Verifique permissões:
```bash
sudo chown -R root:root /var/www/baiten-mcp
sudo chmod +x /var/www/baiten-mcp/dist/index.js
```

### Token expirado
O token JWT expira. Para renovar:
```bash
# Obter novo token
curl -X POST https://72.60.49.106/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@baiten.com.br","senha":"admin123"}' \
  --insecure

# Atualizar no .env e reiniciar
sudo systemctl restart baiten-mcp
```

## 📁 Estrutura Final no VPS

```
/var/www/baiten-mcp/
├── dist/
│   ├── index.js
│   ├── index.d.ts
│   └── ...
├── node_modules/
├── package.json
├── .env
└── ...
```

## 🎉 Pronto!

Seu MCP Server está configurado e pronto para uso com o OpenClaw + Kimi!
