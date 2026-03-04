# 🚀 Guia Rápido - Baiten ANC
## Referência rápida para o dia a dia

---

## 🎯 Fluxo Básico (99% dos casos)

```
┌─────────────────┐     ┌──────────────┐     ┌─────────────┐     ┌──────────┐
│ 1. CRIAR PESSOA │ ──▶ │ 2. ANOTAR ID │ ──▶ │ 3. ADICIONA │ ──▶ │ 4. PAGA  │
│   (novo cliente)│     │   da comanda │     │   consumos  │     │   e fecha│
└─────────────────┘     └──────────────┘     └─────────────┘     └──────────┘
```

---

## 📱 Comandos Essenciais

### Criar Cliente Novo
```
→ Nome: (obrigatório)
→ Telefone: (recomendado)
→ Sistema devolve: ID da comanda (ex: #A7B3C9)

💡 Dica: Anote o ID no papelzinho da mesa!
```

### Adicionar Pedido
```
→ ID da comanda: #A7B3C9
→ Produto: Cerveja
→ Quantidade: 2
→ Sistema calcula total automaticamente
```

### Consultar Conta
```
→ ID da comanda: #A7B3C9
→ Sistema mostra:
   💰 Total devido: R$ 85,00
   💳 Limite: R$ 200,00
   ✅ Disponível: R$ 115,00
```

### Registrar Pagamento
```
→ ID da comanda: #A7B3C9
→ Valor: 85.00
→ Forma: PIX (ou dinheiro/cartão)
→ Sistema confirma e dá troco se necessário
```

---

## 🔄 Jornadas Comuns

### Cliente Novo 🆕
1. Criar pessoa → sistema abre comanda automaticamente
2. Anotar ID da comanda
3. Adicionar consumos
4. Pagamento → fecha comanda

### Cliente Frequente 💳
1. Buscar cliente existente
2. Ver limite disponível
3. Adicionar consumos
4. Pagar (ou acumular no fiado)

### Pagamento Parcial 💵
1. Consultar saldo total
2. Registrar pagamento (valor parcial)
3. Sistema mostra: "Resta: R$ X"
4. Cliente pode continuar consumindo

### Mesa com Amigos 👥
1. Criar comanda para cada pessoa
2. Anotar consumos separadamente
3. Cada um paga a sua (ou um paga tudo)

---

## ⚠️ O que NÃO fazer

| ❌ Errado | ✅ Certo |
|-----------|----------|
| Criar pessoa duplicada | Buscar cliente existente primeiro |
| Usar comanda fechada | Abrir nova comanda |
| Esquecer de anotar ID | Sempre anotar o ID da comanda |
| Adicionar sem consultar limite | Verificar saldo antes de pedidos grandes |
| Ignorar aviso de limite excedido | Avisar gerente/cliente |

---

## 💡 Dicas de Ouro

### Para Não Errar
1. **Sempre pergunte:** "Comanda em nome de quem?"
2. **Confirme:** "Registrei 2 cervejas na comanda do João, certo?"
3. **Anote:** Papelzinho com ID na mesa evita confusão

### Para Ser Rápido
- Use buscas curtas: "cerveja" em vez de "cerveja heineken 600ml"
- Memorize os IDs das mesas fixas
- Consulte saldo antes de pedidos grandes

### Para o Cliente
- Explique: "Você está com R$ X na comanda, limite de R$ Y"
- Confirme pagamentos: "Registrei R$ 50 no PIX, resta R$ 30"
- Ofereça: "Quer que eu verifique o saldo?"

---

## 🔢 Códigos de Erro Comuns

| Erro | Significado | Solução |
|------|-------------|---------|
| "Comanda não encontrada" | ID errado ou comanda fechada | Verifique o ID ou crie nova |
| "Limite excedido" | Cliente atingiu o máximo | Peça pagamento parcial |
| "Produto não encontrado" | Busca muito específica | Use termos mais genéricos |
| "Token expirado" | Sessão técnica expirou | Chamar administrador |

---

## 📊 Tabela de Decisão

### Quando criar nova pessoa?
```
Cliente novo? ──Sim──▶ Criar pessoa
    │
    Não
    │
    ▼
Buscar existente ──Achou?──Sim──▶ Usar comanda ativa
    │
    Não
    │
    ▼
Verificar se digitou certo
```

### Quanto o cliente pode gastar?
```
Limite: R$ 500
Já usou: R$ 320
Disponível: R$ 180

Pedido novo: R$ 200
Resultado: ⚠️ ULTRAPASSA em R$ 20

Ação: Avise o cliente ou peça pagamento parcial
```

---

## 🎨 Cores e Significados

- 🟢 **Comanda Ativa** = Aberta, aceitando pedidos
- 🔴 **Comanda Fechada** = Paga, não aceita mais nada
- ⚫ **Cancelada** = Anulada (erro ou desistência)
- 💰 **Saldo** = Quanto deve (quanto maior, mais deve)
- ✅ **Disponível** = Quanto ainda pode gastar

---

## 📞 Quando Pedir Ajuda

**Chame seu supervisor se:**
- Cliente quer cancelar algo já adicionado
- Sistema não aceita pagamento
- Dúvida sobre limites de crédito
- Precisa reabrir comanda fechada

**Chame o técnico se:**
- Sistema não conecta (offline)
- Mensagens de "token" ou "API"
- Erros estranhos persistentes

---

## 📝 Checklist Diário

### Abertura ▶️
- [ ] Sistema online
- [ ] Nenhuma comanda ativa do dia anterior

### Atendimento 🍽️
- [ ] Nome anotado corretamente
- [ ] ID da comanda no papelzinho
- [ ] Consumos na comanda certa
- [ ] Pagamento confirmado

### Fechamento ⏹️
- [ ] Todas as comandas zeradas foram fechadas
- [ ] Nenhuma comanda "esquecida"
- [ ] Caixa conferido

---

## 🎓 Quiz Rápido (Teste seus conhecimentos!)

**1. Um cliente chega pela primeira vez. O que faz?**
   - [ ] Procurar no sistema
   - [x] Criar pessoa nova
   - [ ] Pedir para voltar depois

**2. Cliente tem limite de R$ 100, já usou R$ 80. Quer pedir R$ 30.**
   - [ ] Aceita de boa
   - [ ] Cancela o pedido
   - [x] Avisa que ultrapassa R$ 10

**3. Cliente pagou R$ 50 de R$ 45. O que acontece?**
   - [ ] Erro no sistema
   - [x] Troco de R$ 5
   - [ ] Não aceita

**4. Uma pessoa pode ter quantas comandas ativas?**
   - [x] Apenas 1
   - [ ] Quantas quiser
   - [ ] No máximo 3

---

*Guia Rápido Baiten ANC - v1.0*  
*Imprima e deixe próximo ao caixa!*
