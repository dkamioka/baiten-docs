# 📘 Manual de Uso - Baiten ANC
## Sistema de Comandas Digital para Restaurantes e Bares

---

## 🎯 O que é o Baiten?

O **Baiten** é um sistema de **comandas digitais** que ajuda restaurantes, bares e estabelecimentos similares a gerenciarem consumos dos clientes de forma simples e organizada.

### Com o Baiten você pode:
- ✅ Abrir comandas para clientes
- ✅ Registrar consumos (pratos, bebidas, serviços)
- ✅ Acompanhar gastos em tempo real
- ✅ Controlar limites de crédito
- ✅ Registrar pagamentos parciais ou totais
- ✅ Fechar comandas no final

---

## 📚 Conceitos Básicos

### 📝 Pessoa (Cliente)
É qualquer pessoa que frequenta seu estabelecimento. Cada pessoa tem:
- **Nome** (obrigatório)
- Telefone, e-mail, CPF (opcionais)
- **Limite de crédito** (quanto pode gastar)

### 🧾 Comanda
É como uma "conta aberta" para um cliente. Cada comanda tem:
- Código único (ID)
- Status: **Ativa**, **Fechada** ou **Cancelada**
- **Saldo** (quanto o cliente já consumiu)
- Histórico de consumos e pagamentos

### 🛒 Consumo (Item da Comanda)
É qualquer produto ou serviço adicionado na comanda:
- Produtos: bebidas, pratos, porções
- Serviços: couvert, taxa de garçom
- Quantidade e valor unitário

### 💰 Pagamento
Quando o cliente paga parte ou tudo da comanda:
- Pode ser parcial (pagou R$ 50 de R$ 100)
- Várias formas: dinheiro, PIX, cartão
- Gera saldo devedor ou troco

---

## 🚀 Jornadas de Uso Comuns

### Jornada 1: Cliente Novo Chegando 🆕

**Cenário:** Um cliente chega pela primeira vez no estabelecimento.

```
Passo 1: Criar a pessoa
→ Sistema cria automaticamente uma comanda ativa

Passo 2: Anotar o ID da comanda
→ Exemplo: "Comanda ABC-123"
→ Pode anotar no papelzinho para o cliente

Passo 3: Cliente faz pedidos
→ Garçom adiciona consumos na comanda ABC-123

Passo 4: Cliente vai embora
→ Registra pagamento
→ Fecha a comanda
```

**Exemplo real:**
> João chega no bar. Atendente cria "João Silva" no sistema → Comanda #5501 aberta automaticamente. João pede 2 cervejas (R$ 16) e 1 porção (R$ 35). Sistema mostra saldo: R$ 51. João paga R$ 60 no PIX. Sistema registra pagamento e calcula troco: R$ 9.

---

### Jornada 2: Cliente Frequente (Fiado) 💳

**Cenário:** Cliente já cadastrado, com limite de crédito.

```
Passo 1: Buscar cliente existente
→ Sistema mostra limite disponível
→ Exemplo: "Limite: R$ 500, Usado: R$ 120, Disponível: R$ 380"

Passo 2: Usar comanda ativa ou abrir nova
→ Cliente pode ter apenas 1 comanda ativa por vez

Passo 3: Adicionar consumos
→ Sistema verifica se ultrapassa o limite
→ Se ultrapassar: avisa o atendente

Passo 4: Cliente paga depois
→ Pode fazer pagamentos parciais durante a semana
→ Ou pagar tudo no fim do mês
```

**Exemplo real:**
> Maria é cliente frequente com limite de R$ 500. Ela vai ao restaurante 3x na semana:
> - Segunda: R$ 80 → Saldo: R$ 80
> - Quarta: R$ 120 → Saldo: R$ 200
> - Sexta: R$ 150 → Saldo: R$ 350
> 
> No sábado ela tenta pedir R$ 200, mas só tem R$ 150 disponíveis. Sistema avisa: "Limite excedido! Disponível: R$ 150"

---

### Jornada 3: Pagamento Parcial 💵

**Cenário:** Cliente quer pagar uma parte agora e o resto depois.

```
Passo 1: Consultar saldo
→ "Total devido: R$ 200"

Passo 2: Registrar pagamento parcial
→ Cliente paga R$ 100 no cartão
→ Sistema atualiza: "Pago: R$ 100, Resta: R$ 100"

Passo 3: Continuar consumindo
→ Novos itens aumentam o restante
→ Ou fechar comanda quando pagar tudo
```

