# Regras de negócio e fluxos

## 1. Objetivo

O Hostask centraliza a gestão de imóveis de aluguel de temporada, reunindo reservas, limpezas, manutenção, estoque, inventário e financeiro.

Também permite organizar a prestação de contas mensal ao proprietário de cada imóvel.

## 2. Perfis de acesso

| Perfil | Acesso |
| --- | --- |
| Administrador | Todos os módulos. |
| Limpeza | Limpezas, Manutenção e Estoque. |

Na implementação descrita, o perfil é escolhido na entrada e mantido na sessão.

## 3. Reservas

Cada reserva pertence a um imóvel e contém:

- Hóspede.
- Check-in e check-out.
- Valor bruto da estadia.
- Taxa Airbnb.
- Taxa de limpeza.
- Caução.
- Status.

### Status

- Confirmada.
- Em andamento.
- Concluída.
- Cancelada.

Reservas confirmadas, em andamento e concluídas são consideradas no financeiro. Reservas canceladas são desconsideradas.

### Período e receita proporcional

Uma reserva participa do mês analisado quando seu período se sobrepõe a ele: o check-in ocorre antes do fim do mês e o check-out ocorre depois do início.

Quando a estadia atravessa meses, o valor bruto é dividido proporcionalmente pelas diárias de cada mês.

**Exemplo:** uma reserva de 10 diárias, com valor bruto total de R$ 1.000, tem 4 diárias no primeiro mês e 6 no segundo. A receita bruta será de R$ 400 no primeiro e R$ 600 no segundo.

### Ocupação

A ocupação corresponde aos dias ocupados no mês divididos pela quantidade de dias daquele mês.

Reservas canceladas não entram no cálculo.

### Acompanhamento operacional

A reserva inclui acompanhamento de check-in, check-out, caução retida, multa e avaliação do hóspede.

## 4. Financeiro

Receitas e despesas são registradas como lançamentos, com categoria, valor e data.

A data do lançamento determina o mês em que ele aparece.

A receita de estadias apresentada por reserva segue a divisão proporcional descrita na seção de reservas.

### Resultado ao proprietário

    Receita bruta de estadias
    − Comissão do administrador
    − Despesas operacionais
    + Reembolso por danos
    = Receita líquida ao proprietário

### Comissão

A comissão do administrador é de 20% sobre a receita bruta de estadias.

Reembolsos por danos não entram na base de cálculo da comissão.

### Reembolso por danos

É registrado em uma tela própria, com categoria específica.

Seu valor é somado ao resultado do proprietário, sem desconto de comissão.

### Despesas

São cadastradas no módulo Financeiro com a data escolhida pelo usuário.

As categorias incluem limpeza, manutenção, energia, água, internet, lixo, condomínio, IPTU, materiais, comissão e outras.

### Margem

A margem é calculada dividindo a receita líquida pela soma da receita bruta de estadias com os reembolsos.

### Períodos do dashboard

- Mês atual.
- Mês anterior.
- Últimos 12 meses.

## 5. Manutenção

Ao salvar uma manutenção com custo maior que zero, o sistema cria uma despesa na categoria Manutenção, vinculada ao chamado.

A data do lançamento é a data da manutenção informada no cadastro. Isso permite registrar uma manutenção retroativa no mês correspondente.

Quando o custo é editado, o lançamento existente é atualizado, sem duplicação.

Se o custo passar a zero, a despesa vinculada é removida.

## 6. Despesas fixas recorrentes

São cadastradas por imóvel, com valor estimado e dia de vencimento.

Exemplos: energia, água, internet, condomínio e IPTU.

O cadastro não gera lançamentos automaticamente. O usuário utiliza a opção de lançar uma despesa individual ou lançar as despesas do mês atual.

Cada despesa é identificada como Lançada ou Pendente no mês.

## 7. Limpezas

Cada limpeza pode conter responsável, checklist, custo e fotos.

As limpezas aparecem no relatório do proprietário.

O custo da limpeza só participa do total de despesas quando também existe um lançamento correspondente no Financeiro.

## 8. Estoque e inventário

O estoque registra a quantidade atual e a quantidade mínima dos itens.

O sistema apresenta alertas de estoque baixo e utiliza essas informações no controle de inventário.

## 9. Relatórios

O relatório do proprietário é gerado por imóvel e por mês, com seleção dos últimos 24 meses.

Apresenta:

- Demonstrativo de resultado.
- Reservas com valores proporcionais.
- Despesas detalhadas.
- Limpezas.
- Gráficos.
- Área para assinatura.

Pode ser impresso ou salvo em PDF.

O sistema também disponibiliza informe de rendimentos e exportações em CSV e PDF.

## 10. Principais fluxos

### Cadastro e acompanhamento de reserva

1. O administrador seleciona o imóvel.
2. Informa hóspede, datas e valores.
3. Define o status e salva.
4. Acompanha check-in e check-out.
5. Atualiza o status conforme o andamento.
6. As reservas válidas entram nos cálculos do período correspondente.

### Registro de manutenção

1. O usuário cadastra o chamado.
2. Informa a data e o custo.
3. Salva o registro.
4. Se o custo for maior que zero, o sistema cria a despesa vinculada.
5. Alterações no custo atualizam o lançamento.
6. Se o custo passar a zero, o lançamento é removido.

### Lançamento de despesa recorrente

1. O administrador cadastra a despesa fixa do imóvel.
2. Consulta as despesas pendentes do mês.
3. Seleciona o lançamento individual ou do mês atual.
4. O sistema cria os lançamentos e atualiza a indicação de lançamento.

### Prestação de contas

1. O administrador seleciona o imóvel e o mês.
2. Confere as reservas e suas receitas proporcionais.
3. Confere despesas e reembolsos.
4. Verifica a comissão e o resultado líquido.
5. Gera o relatório para impressão ou PDF.