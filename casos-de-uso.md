# Casos de Uso do ERP - Centro Educacional CSI

Explicação das principais funcionalidades do sistema.

[Voltar para o inicio](README.md)

## Definições

### Cadastro Simples

Cadastro simples de um registro com preenchimento de campos que permitirá ao usuário incluir, visualizar, atualizar e/ou remover o registro. A remoção não excluirá os dados do sistema, apenas ocultará. Os dados poderão ainda ser lidos pelos programadores.

### Status

Campo de controle que representa o estado do registro.

## Casos de Uso

### Pessoa Física, Pessoa Jurídica

É um [cadastro simples](#cadastro-simples).

### Doador

É um [cadastro simples](#cadastro-simples).
Será obrigatório vincular o doador a uma pessoa física ou jurídica (apenas um dos dois).

### ONG

É um [cadastro simples](#cadastro-simples).
Será obrigatório vincular a ONG a uma pessoa jurídica.

### Instituição Bancária

É um [cadastro simples](#cadastro-simples).

### Conta Bancária

É um [cadastro simples](#cadastro-simples).
Será obrigatório vincular a conta bancária a uma instituição bancária.

### Doação Financeira

Contém [status](#status).

#### Status "rascunho"

A inclusão de uma doação financeira terá o status "rascunho" por padrão. Neste status, a doação financeira será um [cadastro simples](#cadastro-simples). Porém, a remoção excluirá os dados por completo do sistema.

Será possível mudar o status para "inclusão solicitada" a fim de gerar a receita referente a doação financeira. Para isso, será obrigatório vincular a doação financeira a um doador.

#### Status "inclusão solicitada"

Quando uma doação financeira tem seu status atualizado para "inclusão solicitada" será criada uma receita com status "inclusão solicitada" e não será mais possível remover a doação financeira.

### Receita

Contém [status](#status).

#### Status "rascunho"

A inclusão de uma receita terá o status "rascunho" por padrão. Neste status, a receita será um [cadastro simples](#cadastro-simples). Porém, a remoção excluirá os dados por completo do sistema.

Será possível mudar o status para "inclusão solicitada" a fim de pedir ao responsável do setor financeiro para gerar a transação financeira referente a receita. Para isso, será obrigatório vincular a receita a uma conta bancária e a uma origem (ex: doação financeira, serviço prestado).

#### Status "inclusão solicitada"

Quando uma receita tem seu status atualizado para "inclusão solicitada" não será mais possível removê-la e ela ficará esperando análise do responsável do setor financeiro. O responsável do setor financeiro poderá rejeitar ou aprovar a receita.

#### Status "inclusão rejeitada"

Quando uma receita tem seu status atualizado para "inclusão rejeitada" ela não terá mais efeitos no sistema e ficará bloqueada.

#### Status "inclusão aprovada"

Quando uma receita tem seu status atualizado para "inclusão aprovada" ela irá gerar uma transação financeira no extrato vinculada a conta bancária da receita.

Será possível mudar o status para "estornada" a fim de realizar o estorno da operação.

#### Status "estornada"

Quando uma receita tem seu status atualizado para "estornada" ela irá gerar uma transação financeira no extrato que anula o efeito da transação original. Essa transação financeira de estorno será vinculada a conta bancária da receita e a transação original. Além disso, a receita ficará bloqueada.

---

### Despesa

Contém [status](#status).

#### Status "rascunho"

A inclusão de uma despesa terá o status "rascunho" por padrão. Neste status, a despesa será um [cadastro simples](#cadastro-simples). Porém, a remoção excluirá os dados por completo do sistema.

Será possível mudar o status para "inclusão solicitada" a fim de pedir ao responsável do setor financeiro para gerar a transação financeira referente a despesa. Para isso, será obrigatório vincular a despesa a uma conta bancária e a uma origem (ex: serviço contratado, ordem de compra), além de incluir as parcelas da despesa.

#### Status "inclusão solicitada"

Quando uma despesa tem seu status atualizado para "inclusão solicitada" não será mais possível removê-la e ela ficará esperando análise do responsável do setor financeiro. O responsável do setor financeiro poderá rejeitar ou aprovar a despesa.

#### Status "inclusão rejeitada"

Quando uma despesa tem seu status atualizado para "inclusão rejeitada" ela não terá mais efeitos no sistema e ficará bloqueada.

#### Status "inclusão aprovada"

Quando uma despesa tem seu status atualizado para "inclusão aprovada" ela irá gerar uma transação financeira no extrato vinculada a conta bancária da despesa.

Será possível mudar o status para "estorno solicitado" a fim de pedir ao responsável do setor financeiro para gerar o estorno da operação.

#### Status "estorno solicitado"

Quando uma despesa tem seu status atualizado para "estorno solicitado" ela ficará esperando análise do responsável do setor financeiro. O responsável do setor financeiro poderá rejeitar ou aprovar o estorno.

#### Status "estorno rejeitado"

Quando uma despesa tem seu status atualizado para "estorno rejeitado" ela não terá mais efeitos no sistema e ficará bloqueada.

#### Status "estorno aprovado"

Quando uma despesa tem seu status atualizado para "estorno aprovado" ela irá gerar uma transação financeira no extrato que anula o efeito da transação original. Essa transação financeira de estorno será vinculada a conta bancária da despesa e a transação original. Além disso, a despesa ficará bloqueada.