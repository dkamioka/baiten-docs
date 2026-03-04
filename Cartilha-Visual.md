# 🎨 Cartilha Visual - Baiten ANC
## Entenda o sistema em 5 minutos

---

## 🎬 Cena 1: "Bom dia, primeira vez aqui?"

### Situação
João chega no seu restaurante pela primeira vez.

### O que você faz

```
┌─────────────────────────────────────────────────────┐
│  VOCÊ: "Bem-vindo! Qual seu nome?"                  │
│                                                     │
│  JOÃO: "João Silva"                                 │
│                                                     │
│  VOCÊ: [Cria pessoa no sistema]                    │
│                                                     │
│  SISTEMA: ✅ Pessoa criada                          │
│           ✅ Comanda #ABC123 aberta automaticamente │
│                                                     │
│  VOCÊ: [Anota no papelzinho: "Mesa 5 - #ABC123"]   │
│                                                     │
│  VOCÊ: "João, sua comanda é a 123. Pode fazer      │
│         seus pedidos!"                              │
└─────────────────────────────────────────────────────┘
```

### 💡 Por que anotar o ID?
Porque quando o garçom for adicionar o pedido, ele precisa saber em qual comanda colocar!

---

## 🎬 Cena 2: "Quero 2 cervejas e uma porção"

### Situação
João está na mesa e chamou o garçom.

### O que o garçom faz

```
┌─────────────────────────────────────────────────────┐
│  GARÇOM: "Boa noite! O que vai ser?"               │
│                                                     │
│  JOÃO: "2 Heineken e uma porção de batata"         │
│                                                     │
│  GARÇOM: [No sistema]                               │
│                                                     │
│  ┌──────────────────────────────────────┐          │
│  │ Comanda: #ABC123                      │          │
│  │ Produto: "Heineken" [busca]          │          │
│  │ Resultado: 🍺 Cerveja Heineken - R$12│          │
│  │ Quantidade: 2                         │          │
│  │                                       │          │
│  │ Produto: "batata" [busca]            │          │
│  │ Resultado: 🍟 Porção Batata - R$35   │          │
│  │ Quantidade: 1                         │          │
│  └──────────────────────────────────────┘          │
│                                                     │
│  SISTEMA: ✅ Adicionado!                            │
│           💰 Total: R$ 59 (2×12 + 35)               │
│                                                     │
│  GARÇOM: "Anotei! Mais alguma coisa?"              │
└─────────────────────────────────────────────────────┘
```

### ⚠️ Cuidado!
Se não anotar na comanda certa, o pedido vai para outra pessoa!

---

## 🎬 Cena 3: "Quanto estou devendo?"

### Situação
João quer saber quanto já gastou.

### O que você faz

```
┌─────────────────────────────────────────────────────┐
│  JOÃO: "Quanto tá minha conta?"                    │
│                                                     │
│  VOCÊ: [Consulta saldo da comanda #ABC123]         │
│                                                     │
│  SISTEMA:                                           │
│  ┌──────────────────────────────────────┐          │
│  │ 📋 Comanda de João Silva             │          │
│  │                                      │          │
│  │ 💰 Limite:     R$ 0,00               │          │
│  │ 📊 Consumido:  R$ 59,00              │          │
│  │ ✅ Disponível: R$ 0,00               │          │
│  │                                      │          │
│  │ 📝 Histórico:                        │          │
│  │    • 2x Cerveja Heineken - R$ 24     │          │
│  │    • 1x Porção Batata    - R$ 35     │          │
│  └──────────────────────────────────────┘          │
│                                                     │
│  VOCÊ: "João, você está com R$ 59. São 2           │
│         Heineken e uma porção de batata."          │
└─────────────────────────────────────────────────────┘
```

### 💡 Dica
Sempre mostre os itens para o cliente confirmar que está tudo certo!

---

## 🎬 Cena 4: "Vou pagar no PIX"

### Situação
João terminou e quer pagar.

### O que você faz

