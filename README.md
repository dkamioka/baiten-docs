# 📚 Baiten ANC - Documentação Oficial

Bem-vindo à documentação oficial do **Baiten ANC** - Sistema de Comandas Digital para Restaurantes e Bares.

---

## 🚀 Acesse a Documentação

👉 **[Home](Home.md)** - Comece por aqui

---

## 📖 Documentos Principais

### 👤 Para Usuários (Não Técnicos)

| Documento | Descrição |
|-----------|-----------|
| **[Manual Completo](Manual-Completo.md)** | Guia detalhado completo do sistema |
| **[Guia Rápido](Guia-Rapido.md)** | Referência rápida para imprimir no caixa |
| **[Cartilha Visual](Cartilha-Visual.md)** | Exemplos e cenários reais de uso |
| **[FAQ](FAQ.md)** | Perguntas frequentes |
| **[Glossário](Glossario.md)** | Termos técnicos explicados |

### 🎓 Tutoriais Passo a Passo

| Tutorial | Descrição |
|----------|-----------|
| **[Primeiro Cliente](Tutorial-Primeiro-Cliente.md)** | Do início ao fim com um cliente |
| **[Usando Fiado](Tutorial-Usando-Fiado.md)** | Trabalhando com limite de crédito |
| **[Dividindo Conta](Tutorial-Dividindo-Conta.md)** | Atendendo grupos e mesas |
| **[Pagamento Parcial](Tutorial-Pagamento-Parcial.md)** | Quando cliente paga aos poucos |

### 🔧 Para Técnicos

| Documento | Descrição |
|-----------|-----------|
| **[MCP Server](MCP-Server-Visao-Geral.md)** | Visão geral do servidor de integração |
| **[OpenClaw Integration](OpenClaw-Integration.md)** | Integração com agente WhatsApp |
| **[Deploy do MCP Server](Deploy-do-MCP-Server.md)** | Instalação na VPS |
| **[Configuração do Ambiente](Configuracao-do-Ambiente.md)** | Setup dev e produção |

---

## 🎯 O que é o Baiten?

O **Baiten ANC** é um sistema de **comandas digitais** que ajuda restaurantes, bares e estabelecimentos similares a gerenciarem consumos dos clientes de forma simples e organizada.

### Funcionalidades Principais

- ✅ Abrir comandas para clientes
- ✅ Registrar consumos (pratos, bebidas, serviços)
- ✅ Acompanhar gastos em tempo real
- ✅ Controlar limites de crédito
- ✅ Registrar pagamentos parciais ou totais
- ✅ Fechar comandas no final

---

## 🔄 Jornadas de Uso

```
┌─────────────────────────────────────────────────────────────┐
│  1. CLIENTE NOVO                                            │
│     Criar Pessoa → Comanda aberta automaticamente           │
│     → Adicionar consumos → Pagar → Fechar                   │
├─────────────────────────────────────────────────────────────┤
│  2. CLIENTE FREQUENTE (FIADO)                               │
│     Buscar cliente → Ver limite → Adicionar consumos        │
│     → Pagar depois ou acumular                              │
├─────────────────────────────────────────────────────────────┤
│  3. PAGAMENTO PARCIAL                                       │
│     Consultar saldo → Pagar parte → Continuar consumindo    │
│     → Pagar resto → Fechar                                  │
├─────────────────────────────────────────────────────────────┤
│  4. MESA COM VÁRIAS PESSOAS                                 │
│     Criar comanda para cada um → Anotar separado            │
│     → Cada um paga a sua                                    │
└─────────────────────────────────────────────────────────────┘
```

---

## 🆘 Precisa de Ajuda?

Consulte nosso **[FAQ](FAQ.md)** ou veja a **[Cartilha Visual](Cartilha-Visual.md)** com exemplos práticos.

---

## 🔗 Links

- **Repositório Principal:** https://github.com/dkamioka/BaitenANC-backend
- **API:** https://72.60.49.106
- **Swagger:** https://72.60.49.106/docs

---

**Versão:** 1.0 | **Última atualização:** Março 2025