**Exemplo real:**
> Pedro está com R$ 250 na comanda. Paga R$ 100 no dinheiro. Resta R$ 150. Mais tarde pede mais R$ 50. Novo saldo: R$ 200. Paga mais R$ 200 no PIX. Saldo: R$ 0. Comanda pode ser fechada.

---

### Jornada 4: Mesa com Várias Pessoas 👥

**Cenário:** Grupo de amigos na mesma mesa, mas cada um com sua comanda.

```
Passo 1: Criar comanda para cada pessoa
→ João: Comanda #101
→ Maria: Comanda #102
→ Carlos: Comanda #103

Passo 2: Anotar pedidos separadamente
→ Cerveja de João → na #101
→ Drink de Maria → na #102
→ Porção compartilhada → pode dividir entre as comandas

Passo 3: Cada um paga o seu
→ Ou uma pessoa paga tudo (soma das 3 comandas)
```

**Dica:** Para consumos compartilhados (porção da mesa), você pode:
- Dividir o valor igualmente entre as comandas
- Ou colocar tudo em uma comanda e os outros pagam para essa pessoa

---

## 📖 Features em Detalhe

### 1️⃣ Criar Pessoa (Novo Cliente)

**O que faz:** Cadastra um cliente novo e abre automaticamente uma comanda para ele.

**O que precisa:**
- ✅ Nome (obrigatório)
- ℹ️ Telefone (recomendado)
- ℹ️ E-mail (opcional)
- ℹ️ CPF (opcional)

**O que acontece:**
1. Cliente é cadastrado no sistema
2. Uma comanda ativa é criada automaticamente
3. Sistema retorna o ID da comanda (ex: "abc-123-def")

**Exemplo de uso:**
```
Entrada: Nome: "Ana Paula", Telefone: "(11) 99999-9999"

Saída: 
- Pessoa criada: Ana Paula
- Comanda aberta: #A7B3C9
- Limite de crédito: R$ 0 (padrão)
```

**❌ Não pode:**
- Criar pessoa sem nome
- Ter duas comandas ativas para a mesma pessoa

---

### 2️⃣ Listar Produtos (Cardápio)

**O que faz:** Mostra todos os produtos disponíveis para venda.

**Como usar:**
- Buscar todos: lista completa
- Buscar por nome: "cerveja", "porção", "refrigerante"

**O que mostra:**
- Nome do produto
- Preço (valor unitário)
- Categoria

**Exemplo:**
```
Busca: "cerveja"

Resultado:
🍺 Cerveja Skol (600ml) - R$ 8,00
🍺 Cerveja Heineken (600ml) - R$ 12,00
🍺 Cerveja Corona (330ml) - R$ 9,00
```

**Dica:** Use buscas simples. "coxinha" funciona melhor que "coxinha de frango com catupiry grande"

---

### 3️⃣ Adicionar Consumo

**O que faz:** Coloca um produto na comanda do cliente.

**O que precisa:**
- ✅ ID da comanda (ex: "abc-123")
- ✅ ID do produto (ex: "prod-456")
- ✅ Quantidade (padrão: 1)

**O que acontece:**
1. Sistema calcula valor total (quantidade × preço unitário)
2. Adiciona na comanda
3. Atualiza o saldo
4. Verifica se ultrapassa o limite de crédito

**Exemplo:**
```
Comanda: #A7B3C9 (Ana Paula)
Produto: Cerveja Heineken (R$ 12,00)
Quantidade: 2

Resultado:
✅ Adicionado: 2x Cerveja Heineken
💰 Valor: R$ 24,00
📊 Novo saldo: R$ 24,00
```

**⚠️ Atenção:**
- Se o cliente tiver limite de R$ 100 e já estiver com R$ 90, adicionar R$ 20 vai ultrapassar o limite
- O sistema **avisa**, mas permite (depende da configuração do estabelecimento)

**❌ Não pode:**
- Adicionar produto em comanda fechada
- Adicionar quantidade negativa ou zero

---

### 4️⃣ Consultar Saldo

**O que faz:** Mostra a situação financeira da comanda.

**O que mostra:**
- Nome do cliente
- 💰 Limite de crédito total
- 📊 Saldo utilizado (quanto já consumiu)
- ✅ Disponível (quanto ainda pode usar)
- Status da comanda
- Data de abertura

**Exemplo 1 - Cliente sem limite:**
```
📋 Comanda de João Silva
💰 Limite: R$ 0,00
📊 Consumido: R$ 85,00
✅ Disponível: R$ 0,00
Status: Ativa
Aberta em: 03/03/2025 14:30
```

**Exemplo 2 - Cliente com limite:**
```
📋 Comanda de Maria Oliveira
💰 Limite: R$ 500,00
📊 Consumido: R$ 320,00
✅ Disponível: R$ 180,00
Status: Ativa
Aberta em: 01/03/2025 19:00
```

