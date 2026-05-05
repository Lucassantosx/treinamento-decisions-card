# Exercício 11: Análise de Vendas por Rede Parceira

## 📝 Pergunta

Calcule o valor total de vendas e a quantidade de transações para cada rede parceira. Mostre o nome fantasia da rede (`nm_fantasia`), o valor total (`total_vendas`), a quantidade de vendas (`qtd_vendas`) e o ticket médio (`ticket_medio`). 

Ordene pelo valor total de vendas em ordem decrescente e considere apenas vendas com status ativo (`fl_status_venda = 'A'`).

## 🎯 Objetivo

Praticar:
- GROUP BY para agrupamento
- Funções de agregação (SUM, COUNT, AVG)
- JOIN entre múltiplas tabelas
- Cálculos derivados (ticket médio)
- Filtros em consultas agrupadas

## 💡 Dicas

- Ticket médio = Valor total / Quantidade de vendas
- Use aliases para nomear as colunas calculadas
- JOIN entre `t_venda` e `t_rede` através do `id_rede`
- GROUP BY deve incluir `nm_fantasia`

---

## ✍️ Sua Resposta

```sql
select tr.nm_fantasia,
sum(tv.vl_venda ) as Total_Vendas,
count(*) as Qtd_Vendas,
AVG(tv.vl_venda) as Ticket_Medio
from decisionscard.t_venda tv
join decisionscard.t_rede tr on tr.id_rede = tv.id_rede
where tv.fl_status_venda = 'A'
group by tr.nm_fantasia, tr.id_rede
order by total_vendas desc;


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] Usa GROUP BY corretamente
- [ ] Calcula valor total, quantidade e ticket médio
- [ ] JOIN correto entre vendas e redes
- [ ] Filtra apenas vendas ativas
- [ ] Ordenação por valor total decrescente

