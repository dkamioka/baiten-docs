# 🎓 Tutorial: Dividindo a Conta

Como atender grupos onde cada pessoa quer pagar separadamente.

---

## 📋 Cenário

**Mesa 8** com 3 amigos:
- João
- Maria  
- Pedro

Eles querem sentar juntos, mas **cada um paga sua parte**.

---

## Estratégia: Uma Comanda por Pessoa

A melhor forma de dividir é criar **comandas separadas** desde o início:

```
MESA 8
├─ João  → Comanda #J001
├─ Maria → Comanda #M002
└─ Pedro → Comanda #P003
```

---

## Passo 1: Criar as 3 Comandas

### Criar João
```
Criar Pessoa:
• Nome: João (Mesa 8)
• Resultado: Comanda #J001
```

### Criar Maria
```
Criar Pessoa:
• Nome: Maria (Mesa 8)
• Resultado: Comanda #M002
```

### Criar Pedro
```
Criar Pessoa:
• Nome: Pedro (Mesa 8)
• Resultado: Comanda #P003
```

### 💡 Organização
Anote no papel da mesa:
```
┌─────────────────────────┐
│       MESA 8            │
│                         │
│  João  → #J001          │
│  Maria → #M002          │
│  Pedro → #P003          │
│                         │
└─────────────────────────┘
```

---

## Passo 2: Anotar Pedidos Separados

### Quando cada um pede individualmente

**João pede:** 2 cervejas
```
Adicionar Consumo:
• Comanda: #J001 (João)
• Produto: Cerveja
• Quantidade: 2
• Total: R$ 24
```

**Maria pede:** 1 drink
```
Adicionar Consumo:
• Comanda: #M002 (Maria)
• Produto: Drink
• Quantidade: 1
• Total: R$ 35
```

**Pedro pede:** 1 refrigerante
```
Adicionar Consumo:
• Comanda: #P003 (Pedro)
• Produto: Refrigerante
• Quantidade: 1
• Total: R$ 8
```

### ✅ Resultado Individual
```
┌────────────────────────────────┐
│ João:  R$ 24  (2 cervejas)    │
│ Maria: R$ 35  (1 drink)       │
│ Pedro: R$ 8   (1 refri)       │
├────────────────────────────────┤
│ TOTAL MESA: R$ 67             │
└────────────────────────────────┘
```

---

## Passo 3: Lidando com Consumos Compartilhados

### O Desafio
Eles pedem uma **porção grande para dividir** (R$ 45).

### Opção 1: Dividir Igualmente (Recomendado)
```
Porção: R$ 45 ÷ 3 = R$ 15 para cada

Adicionar em cada comanda:
• #J001 (João):   R$ 15 (porção dividida)
• #M002 (Maria):  R$ 15 (porção dividida)
• #P003 (Pedro):  R$ 15 (porção dividida)

Novos totais:
• João:  R$ 24 + R$ 15 = R$ 39
• Maria: R$ 35 + R$ 15 = R$ 50
• Pedro: R$ 8  + R$ 15 = R$ 23
```

### Opção 2: Um Paga a Porção
```
Pedro quer pagar a porção inteira:

Adicionar apenas em #P003:
• #P003 (Pedro): R$ 45 (porção inteira)

Novos totais:
• João:  R$ 24
• Maria: R$ 35
• Pedro: R$ 8 + R$ 45 = R$ 53

João e Maria "devolvem" para Pedro em dinheiro depois.
```

### Opção 3: Anotar e Dividir no Final
```
Se o sistema não permitir valores fracionados:

1. Anote no papel: "Porção R$ 45 - dividir"
2. Adicione em uma comanda (ex: #J001 João)
3. No final, calcule:
   - João paga R$ 15 a menos do que aparece
   - Maria e Pedro transferem R$ 15 cada
```

---

## Passo 4: Fechando as Contas

### Situação A: Cada um paga o seu

**João paga:**
```
Consultar Saldo #J001: R$ 39
Registrar Pagamento:
• Valor: 39.00
• Forma: PIX
✅ Comanda #J001 fechada
```

**Maria paga:**
```
Consultar Saldo #M002: R$ 50
Registrar Pagamento:
• Valor: 50.00
• Forma: Cartão
✅ Comanda #M002 fechada
```

**Pedro paga:**
```
Consultar Saldo #P003: R$ 23
Registrar Pagamento:
• Valor: 23.00
• Forma: Dinheiro
✅ Comanda #P003 fechada
```

