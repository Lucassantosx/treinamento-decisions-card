# Exercício 10: JOIN Complexo com Múltiplas Tabelas

## 📝 Pergunta

Crie um relatório completo de vendas mostrando: nome do cliente (`nm_cliente`), nome fantasia da rede (`nm_fantasia`), cidade da rede (`nm_cidade`), UF da rede (`cd_uf`), valor da venda (`vl_venda`), descrição da forma de pagamento (`ds_forma_pagamento`) e data da venda (`dt_venda`). 

Considere apenas vendas ativas dos últimos 6 meses a partir da maior data de venda existente na base. Ordene por valor decrescente.

## 🎯 Objetivo

Praticar:
- JOIN entre 4 tabelas (`t_venda`, `t_cliente`, `t_rede`, `t_forma_pagamento`)
- Filtros temporais baseados na maior data existente
- Consulta complexa com múltiplos relacionamentos
- Relatório gerencial completo

## 💡 Dicas

- Use `(SELECT MAX(dt_venda) FROM decisionscard.t_venda)` para a data máxima
- Subtraia 6 meses: `INTERVAL '6 months'`
- Conecte todas as tabelas pelos campos de relacionamento apropriados
- Qualifique todos os campos com alias das tabelas

---

## ✍️ Sua Resposta

```sql
select tc.nm_cliente, tr.nm_fantasia, tr.nm_cidade, tr.cd_uf, tv.vl_venda, tfp.ds_forma_pagamento, tv.dt_venda        
from decisionscard.t_venda tv 
join decisionscard.t_cliente tc  on tc.id_cliente = tv.id_cliente 
join decisionscard.t_rede tr on tr.id_rede = tv.id_rede 
join decisionscard.t_forma_pagamento tfp  on tfp.id_forma_pagamento = tv.id_forma_pagamento 
where tv.fl_status_venda = 'A' and tv.dt_venda >= (select max(dt_venda) - interval '6 months'
from decisionscard.t_venda)
order by tv.vl_venda desc;


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] JOINs corretos entre as 4 tabelas
- [ ] Filtra vendas dos últimos 6 meses
- [ ] Usa subconsulta para data máxima
- [ ] Campos de todas as tabelas
- [ ] Ordenação por valor decrescente