**Quando usar:**
- Cliente pergunta "quanto estou devendo?"
- Antes de adicionar consumos grandes
- Para verificar se está próximo do limite

---

### 5️⃣ Registrar Pagamento

**O que faz:** Registra que o cliente pagou parte ou tudo.

**O que precisa:**
- ✅ ID da comanda
- ✅ Valor pago (ex: 50.00)
- ✅ Forma de pagamento:
  - 💵 Dinheiro
  - 📱 PIX
  - 💳 Cartão de Crédito
  - 💳 Cartão de Débito

**O que acontece:**
1. Sistema registra o pagamento
2. Atualiza o saldo (subtrai o valor pago)
3. Calcula se sobrou troco

**Exemplo 1 - Pagamento exato:**
```
Comanda: #A7B3C9
Saldo devido: R$ 85,00
Pagamento: R$ 85,00 no PIX

Resultado:
✅ Pagamento registrado!
💰 Pago: R$ 85,00 via PIX
📊 Saldo restante: R$ 0,00
```

**Exemplo 2 - Pagamento com troco:**
```
Comanda: #A7B3C9
Saldo devido: R$ 85,00
Pagamento: R$ 100,00 em dinheiro

Resultado:
✅ Pagamento registrado!
💰 Pago: R$ 100,00 em dinheiro
🪙 Troco: R$ 15,00
📊 Saldo restante: R$ 0,00
```

**Exemplo 3 - Pagamento parcial:**
```
Comanda: #A7B3C9
Saldo devido: R$ 200,00
Pagamento: R$ 100,00 no cartão

Resultado:
✅ Pagamento registrado!
💰 Pago: R$ 100,00 no cartão
📊 Ainda deve: R$ 100,00
```

**❌ Não pode:**
- Pagar valor negativo
- Usar forma de pagamento inválida

---

### 6️⃣ Listar Comandas

**O que faz:** Mostra todas as comandas do sistema.

**Filtros disponíveis:**
- Todas
- 🟢 Ativas (abertas)
- 🔴 Fechadas (pagas e encerradas)
- ⚫ Canceladas

**O que mostra:**
- ID da comanda
- Nome do cliente
- Valor do saldo
- Status

**Exemplo:**
```
5 comandas encontradas:

#A1B2C3 - João Silva - R$ 85,00 - Ativa
#D4E5F6 - Maria Oliveira - R$ 320,00 - Ativa
#G7H8I9 - Pedro Santos - R$ 0,00 - Fechada
#J0K1L2 - Ana Paula - R$ 150,00 - Ativa
#M3N4O5 - Carlos Lima - R$ 0,00 - Cancelada
```

**Quando usar:**
- Ver todas as mesas ocupadas
- Fechar o caixa no fim do dia
- Encontrar comanda de um cliente específico

---

## ⚠️ Regras Importantes

### Sobre Comandas

| Situação | O que acontece |
|----------|----------------|
| Uma pessoa pode ter 2 comandas ativas? | ❌ Não. Apenas 1 comanda ativa por pessoa |
| Pode usar comanda fechada? | ❌ Não. Comanda fechada não aceita novos consumos |
| Pode reabrir comanda fechada? | ⚠️ Depende da configuração do sistema |
| Comanda cancelada some? | ❌ Não. Fica registrada como cancelada para histórico |

### Sobre Limites

| Situação | O que acontece |
|----------|----------------|
| Limite zero = sem fiado? | ✅ Sim. Cliente precisa pagar na hora |
| O que acontece se ultrapassar? | ⚠️ Sistema avisa, mas permite (se configurado) |
| Pode aumentar limite? | ✅ Sim, editando a pessoa |
| Limite é por comanda ou pessoa? | Por pessoa. Todas as comandas somam |

### Sobre Pagamentos

| Situação | O que acontece |
|----------|----------------|
| Pagar mais que o devido? | ✅ Aceita. Gera troco |
| Pagar várias vezes? | ✅ Sim. Pagamentos parciais são permitidos |
| Forma de pagamento obrigatória? | ✅ Sim. Sempre informe: dinheiro, PIX, cartão |
| Pode cancelar pagamento? | ⚠️ Depende da configuração |

---

## 💡 Dicas e Boas Práticas

### Para Atendentes

1. **Sempre confirme o nome do cliente**
   - "Comanda em nome de quem?"
   - Evita criar duplicados ("João" e "João Silva")

2. **Anote o ID da comanda**
   - Papelzinho na mesa: "Comanda #A7B3C9"
   - Facilita consultas rápidas

