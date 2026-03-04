# 🎓 Tutorial: Usando Fiado (Limite de Crédito)

Aprenda a trabalhar com clientes que têm permissão para consumir e pagar depois.

---

## 📋 Cenário

**Maria Oliveira** é cliente frequente do restaurante. Ela tem um **limite de crédito** de R$ 500 e já está usando parte desse limite.

---

## O que é "Fiado"?

Fiado é quando o cliente **consome agora** e **paga depois**. No Baiten, isso é controlado pelo **Limite de Crédito**.

```
┌─────────────────────────────────────────┐
│  LIMITE DE CRÉDITO                      │
├─────────────────────────────────────────┤
│                                         │
│  💰 Limite total:      R$ 500,00       │
│  📊 Já usou:           R$ 320,00       │
│  ✅ Ainda pode usar:   R$ 180,00       │
│                                         │
│  Maria pode consumir até R$ 180        │
│  antes de precisar pagar               │
│                                         │
└─────────────────────────────────────────┘
```

---

## Passo 1: Buscar Cliente Existente

### Por que buscar?
Maria já é cadastrada. Não precisamos criar uma nova pessoa!

### Como fazer
1. Função: **"Listar Comandas"** ou buscar por nome
2. Filtre por: **Ativas**
3. Procure: **Maria Oliveira**

### Resultado
```
✅ Cliente encontrado: Maria Oliveira
✅ Comanda ativa: #XYZ789
✅ Limite: R$ 500,00
```

---

## Passo 2: Consultar Situação Atual

Antes de adicionar novos consumos, verifique o saldo:

```
📋 Comanda de Maria Oliveira
💰 Limite:     R$ 500,00
📊 Consumido:  R$ 320,00
✅ Disponível: R$ 180,00

Status: Ativa desde 01/03/2025
```

### Interpretando os números

| Valor | Significado | Situação |
|-------|-------------|----------|
| R$ 500 | O máximo que Maria pode acumular | Limite total |
| R$ 320 | Quanto ela já consumiu este mês | Saldo atual |
| R$ 180 | Quanto ainda pode consumir | Disponível |

**Barra visual:**
```
[██████████████████████████░░░░░░░░░░░░]
       64% usado          36% disponível
       (R$ 320)           (R$ 180)
```

---

## Passo 3: Adicionar Novo Consumo

### Situação
Maria quer pedir um **drink especial (R$ 35)**.

### Verificação
```
Disponível: R$ 180
Novo pedido: R$ 35
Resultado: R$ 145 ainda disponível ✅

Não ultrapassa o limite! Pode adicionar.
```

### Como fazer
1. **Adicionar Consumo**
2. Comanda: **#XYZ789**
3. Produto: **Drink Especial**
4. Quantidade: **1**

### Resultado
```
✅ Adicionado: 1x Drink Especial
💰 Valor: R$ 35,00

Novo saldo: R$ 355,00
Disponível: R$ 145,00
```

---

## Situação Especial: Ultrapassar o Limite

### O que acontece?

Maria pede uma **garrafa de vinho (R$ 200)**, mas só tem **R$ 145** disponível.

```
⚠️ ATENÇÃO: LIMITE SERÁ ULTRAPASSADO!

Limite:        R$ 500,00
Já usou:       R$ 355,00
Disponível:    R$ 145,00
               ─────────
Novo item:     R$ 200,00
               ─────────
Nova dívida:   R$ 555,00 ❌
Ultrapassa:    R$ 55,00   ❌
```

### O que você deve fazer?

#### Opção 1: Pagamento Parcial (Recomendado)
```
Você: "Maria, esse vinho é R$ 200. Você está com R$ 355 na conta
      e tem R$ 145 de limite. Se eu adicionar, vai ultrapassar
      R$ 55. Quer fazer um pagamento parcial primeiro?"

Maria: "Sim, vou pagar R$ 100 no cartão."

[Você registra pagamento de R$ 100]

Novo saldo: R$ 255
Disponível: R$ 245

Agora pode adicionar o vinho de R$ 200! ✅
```

#### Opção 2: Autorização do Gerente
```
Você: "Maria, esse pedido vai ultrapassar seu limite em R$ 55.
      Preciso falar com o gerente para autorizar."

[Chama gerente]

Gerente: "Tudo bem, pode adicionar."

[Adiciona com autorização]
```