### Situação B: Um Paga por Todos

**Maria** quer pagar tudo:

```
Calcular total: R$ 39 + R$ 50 + R$ 23 = R$ 112

Maria paga R$ 112 no cartão:

Comanda #J001 (João):
• Pagamento: R$ 39
• Fechar

Comanda #M002 (Maria):
• Pagamento: R$ 50
• Fechar

Comanda #P003 (Pedro):
• Pagamento: R$ 23
• Fechar

✅ Todas as comandas fechadas!
```

**Nota:** João e Pedro "devolvem" para Maria depois (fora do sistema).

---

## 📋 Comparativo das Estratégias

| Estratégia | Quando Usar | Vantagem | Desvantagem |
|------------|-------------|----------|-------------|
| **Uma comanda por pessoa** | Grupos grandes, contas separadas | Cada um paga exatamente o que consumiu | Mais trabalho para criar |
| **Uma comanda só** | Grupos pequenos, um paga tudo | Rápido de criar | Precisa calcular divisão manualmente |
| **Dividir itens** | Consumos compartilhados | Justo para todos | Pode gerar valores quebrados |

---

## 💡 Dicas Práticas

### Para Garçons

1. **Sempre confirme:** "Vai ser tudo junto ou separado?"
2. **Anota na hora:** Não confie na memória para dividir depois
3. **Use códigos claros:**
   - João → #J001
   - Maria → #M002
   - Pedro → #P003

### Para Clientes

1. **Decidam no início:** Separado ou junto?
2. **Quem paga o que:** Definam antes de chamar o garçom
3. **Pix facilita:** Transferências entre amigos são rápidas

---

## 🔄 Fluxo Completo

```
GRUPO CHEGA NA MESA 8
          │
          ▼
┌───────────────────────┐
│ "Vai ser separado     │
│  ou junto?"           │
└───────────┬───────────┘
            │
    ┌───────┴───────┐
    │               │
  JUNTO         SEPARADO
    │               │
    ▼               ▼
┌───────────┐  ┌───────────────────┐
│ 1 comanda │  │ 1 comanda por     │
│ só        │  │ pessoa            │
│           │  │                   │
│ Anotar    │  │ Anotar separado   │
│ tudo      │  │ cada pedido       │
│ junto     │  │                   │
└─────┬─────┘  └─────────┬─────────┘
      │                  │
      │         ┌────────┴────────┐
      │         │                 │
      │    Individual      Compartilhado
      │         │                 │
      │         ▼                 ▼
      │    Vai para      Dividir valor
      │    comanda       entre todos
      │    da pessoa     ou um paga
      │                       │
      └───────────┬───────────┘
                  │
                  ▼
         ┌────────────────┐
         │ CADA UM PAGA   │
         │ SEU CONSUMO    │
         └────────────────┘
```

---

## ✅ Checklist para Mesa de Grupo

### No início:
- [ ] Perguntar se é separado ou junto
- [ ] Criar comandas (uma ou várias)
- [ ] Anotar IDs claramente

### Durante:
- [ ] Confirmar nome ao anotar pedido
- [ ] Marcar claramente itens compartilhados
- [ ] Anotar quem paga o compartilhado

### No final:
- [ ] Consultar saldo de cada comanda
- [ ] Confirmar valores individuais
- [ ] Registrar pagamentos separados
- [ ] Fechar todas as comandas

---

## ❌ Erros Comuns

### Erro 1: Misturar comandas
```
❌ Colocar a cerveja do João na comanda da Maria

✅ Sempre confirme: "Isso é para o João, comanda #J001, certo?"
```

### Erro 2: Esquecer de dividir compartilhado
```
❌ Porção de R$ 45 toda na comanda de um só

✅ Anotar no papel: "Dividir por 3 = R$ 15 cada"
```

### Erro 3: Fechar só uma comanda
```
❌ João pagou e foi embora, mas Maria e Pedro ainda estão
   → Fechou comanda #J001
   → Esqueceu que #M002 e #P003 ainda estão ativas!

✅ Verificar todas as comandas da mesa antes de considerar "livre"
```

---

## 📚 Próximos Passos

- [[Tutorial: Primeiro Cliente]] - Revisar conceitos básicos
- [[Tutorial: Usando Fiado]] - Se algum tiver limite de crédito
- [[Tutorial: Pagamento Parcial]] - Se um quiser pagar parte agora

---

*Grupos são ótimos para o faturamento! Organização é a chave.* 🎉
