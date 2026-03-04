# 📖 Glossário

Termos e definições usados no sistema Baiten ANC.

---

## A

### API
Interface que conecta diferentes sistemas. No Baiten, é a "ponte" entre o aplicativo que você usa e o banco de dados onde as informações são guardadas.

### Ativa (Status da Comanda)
Comanda que está **aberta** e aceitando novos consumos e pagamentos.

---

## C

### Cliente
Ver **Pessoa**.

### Comanda
Uma "conta aberta" para um cliente. É como uma folha onde são anotados todos os consumos e pagamentos de uma pessoa durante a visita ao estabelecimento.

**Comanda Ativa:** Aberta, aceitando pedidos  
**Comanda Fechada:** Paga e encerrada  
**Comanda Cancelada:** Anulada (erro ou desistência)

### Consumo
Qualquer item adicionado à comanda: pratos, bebidas, porções, serviços (como couvert artístico).

---

## D

### Débito
Ver **Saldo**.

### Disponível
Valor que o cliente **ainda pode gastar** dentro do limite de crédito.

**Fórmula:** Limite - Saldo = Disponível

---

## F

### Fechada (Status da Comanda)
Comanda que foi **paga totalmente** e encerrada. Não aceita mais consumos nem pagamentos.

### Fiado
Quando o cliente consome agora e paga depois. Só é permitido para clientes com **limite de crédito** configurado.

---

## I

### ID
Código único de identificação. Cada comanda tem um ID (ex: "abc-123-def") que serve para localizá-la no sistema.

### Item da Comanda
Ver **Consumo**.

---

## L

### Limite de Crédito
Valor máximo que um cliente pode acumular em consumos antes de precisar pagar.

- **Limite 0:** Cliente precisa pagar na hora (sem fiado)
- **Limite 500:** Cliente pode acumular até R$ 500 em consumos

---

## P

### Pagar
Quando o cliente dá dinheiro (ou PIX, cartão) para abater o valor da comanda.

### Pagamento Parcial
Quando o cliente paga **uma parte** do total devido. A comanda continua ativa com o valor restante.

Exemplo: Deve R$ 100, pagou R$ 40. Continua devendo R$ 60.

### Pessoa
Cadastro de um cliente no sistema. Contém:
- Nome (obrigatório)
- Telefone, e-mail, CPF (opcionais)
- Limite de crédito

### PIX
Forma de pagamento eletrônico instantânea (sistema do Banco Central do Brasil).

### Produto
Item disponível para venda no estabelecimento. Cada produto tem:
- Nome
- Preço
- Categoria (bebidas, pratos, etc.)

---

## R

### Registrar
Ato de anotar/salvar informações no sistema.

---

## S

### Saldo
Valor total que o cliente **consumiu** e ainda **não pagou**.

- Saldo **0:** Cliente não deve nada
- Saldo **150:** Cliente deve R$ 150

### Status
Situação atual da comanda:
- **Ativa:** Aberta
- **Fechada:** Paga e encerrada
- **Cancelada:** Anulada

---

## T

### Token
Código técnico de acesso ao sistema (usado por desenvolvedores e técnicos).

### Troco
Valor que o estabelecimento devolve ao cliente quando ele paga **mais** que o devido.

Exemplo: Conta R$ 45, cliente pagou R$ 50. Troco: R$ 5.

---

## U

### Ultrapassar
Quando um consumo faz o saldo ficar **maior** que o limite de crédito.

Exemplo:
- Limite: R$ 100
- Já usou: R$ 80
- Quer pedir: R$ 30
- Resultado: Ultrapassa em R$ 10 (novo saldo seria R$ 110)

---

## Z

### Zerar
Quando o saldo da comanda fica **R$ 0** (tudo foi pago).

---

## 📊 Comparativo Visual

```
┌─────────────────────────────────────────┐
│  LIMITE vs SALDO vs DISPONÍVEL         │
├─────────────────────────────────────────┤
│                                         │
│  💰 Limite:     R$ 500,00  [total]     │
│  📊 Saldo:      R$ 320,00  [usado]     │
│  ✅ Disponível: R$ 180,00  [resta]     │
│                                         │
│  Representação visual:                  │
│  [████████████████████░░░░░░░░░░░░░░]  │
│   320 usados     180 disponíveis       │
│   (64%)          (36%)                 │
│                                         │
└─────────────────────────────────────────┘
```

---

## 🔄 Estados da Comanda

```
         NOVA COMANDA
              │
              ▼
        ┌───────────┐
        │   ATIVA   │◄──── Aceita consumos
        │   (verde) │       Aceita pagamentos
        └─────┬─────┘
              │
      ┌───────┴───────┐
      │               │
   Pagou         Cancelada
   tudo?         (erro)
      │               │
      ▼               ▼
┌───────────┐   ┌───────────┐
│  FECHADA  │   │ CANCELADA │
│  (vermelho)│   │  (cinza)  │
└───────────┘   └───────────┘
```

---

## 📝 Abreviações Comuns

| Abreviação | Significado |
|------------|-------------|
| ID | Identificador |
| API | Interface de Programação de Aplicações |
| PIX | Pagamento Instantâneo (BC) |
| CPF | Cadastro de Pessoa Física |
| Env | Environment (ambiente) |
| URL | Endereço de internet |

---

## 🌍 Em Outros Sistemas

Termos similares em outros contextos:

| Baiten | Restaurante Tradicional | Sistema de Loja |
|--------|-------------------------|-----------------|
| Comanda | Conta | Pedido |
| Consumo | Pedido | Item |
| Saldo | Total devido | Débito |
| Fechar comanda | Fechar conta | Finalizar venda |
| Limite | Fiado | Crédito |

---

*Dúvidas sobre algum termo? Consulte o [[Manual Completo]] ou pergunte ao seu supervisor.*
