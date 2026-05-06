# Exercício 12: GROUP BY com Múltiplas Colunas

## 📝 Pergunta

Analise as vendas por estado (UF) e rede parceira, mostrando: UF da rede (`cd_uf`), nome fantasia da rede (`nm_fantasia`), quantidade de vendas (`qtd_vendas`), valor total (`total_vendas`) e ticket médio (`ticket_medio`). 

Considere apenas vendas ativas e mostre apenas combinações com mais de 5 vendas. Ordene por UF e depois por valor total decrescente.

## 🎯 Objetivo

Praticar:
- GROUP BY com múltiplas colunas
- Cláusula HAVING para filtrar grupos
- Cálculos agregados por múltiplas dimensões
- Análise geográfica e por parceiro

## 💡 Dicas

- GROUP BY deve incluir `cd_uf` e `nm_fantasia`
- Use HAVING para filtrar grupos com COUNT(*) > 5
- Ticket médio = SUM(vl_venda) / COUNT(*)
- ORDER BY pode ter múltiplas colunas

---

## ✍️ Sua Resposta

```sql
select tr.cd_uf, 
tr.nm_fantasia,
sum(tv.vl_venda ) as Total_Vendas,
count(*) as Qtd_Vendas,
avg(tv.vl_venda) as Ticket_Medio
from decisionscard.t_venda tv
join decisionscard.t_rede tr on tr.id_rede = tv.id_rede
where tv.fl_status_venda = 'A'
group by tr.cd_uf, tr.nm_fantasia 
having count(*) > 5
order by tr.cd_uf, total_vendas desc


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] GROUP BY com múltiplas colunas
- [ ] HAVING filtra grupos corretamente
- [ ] Cálculos agregados corretos
- [ ] JOIN entre vendas e redes
- [ ] Ordenação múltipla (UF, valor)