```
┌─────────────────────────────────────────────────────┐
│  JOÃO: "Fecha a conta pra mim, vou pagar no PIX"   │
│                                                     │
│  VOCÊ: [Consulta saldo: R$ 59]                     │
│                                                     │
│  VOCÊ: "Ficou R$ 59. Pode fazer o PIX!"            │
│                                                     │
│  [João faz o PIX no celular]                       │
│                                                     │
│  JOÃO: "Pronto, enviei R$ 60" (quer troco)         │
│                                                     │
│  VOCÊ: [Registra pagamento]                        │
│                                                     │
│  ┌──────────────────────────────────────┐          │
│  │ Pagamento registrado!                │          │
│  │                                      │          │
│  │ 💰 Pago:    R$ 60,00 (PIX)          │          │
│  │ 📊 Devido:  R$ 59,00                │          │
│  │ 🪙 Troco:   R$ 1,00                 │          │
│  │                                       │          │
│  │ ✅ Saldo: R$ 0,00                   │          │
│  └──────────────────────────────────────┘          │
│                                                     │
│  VOCÊ: [Entrega R$ 1 de troco]                     │
│  VOCÊ: "Obrigado, João! Volte sempre!"             │
│                                                     │
│  [Fecha comanda #ABC123]                           │
└─────────────────────────────────────────────────────┘
```

### ✅ Comanda fechada!
Pronto para atender o próximo cliente.

---

## 🎬 Cena 5: "Sou cliente frequente, pode fiar?"

### Situação
Maria é cliente antiga com limite de crédito.

```
┌─────────────────────────────────────────────────────┐
│  MARIA: "Oi, sou a Maria. Põe mais um drink pra     │
│          mim na conta?"                             │
│                                                     │
│  VOCÊ: [Busca "Maria"]                              │
│                                                     │
│  SISTEMA: ✓ Maria Oliveira encontrada               │
│           ✓ Limite: R$ 500                          │
│           ✓ Comanda ativa: #XYZ789                  │
│                                                     │
│  VOCÊ: [Consulta saldo da #XYZ789]                 │
│                                                     │
│  ┌──────────────────────────────────────┐          │
│  │ 📋 Comanda de Maria Oliveira         │          │
│  │                                      │          │
│  │ 💰 Limite:     R$ 500,00  ├─────────┤          │
│  │ 📊 Consumido:  R$ 320,00  │██████░░░│ 64%      │
│  │ ✅ Disponível: R$ 180,00  ├─────────┤          │
│  └──────────────────────────────────────┘          │
│                                                     │
│  VOCÊ: "Claro, Maria! Você tem R$ 180 de limite.    │
│         O drink é R$ 25, tudo certo!"              │
│                                                     │
│  [Adiciona drink - novo saldo: R$ 345]             │
└─────────────────────────────────────────────────────┘
```

### 📊 Barra de Progresso Visual
Mostra quando o cliente está próximo do limite:
- 🟢 Verde: até 70% (seguro)
- 🟡 Amarelo: 70-90% (atenção)
- 🔴 Vermelho: acima de 90% (perto do limite)

---

## 🎬 Cena 6: "Ultrapassou o limite!"

### Situação
Maria pediu algo caro e vai ultrapassar o limite.

