# 🤖 Baiten MCP Server

Servidor MCP (Model Context Protocol) para integração do **Baiten ANC** com LLMs como Kimi, Claude, GPT, etc.

## 📖 O que é MCP?

MCP (Model Context Protocol) é um protocolo aberto da Anthropic que permite a LLMs se conectarem a ferramentas e dados externos de forma padronizada. Com esse servidor MCP, seu agente de IA pode:

- 📝 **Criar pessoas/comandas** automaticamente
- 📦 **Listar produtos** disponíveis
- 🛒 **Adicionar consumos** na comanda
- 💰 **Consultar saldo** e limite
- 💳 **Registrar pagamentos**
- 📋 **Listar comandas** ativas

## 🚀 Instalação Rápida

```bash
cd mcp-server
npm install
npm run build
```

## ⚙️ Configuração

### 1. Copie o arquivo de exemplo:

```bash
cp .env.example .env
```

### 2. Configure o token:

```bash
# .env
BAITEN_API_URL=https://72.60.49.106
BAITEN_API_TOKEN=seu_token_jwt_aqui
```

> 💡 **Como obter o token:**
> ```bash
> curl -X POST https://72.60.49.106/auth/login \
>   -H "Content-Type: application/json" \
>   -d '{"email":"admin@baiten.com.br","senha":"admin123"}' \
>   --insecure
> ```

## 🎯 Uso

### Executar manualmente:

```bash
npm start
```

### Integrar com Kimi (Moonshot AI):

Para usar com o Kimi ou outro cliente MCP, adicione à configuração:

```json
{
  "mcpServers": {
    "baiten": {
      "command": "node",
      "args": ["/caminho/completo/para/mcp-server/dist/index.js"],
      "env": {
        "BAITEN_API_URL": "https://72.60.49.106",
        "BAITEN_API_TOKEN": "seu_token_aqui"
      }
    }
  }
}
```

## 🛠️ Ferramentas Disponíveis

| Ferramenta | Descrição | Parâmetros |
|------------|-----------|------------|
| `criar_pessoa` | Cria novo cliente e comanda | `nome` (obrigatório), `telefone`, `email`, `cpf` |
| `listar_produtos` | Lista produtos disponíveis | `busca` (opcional) |
| `adicionar_consumo` | Adiciona item na comanda | `comanda_id`, `produto_id`, `quantidade` |
| `consultar_saldo` | Mostra saldo e limite | `comanda_id` |
| `registrar_pagamento` | Registra pagamento | `comanda_id`, `valor`, `forma_pagamento` |
| `listar_comandas` | Lista comandas | `status`, `limite` |

## 💬 Exemplos de Conversa

### Cenário 1: Novo cliente
```
Cliente: "Quero fazer uma comanda, meu nome é João Silva"

Agente (via Kimi + MCP):
→ Chama: criar_pessoa({nome: "João Silva"})
← Retorna: Pessoa e comanda criadas

Resposta: "Olá João! Sua comanda foi aberta com sucesso. 
ID da comanda: abc-123. Pode fazer seus pedidos!"
```

### Cenário 2: Adicionar consumo
```
Cliente: "Quero um almoço completo e uma coca"

Agente:
→ Chama: listar_produtos({busca: "almoço"})
← Retorna: Almoço Completo - R$ 22.00
→ Chama: listar_produtos({busca: "coca"})
← Retorna: Coca-Cola - R$ 6.00
→ Chama: adicionar_consumo({comanda_id: "abc-123", produto_id: "prod-456", quantidade: 1})
→ Chama: adicionar_consumo({comanda_id: "abc-123", produto_id: "prod-789", quantidade: 1})

Resposta: "Adicionei na sua comanda:\n🍽️ 1x Almoço Completo - R$ 22.00\n🥤 1x Coca-Cola - R$ 6.00\n\nTotal: R$ 28.00"
```

### Cenário 3: Consultar saldo
```
Cliente: "Quanto eu já gastei?"

Agente:
→ Chama: consultar_saldo({comanda_id: "abc-123"})

Resposta: "📊 Resumo da sua comanda:\n💰 Limite: R$ 100.00\n📉 Utilizado: R$ 45.00\n✅ Disponível: R$ 55.00"
```

### Cenário 4: Pagamento
```
Cliente: "Quero pagar R$ 30 no pix"

Agente:
→ Chama: registrar_pagamento({comanda_id: "abc-123", valor: 30, forma_pagamento: "pix"})

Resposta: "✅ Pagamento registrado!\nR$ 30.00 via PIX\nSaldo restante: R$ 15.00"
```

## 📁 Estrutura do Projeto

```
mcp-server/
├── src/
│   └── index.ts          # Servidor MCP principal
├── dist/                 # Código compilado
├── .env                  # Configurações (não commitar)
├── .env.example          # Exemplo de config
├── package.json          # Dependências
├── tsconfig.json         # Config TypeScript
└── README.md            # Este arquivo
```

## 🔧 Solução de Problemas

### Erro: "certificate has expired"
O certificado SSL é self-signed. Configure o cliente HTTP para ignorar verificação de certificado em ambiente de desenvolvimento.

### Erro: "BAITEN_API_TOKEN não configurado"
Execute o login na API para obter o token JWT e configure no `.env`.

### Erro: "Conexão recusada"
Verifique se a API Baiten está online: `curl https://72.60.49.106/health --insecure`

## 📚 Recursos

- [Documentação MCP](https://modelcontextprotocol.io)
- [Swagger API Baiten](https://72.60.49.106/docs)
- [SDK MCP Node.js](https://github.com/modelcontextprotocol/typescript-sdk)

## 📝 Licença

MIT
