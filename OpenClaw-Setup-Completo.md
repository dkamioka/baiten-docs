# 🔧 Configuração Completa do OpenClaw + Baiten MCP

Guia passo a passo para integrar o Baiten MCP Server com o OpenClaw.

---

## 📋 O que você precisa saber

O **OpenClaw** usa uma ferramenta chamada **`mcporter`** para se conectar a MCP Servers. Isso é diferente do Claude Desktop ou Cursor que usam `mcpServers` diretamente.

### Diferenças importantes:

| Cliente | Formato | Arquivo de Config |
|---------|---------|-------------------|
| Claude Desktop | `mcpServers` | `claude_desktop_config.json` |
| Cursor | `mcpServers` | `.cursor/mcp.json` |
| **OpenClaw** | `mcporter` | `config/mcporter.json` |

---

## 🚀 Opção 1: Comando Direto (Mais Simples)

Sem necessidade de arquivo de configuração. Use diretamente no chat do OpenClaw:

```
mcporter call --stdio "/var/www/baiten-mcp/mcp-wrapper.sh" criar_pessoa nome="João Silva"
```

Ou para listar produtos:
```
mcporter call --stdio "/var/www/baiten-mcp/mcp-wrapper.sh" listar_produtos busca="cerveja"
```

---

## ⚙️ Opção 2: Configuração Persistente (Recomendado)

### Passo 1: Instalar o mcporter

```bash
npm install -g mcporter
```

### Passo 2: Criar arquivo de configuração

Crie o arquivo `config/mcporter.json` na pasta do seu projeto OpenClaw:

```json
{
  "servers": {
    "baiten": {
      "type": "stdio",
      "command": "/var/www/baiten-mcp/mcp-wrapper.sh",
      "args": [],
      "env": {
        "BAITEN_API_URL": "https://72.60.49.106",
        "BAITEN_API_TOKEN": "eyJhbGciOiJIUzI1NiIs..."
      }
    }
  }
}
```

**Ou** usando o wrapper que carrega o .env:

```json
{
  "servers": {
    "baiten": {
      "type": "stdio",
      "command": "/var/www/baiten-mcp/mcp-wrapper.sh",
      "args": []
    }
  }
}
```

### Passo 3: Adicionar ao OpenClaw

No diretório do seu agente OpenClaw, execute:

```bash
mcporter config add baiten --stdio "/var/www/baiten-mcp/mcp-wrapper.sh"
```

### Passo 4: Testar

```bash
# Listar ferramentas disponíveis
mcporter list baiten --schema

# Ou no chat do OpenClaw:
"Use o mcporter para chamar o baiten.criar_pessoa com nome='João Silva'"
```

---

## 💬 Usando no Chat do OpenClaw

### Para criar uma pessoa:
```
Crie uma nova comanda para o cliente "Maria Oliveira" usando o servidor baiten
```

### Para listar produtos:
```
Liste os produtos disponíveis no cardápio usando mcporter no servidor baiten
```

### Para adicionar consumo:
```
Adicione 2 cervejas na comanda ABC-123 usando o servidor baiten
```

---

## 🔧 Arquivos no Servidor (VPS)

Verifique se estão atualizados:

```bash
# SSH no servidor
ssh root@72.60.49.106

# Verificar arquivos
cd /var/www/baiten-mcp
ls -la

# Testar MCP Server
./mcp-wrapper.sh
# Deve mostrar: 🚀 Iniciando Baiten MCP Server...
```

---

## 🐛 Troubleshooting

### "command not found: mcporter"
```bash
npm install -g mcporter
```

### "Token não configurado"
O token JWT expirou (dura 15 minutos). Renove:

```bash
curl -X POST https://72.60.49.106/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@baiten.com.br","senha":"admin123"}' \
  --insecure
```

Copie o `accessToken` e atualize no `.env` do servidor.

### "Server not found"
Verifique se o arquivo `config/mcporter.json` está no diretório correto do OpenClaw.

### Ferramenta não aparece
```bash
# Verificar se o servidor está funcionando
mcporter list

# Ver detalhes de uma ferramenta específica
mcporter list baiten.criar_pessoa --schema
```

---

## 📝 Exemplos de Uso

### Cenário 1: Cliente Novo
**Você diz:**
```
Crie uma nova pessoa chamada "João Silva" no sistema baiten
```

**OpenClaw executa:**
```bash
mcporter call --stdio "/var/www/baiten-mcp/mcp-wrapper.sh" criar_pessoa nome="João Silva"
```

**Resposta:**
```
✅ Pessoa criada: João Silva
✅ Comanda aberta: #ABC-123
```

### Cenário 2: Adicionar Pedido
**Você diz:**
```
No servidor baiten, adicione 2 cervejas na comanda ABC-123
```

**OpenClaw:**
1. Primeiro lista produtos para encontrar o ID
2. Depois adiciona o consumo

### Cenário 3: Consultar Saldo
**Você diz:**
```
Consulte o saldo da comanda ABC-123 no baiten
```

---

## 🔗 Recursos

- [Documentação mcporter](http://mcporter.dev)
- [Skill mcporter no OpenClaw](https://github.com/openclaw/openclaw/tree/main/skills/mcporter)
- [Baiten API](https://72.60.49.106/docs)

---

## ✅ Checklist de Configuração

- [ ] mcporter instalado: `npm install -g mcporter`
- [ ] Arquivo `config/mcporter.json` criado
- [ ] Caminho `/var/www/baiten-mcp/mcp-wrapper.sh` correto
- [ ] Token JWT atualizado no servidor
- [ ] Teste: `mcporter list` mostra o servidor baiten
- [ ] Teste no chat: consegue chamar ferramentas