```
┌─────────────────────────────────────────────────────┐
│  MARIA: "Essa garrafa de vinho é boa? Quero uma!"  │
│                                                     │
│  VOCÊ: "É R$ 120 a garrafa. Deixa eu ver sua       │
│         comanda..."                                 │
│                                                     │
│  SISTEMA:                                           │
│  ┌──────────────────────────────────────┐          │
│  │ ⚠️ LIMITE SERÁ ULTRAPASSADO!         │          │
│  │                                      │          │
│  │ Limite:       R$ 500,00              │          │
│  │ Já usou:      R$ 345,00              │          │
│  │ Disponível:   R$ 155,00              │          │
│  │                                      │          │
│  │ Novo item:    R$ 120,00              │          │
│  │                                      │          │
│  │ Nova dívida:  R$ 465,00  ✓ OK        │          │
│  │ Ultrapassa:   R$ 0,00    ✓ Dentro    │          │
│  │                                      │          │
│  │ [SE FOSSE R$ 200:]                   │          │
│  │ Nova dívida:  R$ 545,00  ❌          │          │
│  │ Ultrapassa:   R$ 45,00   ❌          │          │
│  └──────────────────────────────────────┘          │
│                                                     │
│  VOCÊ: "Maria, o vinho é R$ 120. Você está com     │
│         R$ 345 na conta e tem R$ 155 de limite.    │
│         Vai sobrar R$ 35 só. Tudo bem?"            │
│                                                     │
│  MARIA: "Pode colocar!"                            │
│  [ou]                                               │
│  MARIA: "Ah, então paga esses R$ 345 agora e       │
│          continua a conta zerada?"                 │
└─────────────────────────────────────────────────────┘
```

### 💡 Soluções quando ultrapassa:
1. Cliente faz pagamento parcial
2. Gerente autoriza exceção
3. Cliente escolhe item mais barato

---

## 🎬 Cena 7: "A gente vai dividir"

### Situação
Mesa com 3 amigos, cada um quer pagar o seu.

```
┌─────────────────────────────────────────────────────┐
│  MESA 8 - 3 amigos                                  │
│                                                     │
│  João:  Comanda #J001                               │
│  Maria: Comanda #M002                               │
│  Pedro: Comanda #P003                               │
│                                                     │
│  CONSUMOS:                                          │
│  ┌─────────────────────────────────────┐           │
│  │ 2 Cervejas  → Comanda João  (R$ 24) │           │
│  │ 1 Drink     → Comanda Maria (R$ 35) │           │
│  │ 1 Porção    → Dividir?              │           │
│  │     Opção 1: R$ 30 só no João       │           │
│  │     Opção 2: R$ 10 em cada um       │           │
│  └─────────────────────────────────────┘           │
│                                                     │
│  RESULTADO (Opção 2 - dividir):                    │
│  ┌─────────────────────────────────────┐           │
│  │ João:  R$ 24 + R$ 10 = R$ 34        │           │
│  │ Maria: R$ 35 + R$ 10 = R$ 45        │           │
│  │ Pedro: R$ 0  + R$ 10 = R$ 10        │           │
│  └─────────────────────────────────────┘           │
│                                                     │
│  Cada um paga sua comanda separadamente!           │
└─────────────────────────────────────────────────────┘
```

---

## 🎬 Cena 8: "Paga uma parte agora, o resto depois"

### Situação
Cliente quer pagar R$ 50 agora de R$ 120.

```
┌─────────────────────────────────────────────────────┐
│  CARLOS: "Vou pagar R$ 50 no cartão agora, o       │
│           resto pago semana que vem."              │
│                                                     │
│  VOCÊ: [Registra pagamento]                        │
│                                                     │
│  ┌──────────────────────────────────────┐          │
│  │ 💳 Pagamento Parcial                 │          │
│  │                                      │          │
│  │ Total devido:   R$ 120,00            │
│  │ Pagamento:      R$ 50,00             │
│  │ Forma:          Cartão               │          │
│  │                                      │          │
│  │ ─────────────────────────            │
│  │ Ainda deve:     R$ 70,00  ⏳         │
│  └──────────────────────────────────────┘          │
│                                                     │
│  [Comanda continua ATIVA]                          │
│  [Carlos pode continuar consumindo]                │
│  [Novo saldo: R$ 70]                               │
│                                                     │
│  SEMANA QUE VEM:                                   │
│  Carlos paga R$ 70 → Comanda fecha                 │
└─────────────────────────────────────────────────────┘
```

---

## 🚫 Erros Comuns (e como evitar)