#### Opção 3: Sugerir Alternativa
```
Você: "Maria, o vinho vai ultrapassar seu limite.
      Temos um vinho similar por R$ 120 que cabe
      no seu limite. Quer experimentar?"
```

---

## Passo 4: Quando Maria Quer Pagar

### Situação
Final do mês, Maria veio pagar a dívida.

### Consultando a dívida total
```
📋 Resumo da Comanda #XYZ789
Cliente: Maria Oliveira

💰 Limite:     R$ 500,00
📊 Consumido:  R$ 555,00  ← Ultrapassou!
✅ Disponível: R$ 0,00    ← Limite esgotado

Histórico de Consumos:
• 05/03 - Almoço executivo    R$ 45,00
• 10/03 - Jantar + vinho      R$ 180,00
• 15/03 - Bebidas             R$ 85,00
• 20/03 - Jantar romântico    R$ 120,00
• 25/03 - Drink + vinho       R$ 125,00
                              ─────────
Total:                        R$ 555,00

Pagamentos realizados:
• 10/03 - Cartão              R$ 100,00
                              ─────────
SALDO DEVIDO:                 R$ 455,00
```

### Registrando o Pagamento

Maria vai pagar **R$ 455** no PIX:

```
✅ Pagamento registrado!
💰 Pago: R$ 455,00 via PIX
📊 Saldo: R$ 0,00

Comanda #XYZ789 pode ser fechada! ✅
```

---

## 📊 Situações de Limite

### Situação 1: Dentro do Limite ✅
```
Limite: R$ 500
Saldo:  R$ 200
Pedido: R$ 100

Resultado: Novo saldo R$ 300 (dentro do limite) ✅
Ação: Pode adicionar normalmente
```

### Situação 2: Próximo do Limite ⚠️
```
Limite: R$ 500
Saldo:  R$ 450
Pedido: R$ 100

Resultado: Ultrapassa em R$ 50 ⚠️
Ação: Avisar cliente, pedir pagamento parcial
```

### Situação 3: Limite Esgotado ❌
```
Limite: R$ 500
Saldo:  R$ 500
Pedido: R$ 50

Resultado: Ultrapassa em R$ 50 ❌
Ação: Só adiciona após pagamento
```

---

## 💡 Dicas para Trabalhar com Fiado

### Para Atendentes

1. **Sempre consulte o saldo antes** de pedidos grandes
2. **Aviso educado:** "Você está com R$ X na conta, limite de R$ Y"
3. **Ofereça soluções:** "Quer fazer um pagamento parcial?"
4. **Não seja constrangedor:** Clientes de fiado são bons clientes!

### Para Gerentes

1. **Defina limites realistas:**
   - Cliente novo: Comece baixo (R$ 100-200)
   - Cliente antigo e pontual: Pode aumentar

2. **Acompanhe regularmente:**
   - Liste comandas ativas semanalmente
   - Identifique clientes próximos do limite

3. **Política de ultrapassagem:**
   - Defina se permite ou não exceder
   - Comunique à equipe

---

## 🎯 Resumo Visual

```
LIMITE DE CRÉDITO = CARTÃO DE CRÉDITO DO RESTAURANTE

┌────────────────────────────────────────┐
│  LIMITE: R$ 500 (teto máximo)         │
├────────────────────────────────────────┤
│  • Pode usar até R$ 500               │
│  • Quando chegar perto, precisa pagar │
│  • Pagando, libera espaço de novo     │
│  • Não paga juros (só o consumo)      │
└────────────────────────────────────────┘
```

---

## ✅ Checklist para Fiado

### Ao atender cliente com limite:
- [ ] Verificar limite disponível
- [ ] Avisar quando estiver próximo do limite (>80%)
- [ ] Oferecer pagamento parcial se ultrapassar
- [ ] Anotar autorização do gerente quando necessário

### Ao receber pagamento:
- [ ] Confirmar valor recebido
- [ ] Informar novo saldo disponível
- [ ] Agradecer (cliente de fiado é cliente fiel!)

---

## 📚 Próximos Passos

- [[Tutorial: Pagamento Parcial]] - Quando cliente paga parte
- [[Tutorial: Primeiro Cliente]] - Revisar conceitos básicos
- [[FAQ]] - Perguntas frequentes sobre limites

---

*Lembre-se: Fiado é uma ferramenta para fidelizar clientes. Use com responsabilidade!*
