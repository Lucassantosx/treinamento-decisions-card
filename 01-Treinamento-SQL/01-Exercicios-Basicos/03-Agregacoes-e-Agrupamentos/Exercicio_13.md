# Exercício 13: HAVING para Filtrar Grupos

## 📝 Pergunta

Identifique clientes com alto volume de compras. Mostre `id_cliente`, `nm_cliente`, quantidade de vendas (`qtd_vendas`) e valor total gasto (`total_gasto`). 

Considere apenas clientes que fizeram mais de 10 compras ativas E gastaram mais de R$ 5.000,00 no total. Ordene por valor total gasto decrescente.

## 🎯 Objetivo

Praticar:
- Cláusula HAVING com múltiplas condições
- Identificação de clientes VIP
- Filtros em dados agregados
- Análise de comportamento de compra

## 💡 Dicas

- Use HAVING com AND para múltiplas condições
- COUNT(*) para quantidade de vendas
- SUM(vl_venda) para valor total
- HAVING vem após GROUP BY

---

## ✍️ Sua Resposta

```sql
select tc.id_cliente, 
tc.nm_cliente,
count(*) as Qtd_Vendas,
sum(tv.vl_venda ) as Total_Gasto
from decisionscard.t_cliente tc 
join decisionscard.t_venda tv on tc.id_cliente = tv.id_cliente
where tv.fl_status_venda = 'A'
group by tc.id_cliente, tc.nm_cliente 
having count (*) > 10 
and sum(tv.vl_venda) > 5000; 


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] GROUP BY por cliente
- [ ] HAVING com múltiplas condições (qtd > 10 E valor > 5000)
- [ ] Cálculos agregados corretos
- [ ] JOIN entre vendas e clientes
- [ ] Ordenação por valor decrescente

