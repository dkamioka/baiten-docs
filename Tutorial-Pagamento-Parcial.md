# 🎓 Tutorial: Pagamento Parcial

Quando o cliente quer pagar uma parte agora e o resto depois.

---

## 📋 Cenário

**Carlos** está com uma comanda de **R$ 200**, mas só tem **R$ 80** no momento. Ele quer pagar esses R$ 80 agora e o resto na semana que vem.

---

## O que é Pagamento Parcial?

Pagamento parcial é quando o cliente paga **menos** que o total devido. A comanda continua **aberta** com o valor restante.

```
Total devido:     R$ 200
Pagamento agora:  R$ 80  ← PARCIAL
────────────────────────
Resta pagar:      R$ 120  ← CONTINUA DEVENDO
```

---

## Passo 1: Consultar Saldo Atual

Antes de receber o pagamento, verifique o valor total:

```
📋 Comanda #C999 (Carlos)

💰 Limite:     R$ 500,00
📊 Consumido:  R$ 200,00
✅ Disponível: R$ 300,00

Histórico:
• 01/03 - Jantar      R$ 120,00
• 05/03 - Bebidas     R$ 80,00
────────────────────────────
TOTAL:               R$ 200,00
```

---

## Passo 2: Registrar Pagamento Parcial

### Como fazer

```
Registrar Pagamento:
• Comanda: #C999
• Valor: 80.00  ← Menos que os R$ 200
• Forma: PIX
```

### Resultado

```
✅ Pagamento registrado!

💰 Pago:        R$ 80,00 (PIX)
📊 Devido:      R$ 200,00
────────────────────────
✅ Diferença:   R$ 120,00 AINDA DEVER

Status: Comanda continua ATIVA ⏳
```

---

## Passo 3: Situação Após o Pagamento

### Consultando novamente

```
📋 Comanda #C999 (Carlos) - ATUALIZADA

💰 Limite:     R$ 500,00
📊 Consumido:  R$ 120,00  ← Diminuiu!
✅ Disponível: R$ 380,00  ← Aumentou!

Pagamentos realizados:
• 10/03 - PIX         R$ 80,00

Resta pagar:         R$ 120,00 ⏳
```

### O que mudou?

| Antes | Depois | Mudança |
|-------|--------|---------|
| Saldo: R$ 200 | Saldo: R$ 120 | ↓ Diminuiu R$ 80 |
| Disponível: R$ 300 | Disponível: R$ 380 | ↑ Aumentou R$ 80 |

---

## Passo 4: Continuar Consumindo

### Situação
Na semana seguinte, Carlos volta ao restaurante.

**Ele ainda deve R$ 120**, mas quer pedir mais coisas.

```
Limite disponível: R$ 380
Novo pedido:       R$ 50

Resultado: Pode pedir! ✅
Novo saldo: R$ 120 + R$ 50 = R$ 170
```

### Adicionando novo consumo

```
Adicionar Consumo:
• Comanda: #C999
• Produto: Prato do dia
• Quantidade: 1
• Valor: R$ 50

Resultado:
✅ Adicionado: 1x Prato do dia
💰 Valor: R$ 50,00

Novo saldo total: R$ 170,00
```

---

## Passo 5: Pagamento Final

### Semana seguinte...

Carlos veio pagar o restante. Agora ele deve **R$ 170**.

```
Consultar Saldo #C999:
• Consumos: R$ 170
• Pagamentos anteriores: R$ 80
• SALDO DEVIDO: R$ 170
```

### Registrando pagamento final

```
Registrar Pagamento:
• Comanda: #C999
• Valor: 170.00
• Forma: Cartão

Resultado:
✅ Pagamento registrado!
💰 Pago: R$ 170,00 (Cartão)
📊 Saldo: R$ 0,00

🎉 Comanda #C999 pode ser FECHADA!
```

---

## 📊 Fluxo Completo do Pagamento Parcial

```
┌─────────────────────────────────────────┐
│ DIA 1 - Carlos faz pedidos              │
│                                         │
│ Consumos:                               │
│   • Jantar    R$ 120                    │
│   • Bebidas   R$ 80                     │
│   ─────────────────                     │
│   TOTAL:      R$ 200 🔴                 │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│ DIA 1 - Pagamento parcial               │
│                                         │
│ Pagou: R$ 80 em PIX                     │
│                                         │
│ Resta: R$ 120 ⏳                        │
│ Status: COMANDA ATIVA                   │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│ DIA 7 - Carlos volta e pede mais        │
│                                         │
│ Novo consumo: R$ 50                     │
│                                         │
│ Saldo atualizado: R$ 170 ⏳             │
│ (120 + 50)                              │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│ DIA 7 - Pagamento final                 │
│                                         │
│ Pagou: R$ 170 no cartão                 │
│                                         │
│ Saldo: R$ 0 ✅                          │
│ Status: COMANDA FECHADA                 │
└─────────────────────────────────────────┘
```

