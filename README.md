# Xbox Game Pass — Dashboard de Assinaturas

arquivo: `dashboard_vendas.xlsx` | período: jan–dez 2024 | 295 registros

---

## o que é isso

é um dashboard de vendas de assinaturas do Xbox Game Pass. tem os dados brutos, os cálculos e um painel visual com KPIs e gráficos. tudo automático — você muda os dados, o dashboard atualiza sozinho.

---

## números rápidos

| métrica | valor |
|---|---|
| receita total | R$ 7.633,00 |
| assinantes | 295 |
| renovação automática | 148 |
| receita EA Play | R$ 2.940,00 |
| receita Minecraft | R$ 3.880,00 |

---

## como o arquivo está organizado

são 4 abas:

- `A̳ssets` — paleta de cores e referência de funções
- `B̳ases` — os 295 registros brutos (é aqui que ficam os dados)
- `C̳álculos` — 4 perguntas de negócio respondidas com fórmulas
- `D̳ashboard` — o painel visual com KPIs, gráficos e tabela

---

## as colunas da base

| coluna | o que é |
|---|---|
| ID Assinante | id único de cada cliente |
| Nome | nome do assinante |
| Plano | Core, Standard ou Ultimate |
| Data Início | quando começou a assinatura |
| Renovação Auto | Yes ou No |
| Preço Assinatura | valor base do plano |
| Tipo Assinatura | Monthly, Annual ou Quarterly |
| EA Play Pass | tem o add-on? Yes ou No |
| Preço EA Play | quanto pagou pelo EA Play |
| Minecraft Pass | tem o add-on? Yes ou No |
| Preço Minecraft | quanto pagou pelo Minecraft |
| Valor Cupom | desconto aplicado |
| Valor Total | valor final da linha |

---

## o que os cálculos respondem

quatro perguntas de negócio, tudo usando `SUMIF` e `SUMIFS`:

1. qual o faturamento por tipo de assinatura (mensal, anual, trimestral)?
2. dentro do mensal, quanto veio de quem tem renovação automática e de quem não tem?
3. qual a receita do EA Play Season Pass separada por plano?
4. qual a receita do Minecraft Season Pass separada por plano?

> os dados que alimentam os gráficos do dashboard também ficam nessa aba, a partir da linha 42. foi feito assim pra não aparecer um monte de fórmula solta no dashboard.

---

## o dashboard

design escuro, fundo `#0A1628`. cada KPI tem uma cor diferente no topo do card pra facilitar a leitura. os gráficos ficam logo abaixo e a tabela de resumo por plano fica no final.

| cor | KPI |
|---|---|
| `#00D4FF` ciano | Receita Total |
| `#00E5A0` verde | Assinantes |
| `#B48EFF` roxo | Renovação Auto |
| `#FF6B8A` rosa | EA Play |
| `#FFC845` amarelo | Minecraft |

---

## fórmulas usadas

47 no total, zero erros.

| função | pra quê |
|---|---|
| `SUM` | soma geral da receita |
| `SUMIF` | receita por plano |
| `SUMIFS` | receita cruzando dois critérios |
| `SUMPRODUCT` | faturamento por mês (via texto da data) |
| `COUNTIF` | quantos têm renovação automática |
| `COUNTA` | total de linhas na base |
| `TEXT` | pega o mês abreviado da data pra agrupar |
| `IFERROR` | evita erro quando não tem dado |

---

## como atualizar

1. vai na aba `B̳ases` e coloca os novos dados a partir da linha 2
2. mantém as 13 colunas na mesma ordem
3. tudo no dashboard e em cálculos atualiza automaticamente
4. se passar de 296 linhas, atualiza o range dos `SUMPRODUCT` na aba `C̳álculos` (linhas 43–54) — troca `D$296` pelo novo limite

---

## resultados 2024

- plano mais rentável: **Ultimate** — R$ 5.388 (70,6% da receita total)
- tipo mais vendido: **Monthly** — R$ 3.571 (46,8%)
- melhor mês: **outubro** — R$ 832
- de março a novembro todos os meses ficaram acima de R$ 770
- renovação automática dividida quase no meio: 148 sim, 147 não

---

*dashboard_vendas_v2.xlsx · 2024*
