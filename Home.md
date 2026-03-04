# 🏠 Bem-vindo ao Baiten ANC Wiki

Bem-vindo à documentação oficial do **Baiten ANC** - Sistema de Comandas Digital para Restaurantes e Bares.

---

## 🚀 Comece Aqui

### 👤 Para Usuários (Atendentes, Garçons, Gerentes)

| Guia | Descrição | Ideal para |
|------|-----------|------------|
| [[Manual Completo]] | Documentação completa do sistema | Treinamento inicial, consulta detalhada |
| [[Guia Rápido]] | Referência rápida para o dia a dia | Imprimir e deixar no caixa |
| [[Cartilha Visual]] | Exemplos e cenários reais | Aprender com casos práticos |

### 🔧 Para Técnicos e Desenvolvedores

| Documento | Descrição |
|-----------|-----------|
| [[MCP Server - Visão Geral]] | Sobre o servidor de integração |
| [[OpenClaw Integration]] | Integração com agente WhatsApp |
| [[Deploy do MCP Server]] | Instalação na VPS |
| [API Swagger](https://72.60.49.106/docs) | Documentação da API (externo) |

---

## 📋 O que é o Baiten?

O **Baiten** é um sistema de **comandas digitais** que ajuda restaurantes, bares e estabelecimentos similares a gerenciarem consumos dos clientes.

### Principais Funcionalidades

- ✅ **Abrir comandas** para clientes
- ✅ **Registrar consumos** (pratos, bebidas, serviços)
- ✅ **Acompanhar gastos** em tempo real
- ✅ **Controlar limites** de crédito
- ✅ **Registrar pagamentos** parciais ou totais
- ✅ **Fechar comandas** no final

---

## 🎯 Jornadas de Uso

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

## 📚 Índice de Documentos

### Documentação de Usuário
- [[Manual Completo]] - Tudo sobre o sistema
- [[Guia Rápido]] - Consulta rápida
- [[Cartilha Visual]] - Cenários e exemplos
- [[FAQ]] - Perguntas frequentes
- [[Glossário]] - Termos técnicos explicados

### Documentação Técnica
- [[MCP Server - Visão Geral]]
- [[OpenClaw Integration]]
- [[Deploy do MCP Server]]
- [[Configuração do Ambiente]]

### Tutoriais Passo a Passo
- [[Tutorial: Primeiro Cliente]]
- [[Tutorial: Usando Fiado]]
- [[Tutorial: Dividindo Conta]]
- [[Tutorial: Pagamento Parcial]]

---

## 💡 Precisa de Ajuda?

### Problemas Comuns

| Problema | Solução Rápida | Documento |
|----------|----------------|-----------|
| Comanda não encontrada | Verifique o ID ou crie nova | [[FAQ]] |
| Limite excedido | Faça pagamento parcial | [[Cartilha Visual#Cena 6]] |
| Produto não aparece | Use busca mais genérica | [[Guia Rápido]] |
| Criou duplicado | Busque cliente existente primeiro | [[Cartilha Visual#Erros Comuns]] |

### Contatos

- **Suporte Técnico:** admin@baiten.com.br
- **API:** https://72.60.49.106
- **Swagger:** https://72.60.49.106/docs

---

## 📝 Versões

| Versão | Data | Notas |
|--------|------|-------|
| 1.0 | Março 2025 | Lançamento inicial do Wiki |

---

**Baiten ANC - Simplificando a gestão do seu estabelecimento** 🚀