---

## 💡 Quando Usar Pagamento Parcial?

### Situações Comuns

#### 1. Cliente sem dinheiro suficiente
```
"Só tenho R$ 50 no momento, pago o resto sexta."
→ Registra R$ 50
→ Resta R$ X
→ Comanda continua ativa
```

#### 2. Quer dividir entre dias
```
"Hoje pago metade, semana que vem pago o resto."
→ Registra metade
→ Continua consumindo ou não
→ Semana que vem quita
```

#### 3. Vários amigos, pagam em horários diferentes
```
João paga R$ 30 agora
Maria paga R$ 40 mais tarde
Pedro paga R$ 30 no fim
→ Cada um paga quando pode
→ Comanda só fecha quando zerar
```

---

## ⚠️ Cuidados Importantes

### 1. Não confunda com Fiado

| Pagamento Parcial | Fiado (Limite) |
|-------------------|----------------|
| Paga **parte** do que consumiu | Consome **sem pagar** |
| Reduz o saldo imediatamente | Acumula até o limite |
| Pode ser em qualquer cliente | Só clientes com limite |

### 2. Controle os pagamentos

Sempre registre **todos** os pagamentos parciais:

```
Histórico de Pagamentos #C999:
• 10/03 - PIX       R$ 80
• 15/03 - Dinheiro  R$ 50
• 17/03 - Cartão    R$ 70
───────────────────────────
TOTAL PAGO:        R$ 200 ✅
```

### 3. Comandas ativas por muito tempo

```
⚠️ ATENÇÃO:

Comanda #C999 está ativa há 30 dias!
• Saldo: R$ 50
• Último pagamento: 20 dias atrás

Ação: Entrar em contato com Carlos
```

---

## 📋 Comparativo: Estratégias de Pagamento

| Estratégia | Quando Usar | Vantagem | Cuidado |
|------------|-------------|----------|---------|
| **Pagamento total** | Cliente tem dinheiro | Fecha comanda imediatamente | Nenhum |
| **Pagamento parcial** | Cliente vai pagar em partes | Flexibilidade | Acompanhar saldo restante |
| **Fiado (limite)** | Cliente de confiança | Não precisa pagar toda hora | Controlar limite |

---

## ✅ Checklist para Pagamento Parcial

### Ao receber pagamento parcial:
- [ ] Confirmar valor recebido
- [ ] Informar saldo restante claramente
- [ ] Explicar que comanda continua aberta
- [ ] Registrar pagamento imediatamente

### Acompanhamento:
- [ ] Verificar comandas com saldo > 7 dias
- [ ] Contatar cliente se muito tempo sem pagar
- [ ] Fechar comanda quando saldo zerar

---

## 🎯 Resumo Visual

```
PAGAMENTO PARCIAL = PAGAR POUCO A POUCO

┌────────────────────────────────────────┐
│ Total: R$ 200                          │
│                                         │
│ Pagamento 1: R$ 80   ████░░░░░░░░░░   │
│ Pagamento 2: R$ 50   ███░░░░░░░░░░░   │
│ Pagamento 3: R$ 70   ████░░░░░░░░░░   │
│                      ────────────────  │
│ Total pago:  R$ 200  ██████████████   │
│ ✅ COMANDA FECHADA                     │
└────────────────────────────────────────┘
```

---

## ❌ Erros Comuns

### Erro 1: Esquecer de registrar
```
❌ "Carlos me deu R$ 50, mas não registrei no sistema"
   → Sistema ainda mostra R$ 200
   → Carlos é cobrado duas vezes!

✅ Sempre registre IMEDIATAMENTE
```

### Erro 2: Não informar saldo restante
```
❌ "Obrigado!" (sem explicar que ainda deve)
   → Carlos acha que quitou
   → Surpresa na próxima visita

✅ "Registrei R$ 50! Restam R$ 120 para quitar."
```

### Erro 3: Fechar comanda com saldo
```
❌ Fechar comanda #C999 com saldo de R$ 50
   → Carlos "some" com a dívida
   → Perda financeira

✅ Só feche quando saldo for R$ 0
```

---

## 📚 Próximos Passos

- [[Tutorial: Usando Fiado]] - Diferença entre pagamento parcial e fiado
- [[Tutorial: Primeiro Cliente]] - Revisar fluxo básico
- [[FAQ]] - Mais dúvidas sobre pagamentos

---

*Pagamento parcial é uma ferramenta de flexibilidade. Use com organização!* 💰