### ❌ Erro 1: Criar duplicado
```
❌ Errado:
   Atendente: "Qual seu nome?"
   João: "João Silva"
   [Cria nova pessoa...]
   
   PROBLEMA: João já tinha cadastro!
   
✅ Certo:
   Atendente: "Qual seu nome?"
   João: "João Silva"
   [Busca "João" primeiro]
   [Achou! Usa comanda existente]
```

### ❌ Erro 2: Comanda errada
```
❌ Errado:
   Garçom anota no papel: "Mesa 5"
   [Adiciona na comanda da mesa 5...]
   
   PROBLEMA: Esqueceu de ver qual ID!
   
✅ Certo:
   Garçom anota no papel: "Mesa 5 - #ABC123"
   [Adiciona na comanda #ABC123]
```

### ❌ Erro 3: Esquecer de fechar
```
❌ Errado:
   Cliente pagou, foi embora...
   [Comanda continua ATIVA no sistema]
   
   PROBLEMA: No fim do dia parece que tem cliente!
   
✅ Certo:
   Cliente pagou → Registra pagamento
   Saldo zerou → Fecha comanda
```

---

## 📋 Resumo Visual

### Estados da Comanda

```
┌────────────────┐      ┌────────────────┐      ┌────────────────┐
│   🟢 ATIVA     │      │   🔴 FECHADA   │      │   ⚫ CANCELADA │
├────────────────┤      ├────────────────┤      ├────────────────┤
│ ✓ Aceita       │      │ ✗ Não aceita   │      │ ✗ Não aceita   │
│   pedidos      │ ──▶  │   pedidos      │      │   pedidos      │
│ ✓ Aceita       │      │ ✗ Está paga    │      │ ✗ Estava       │
│   pagamentos   │      │                │      │   errada       │
└────────────────┘      └────────────────┘      └────────────────┘
       │
       │ Saldo = 0
       ▼
   Pode fechar
```

### Fluxo de Valores

```
Entrada: Cliente novo
    │
    ▼
┌─────────────────┐
│ Limite: R$ 500  │
│ Saldo:  R$ 0    │
└─────────────────┘
    │
    │ + R$ 50 (pedido 1)
    ▼
┌─────────────────┐
│ Saldo:  R$ 50   │
│ Disp:   R$ 450  │
└─────────────────┘
    │
    │ + R$ 30 (pedido 2)
    ▼
┌─────────────────┐
│ Saldo:  R$ 80   │
│ Disp:   R$ 420  │
└─────────────────┘
    │
    │ - R$ 50 (pagamento parcial)
    ▼
┌─────────────────┐
│ Saldo:  R$ 30   │
│ Disp:   R$ 470  │
└─────────────────┘
    │
    │ - R$ 30 (pagamento final)
    ▼
┌─────────────────┐
│ Saldo:  R$ 0    │
│ Status: FECHADA │
└─────────────────┘
```

---

## 🎯 Guia de Decisão (Fluxograma Simples)

```
CLIENTE CHEGOU
      │
      ▼
Já tem cadastro? ──Não──▶ CRIAR PESSOA
      │                        │
      Sim                       ▼
      │                   Comanda aberta
      ▼                        │
Buscar nome                    ▼
      │                   [Anote o ID]
      ▼                        │
Tem comanda ──Não──▶ Abrir nova comanda
  ativa?              (se permitido)
      │
      Sim
      │
      ▼
Usar comanda existente
      │
      ▼
ADICIONAR CONSUMOS
      │
      ▼
Quer saber ──Sim──▶ CONSULTAR SALDO
  saldo?              │
      │               ▼
      Não         Mostra total
      │               │
      ▼               ▼
Vai pagar ──Sim──▶ REGISTRAR PAGAMENTO
  algo?               │
      │               ▼
      Não         Zerou? ──Sim──▶ FECHAR
      │               │              COMANDA
      │               Não
      ▼               │
Continua na      Continua
mesa ativa       consumindo
```

---

*Cartilha Visual Baiten ANC - Imprima e coloque na parede da cozinha/caixa!*