3. **Consulte o saldo antes de pedidos grandes**
   - Cliente com limite baixo → avise antes
   - Evita constrangimento na hora de pagar

4. **Use buscas simples para produtos**
   - "cerveja" ✓
   - "Cerveja Heineken garrafa 600ml" ✗ (pode não encontrar)

5. **Confirme pagamentos**
   - "Registrei seu pagamento de R$ 50 no PIX. Resta R$ 30."

### Para Gerentes

1. **Defina limites de crédito com cautela**
   - Clientes novos: comece com limite baixo
   - Clientes fiéis: pode aumentar gradualmente

2. **Feche comandas diariamente**
   - Comandas zeradas devem ser fechadas
   - Mantém o sistema organizado

3. **Monitore comandas ativas**
   - Use "Listar Comandas" no fim do expediente
   - Verifique se alguma ficou "esquecida"

4. **Treine a equipe**
   - Um erro comum: criar pessoa duplicada
   - Sempre buscar cliente existente primeiro

---

## ❓ FAQ - Perguntas Frequentes

**P: O cliente esqueceu o ID da comanda. Como acho?**
R: Use "Listar Comandas" e procure pelo nome do cliente. Ou crie uma nova (se não achar) - o sistema não deixa ter duas ativas.

**P: Posso trocar uma cerveja que o cliente pediu errado?**
R: Depende da versão do sistema. Na maioria dos casos, você cancela o item errado e adiciona o certo. Consulte o administrador.

**P: O cliente quer dividir a conta. Como fazer?**
R: Você pode:
1. Registrar pagamentos parciais (cada um paga sua parte)
2. Ou transferir itens para outra comanda (se disponível)

**P: E se o cliente não tiver limite e quiser fiar?**
R: O sistema avisa que ultrapassou o limite. A decisão de permitir ou não é do gerente/estabelecimento.

**P: Posso ver histórico de consumo do cliente?**
R: Sim, através da consulta de saldo e histórico da comanda. Comandas fechadas também ficam registradas.

**P: O sistema funciona offline?**
R: Não. Precisa de conexão com internet para acessar a API.

---

## 🆘 Problemas Comuns

### "Comanda não encontrada"
- Verifique se digitou o ID correto
- IDs têm letras e números (ex: "a1b2-c3d4-e5f6")
- A comanda pode ter sido fechada

### "Limite excedido"
- Cliente atingiu o limite de crédito
- Peça para fazer um pagamento parcial
- Ou fale com o gerente para aumentar o limite

### "Produto não encontrado"
- Use termos mais genéricos na busca
- Verifique se o produto está cadastrado
- Pode ser erro de digitação

### "Token expirado" (para técnicos)
- O token de acesso à API expira
- Renove fazendo login novamente
- Veja instruções no arquivo README-VPS

---

## 📞 Suporte

Em caso de dúvidas ou problemas:

1. Consulte este manual primeiro
2. Verifique os exemplos de cada feature
3. Pergunte ao seu supervisor/gerente
4. Para problemas técnicos, entre em contato com o administrador do sistema

---

## 📝 Glossário

| Termo | Significado |
|-------|-------------|
| **API** | Sistema que conecta o aplicativo ao banco de dados |
| **Comanda Ativa** | Comanda aberta, aceitando consumos |
| **Comanda Fechada** | Comanda paga e encerrada |
| **Consumo** | Qualquer item adicionado à comanda |
| **Fiado** | Comprar agora, pagar depois (com limite) |
| **Limite de Crédito** | Valor máximo que cliente pode dever |
| **Pagamento Parcial** | Pagar uma parte do total devido |
| **Saldo** | Quanto o cliente consumiu/está devendo |
| **Token** | Código de acesso ao sistema (para técnicos) |

---

## ✅ Checklist do Dia a Dia

### Abertura do Estabelecimento
- [ ] Verificar se sistema está online
- [ ] Conferir comandas do dia anterior (devem estar fechadas)

### Durante o Atendimento
- [ ] Criar pessoa para cliente novo
- [ ] Anotar ID da comanda
- [ ] Adicionar consumos na comanda correta
- [ ] Consultar saldo quando solicitado

### Fechamento
- [ ] Listar todas as comandas ativas
- [ ] Fechar comandas zeradas
- [ ] Verificar comandas pendentes
- [ ] Conferir pagamentos do dia

---

**Versão do Manual:** 1.0  
**Última atualização:** Março 2025  
**Sistema:** Baiten ANC

---

*Este manual foi criado para facilitar o uso do sistema. Em caso de dúvidas, consulte seu supervisor.*
