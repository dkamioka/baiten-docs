# 📊 Status do Projeto Baiten ANC

**Data do Snapshot:** 04 de Março de 2025  
**Versão:** 1.0.0  
**Status:** ✅ Produção

---

## 🎯 Resumo Executivo

Sistema de comandas digital completo com:
- ✅ API REST funcionando em produção
- ✅ Banco de dados PostgreSQL
- ✅ Documentação completa publicada
- ✅ MCP Server com auto-refresh de token
- ✅ Integração pronta para OpenClaw

---

## 🌐 Infraestrutura em Produção

### VPS (Hostinger)
- **IP:** 72.60.49.106
- **URL API:** https://72.60.49.106
- **Swagger:** https://72.60.49.106/docs
- **Status:** ✅ Online

### Serviços Instalados
```
✅ Node.js 20
✅ PostgreSQL 15
✅ Nginx (reverse proxy)
✅ PM2 (gerenciamento de processos)
✅ Baiten API (porta 3003)
✅ Baiten MCP Server (stdio)
```

---

## 📁 Estrutura do Projeto

```
BaitenANC-backend/
├── 📄 API (src/)
│   ├── modules/
│   │   ├── auth/         # Autenticação JWT
│   │   ├── pessoas/      # CRUD de clientes
│   │   ├── comandas/     # Comandas e itens
│   │   └── produtos/     # Cardápio
│   └── config/           # Database, env
│
├── 📄 Documentação (docs/)
│   ├── Home.md
│   ├── Manual-Completo.md
│   ├── Guia-Rapido.md
│   ├── Cartilha-Visual.md
│   ├── FAQ.md
│   ├── Glossario.md
│   ├── Tutorial-*.md (4 tutoriais)
│   └── OpenClaw-Integration.md
│
├── 🤖 MCP Server (mcp-server/)
│   ├── src/index.ts      # v1.1.0 (auto-refresh)
│   ├── dist/index.js     # Compilado
│   └── openclaw-mcporter.json
│
└── 📄 Configuração
    ├── prisma/schema.prisma
    ├── docker-compose.yml
    └── ecosystem.config.js
```

---

## ✅ Funcionalidades Implementadas

### API Endpoints
| Módulo | Endpoints | Status |
|--------|-----------|--------|
| Auth | POST /auth/login, /auth/refresh | ✅ |
| Pessoas | CRUD completo | ✅ |
| Comandas | CRUD + itens + pagamentos | ✅ |
| Produtos | Listagem + busca | ✅ |

### MCP Server (Ferramentas)
| Ferramenta | Descrição | Status |
|------------|-----------|--------|
| criar_pessoa | Cria cliente + comanda | ✅ |
| listar_produtos | Cardápio | ✅ |
| adicionar_consumo | Adiciona item | ✅ |
| consultar_saldo | Ver gastos | ✅ |
| registrar_pagamento | Receber pagamento | ✅ |
| listar_comandas | Ver comandas ativas | ✅ |

### Documentação
| Documento | Tipo | Status |
|-----------|------|--------|
| Manual Completo | Guia detalhado | ✅ Publicado |
| Guia Rápido | Referência | ✅ Publicado |
| Cartilha Visual | Cenários | ✅ Publicado |
| FAQ | Perguntas | ✅ Publicado |
| Glossário | Termos | ✅ Publicado |
| 4 Tutoriais | Passo a passo | ✅ Publicados |

---

## 🔗 URLs Importantes

### Produção
- **API:** https://72.60.49.106
- **Swagger:** https://72.60.49.106/docs
- **Docs Wiki:** https://github.com/dkamioka/baiten-docs
- **Docs Site:** https://dkamioka.github.io/baiten-docs/

### Repositórios
- **Código:** https://github.com/dkamioka/BaitenANC-backend
- **Docs:** https://github.com/dkamioka/baiten-docs

---

## 🔧 Configuração do Sistema

### Credenciais Padrão
```
Admin: admin@baiten.com.br / admin123
```

### Banco de Dados
```
Tipo: PostgreSQL 15
Host: localhost (VPS)
Porta: 5433
Database: baiten
```

### MCP Server (VPS)
```
Caminho: /var/www/baiten-mcp/
Wrapper: /var/www/baiten-mcp/mcp-wrapper.sh
Versão: 1.1.0 (com auto-refresh)
```

---

## 🚀 Integração OpenClaw

### Formato Correto (mcporter)
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

### Comando de Teste
```bash
mcporter call --stdio "/var/www/baiten-mcp/mcp-wrapper.sh" listar_produtos
```

---

## ⚠️ Pontos de Atenção

### 1. Token JWT
- **Access Token:** 15 minutos (auto-renovado pelo MCP)
- **Refresh Token:** 7 dias
- **Solução:** MCP Server v1.1.0 renova automaticamente

### 2. Certificado SSL
- **Tipo:** Self-signed (autossinado)
- **Warning:** Browsers mostram alerta de segurança
- **Solução:** Aceitar exceção ou usar Let's Encrypt

### 3. Backup
- **Banco:** Configurar backup automático do PostgreSQL
- **Código:** GitHub como backup principal

---

## 📋 Próximos Passos Sugeridos

### Prioridade Alta
1. [ ] Testar integração completa com OpenClaw
2. [ ] Configurar WhatsApp Business API
3. [ ] Testar fluxo de conversa real

### Prioridade Média
4. [ ] Configurar backup automático do banco
5. [ ] Implementar Let's Encrypt para SSL válido
6. [ ] Criar dashboard administrativo

### Prioridade Baixa
7. [ ] Adicionar relatórios de vendas
8. [ ] Implementar notificações push
9. [ ] Criar app mobile

---

## 🆘 Troubleshooting Rápido

### Token Expirado
```bash
# O MCP Server renova automaticamente!
# Se precisar manual:
curl -X POST https://72.60.49.106/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@baiten.com.br","senha":"admin123"}' \
  --insecure
```

### API Offline
```bash
# SSH no servidor
ssh root@72.60.49.106

# Verificar status
pm2 status
pm2 logs baitenanc

# Restartar
pm2 restart baitenanc
```

### MCP Server com Erro
```bash
# Testar manualmente
cd /var/www/baiten-mcp
./mcp-wrapper.sh

# Ver logs
# (O MCP loga no stderr)
```

---

## 📞 Contatos e Acesso

### VPS
```
SSH: ssh root@72.60.49.106
Chave: ~/.ssh/baitenanc_deploy (local)
```

### API
```
URL Base: https://72.60.49.106
Swagger: https://72.60.49.106/docs
```

---

## 📝 Notas Finais

Este projeto está **pronto para produção** e uso real com clientes.

Para continuar:
1. Acesse a documentação: https://dkamioka.github.io/baiten-docs/
2. Teste a API: https://72.60.49.106/docs
3. Configure o OpenClaw seguindo o guia na documentação

---

**Snapshot criado em:** 04/03/2025  
**Último commit:** 16e9e2a (feat: adiciona auto-refresh de token JWT no MCP Server)
