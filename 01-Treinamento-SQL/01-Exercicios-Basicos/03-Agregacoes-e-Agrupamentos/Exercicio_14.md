# Exercício 14: Funções de Data e Agrupamento Temporal

## 📝 Pergunta

Analise a evolução mensal das vendas nos últimos 12 meses a partir da maior data de venda existente na base. Mostre: ano (`ano`), mês (`mes`), nome do mês (`nome_mes`), quantidade de vendas (`qtd_vendas`), valor total (`total_vendas`) e crescimento percentual em relação ao mês anterior (`crescimento_pct`).

Ordene por ano e mês.

## 🎯 Objetivo

Praticar:
- Funções de data (EXTRACT, TO_CHAR)
- Agrupamento temporal
- Window functions para cálculo de crescimento
- Análise de tendências temporais

## 💡 Dicas

- Use EXTRACT(YEAR FROM dt_venda) e EXTRACT(MONTH FROM dt_venda)
- TO_CHAR(dt_venda, 'Month') para nome do mês
- LAG() para valor do mês anterior
- Fórmula: ((valor_atual - valor_anterior) / valor_anterior) * 100

---

## ✍️ Sua Resposta

```sql
select extract (year from tv.dt_venda) as Ano,
extract (month from tv.dt_venda) as Mes,
to_char(dt_venda, 'TMMonth') as nome_mes,
count(*) as Qtd_Vendas,
sum(tv.vl_venda) as Total_Vendas,
lag(sum(tv.vl_venda)) over(order by extract(year from tv.dt_venda), extract(month from tv.dt_venda)) as valor_anterior,
round( 
((sum(tv.vl_venda) - lag(sum(tv.vl_venda)) over(order by extract(year from tv.dt_venda), extract(month from tv.dt_venda))) /
lag(sum(tv.vl_venda)) over(order by extract(year from tv.dt_venda), extract(month from tv.dt_venda))) * 100, 2) as crescimento_pt
from decisionscard.t_venda tv
group by 
extract (year from tv.dt_venda),
extract (month from tv.dt_venda),
to_char(tv.dt_venda, 'TMMonth')
order by Ano, Mes;


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] Funções de data corretas
- [ ] Filtro dos últimos 12 meses
- [ ] GROUP BY por ano e mês
- [ ] Window function para crescimento
- [ ] Ordenação temporal

