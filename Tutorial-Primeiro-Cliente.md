# 🎓 Tutorial: Seu Primeiro Cliente

Guia passo a passo para atender um cliente do início ao fim.

---

## 📋 Cenário

**João Silva** chegou no seu restaurante pela primeira vez. Ele quer sentar, fazer um pedido e pagar no final.

---

## Passo 1: Criar o Cliente (2 minutos)

### O que fazer
```
┌─────────────────────────────────────────────────────┐
│  AÇÃO: Criar pessoa no sistema                      │
└─────────────────────────────────────────────────────┘
```

### Como fazer
1. Abra a função **"Criar Pessoa"**
2. Preencha:
   - **Nome:** João Silva (obrigatório)
   - **Telefone:** (11) 99999-9999 (recomendado)
3. Clique em **Salvar**

### O que acontece
```
✅ Pessoa criada: João Silva
✅ Comanda aberta automaticamente: #ABC123
```

### 💡 Dica Importante
> **Anote o ID da comanda!** Escreva em um papelzinho: "Mesa 5 - #ABC123"

---

## Passo 2: Anotar o Pedido (3 minutos)

### O que fazer
```
┌─────────────────────────────────────────────────────┐
│  AÇÃO: Adicionar consumos na comanda #ABC123        │
└─────────────────────────────────────────────────────┘
```

### Como fazer

#### Pedido 1: 2 Cervejas
1. Função: **"Adicionar Consumo"**
2. Comanda: **#ABC123**
3. Produto: Busque "cerveja"
4. Selecione: **Cerveja Heineken (600ml)**
5. Quantidade: **2**
6. Clique em **Adicionar**

**Resultado:**
```
✅ Adicionado: 2x Cerveja Heineken
💰 Valor: R$ 24,00
```

#### Pedido 2: 1 Porção
1. Produto: Busque "batata"
2. Selecione: **Porção de Batata Frita**
3. Quantidade: **1**
4. Clique em **Adicionar**

**Resultado:**
```
✅ Adicionado: 1x Porção de Batata Frita
💰 Valor: R$ 35,00
```

---

## Passo 3: Consultar a Conta (1 minuto)

### O que fazer
```
┌─────────────────────────────────────────────────────┐
│  AÇÃO: Verificar saldo da comanda                   │
└─────────────────────────────────────────────────────┘
```

### Como fazer
1. Função: **"Consultar Saldo"**
2. Comanda: **#ABC123**
3. Veja o resultado:

```
📋 Comanda de João Silva
💰 Limite: R$ 0,00
📊 Consumido: R$ 59,00
✅ Disponível: R$ 0,00

Histórico:
• 2x Cerveja Heineken - R$ 24,00
• 1x Porção Batata Frita - R$ 35,00
```

### Quando usar
- Cliente pergunta "quanto está minha conta?"
- Antes de adicionar pedidos grandes
- Para conferir se está tudo correto

---

## Passo 4: Receber o Pagamento (2 minutos)

### O que fazer
```
┌─────────────────────────────────────────────────────┐
│  AÇÃO: Registrar pagamento e fechar comanda         │
└─────────────────────────────────────────────────────┘
```

### Como fazer

#### Opção A: Pagamento Exato
1. Função: **"Registrar Pagamento"**
2. Comanda: **#ABC123**
3. Valor: **59.00**
4. Forma: **PIX** (ou Dinheiro/Cartão)
5. Clique em **Registrar**

**Resultado:**
```
✅ Pagamento registrado!
💰 Pago: R$ 59,00 via PIX
📊 Saldo restante: R$ 0,00
```

#### Opção B: Pagamento com Troco
Se João pagar R$ 60 em dinheiro:

```
✅ Pagamento registrado!
💰 Pago: R$ 60,00 em dinheiro
📊 Devido: R$ 59,00
🪙 Troco: R$ 1,00
```

> 💡 **Entregue o troco de R$ 1,00 para João!**

---

## Passo 5: Fechar a Comanda (30 segundos)

### O que fazer
Com o saldo em R$ 0,00, feche a comanda:

1. Função: **"Fechar Comanda"**
2. Comanda: **#ABC123**
3. Confirme

**Resultado:**
```
✅ Comanda #ABC123 FECHADA
Status: Fechada
Total pago: R$ 59,00
```

---

## ✅ Checklist do Atendimento

Use esta lista para não esquecer nada:

### Abertura
- [ ] Perguntar nome do cliente
- [ ] Criar pessoa no sistema
- [ ] Anotar ID da comanda no papel

### Durante
- [ ] Anotar cada pedido na comanda correta
- [ ] Confirmar comanda ao adicionar ("Mesa 5, certo?")

### Fechamento
- [ ] Consultar saldo quando cliente pedir a conta
- [ ] Registrar pagamento
- [ ] Dar troco se necessário
- [ ] Fechar comanda
- [ ] Agradecer e convidar a voltar!

---

## 📝 Resumo do Fluxo

```
CLIENTE CHEGA
      │
      ▼
┌─────────────────┐
│ 1. CRIAR PESSOA │
│    João Silva   │
│    Comanda: #123│
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 2. ADICIONAR    │
│    CONSUMOS     │
│    🍺🍺🍟       │
│    R$ 59        │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 3. CONSULTAR    │
│    SALDO        │
│    Total: R$ 59 │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 4. REGISTRAR    │
│    PAGAMENTO    │
│    R$ 59 - PIX  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 5. FECHAR       │
│    COMANDA      │
│    ✅ Pronto!   │
└─────────────────┘
```

---

## ⚠️ Cuidados Comuns

### ❌ Erro: Esquecer de anotar o ID
**Problema:** Quando o garçom for adicionar o pedido, não saberá qual comanda usar.

**Solução:** Sempre escreva o ID no papelzinho da mesa!

### ❌ Erro: Adicionar na comanda errada
**Problema:** O consumo vai para outro cliente.

**Solução:** Confirme antes: "Comanda do João, mesa 5, #ABC123, certo?"

### ❌ Erro: Não fechar a comanda
**Problema:** No fim do dia parece que ainda tem cliente na mesa.

**Solução:** Sempre feche a comanda após o pagamento total.

---

## 🎉 Parabéns!

Você acabou de completar seu primeiro atendimento completo no Baiten!

### Próximos Passos

- [[Tutorial: Usando Fiado]] - Aprenda sobre limites de crédito
- [[Tutorial: Dividindo Conta]] - Atenda grupos e mesas
- [[Tutorial: Pagamento Parcial]] - Quando cliente paga parte

---

*Dúvidas? Consulte o [[Manual Completo]] ou o [[FAQ]].*
