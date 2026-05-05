# Exercício 4: Top 5 Vendas por Valor

## 📝 Pergunta

Encontre as 5 vendas (`t_venda`) de maior valor da base de dados. Mostre os campos `id_venda`, `id_cliente`, `vl_venda` e `dt_venda`. Ordene do maior valor para o menor.

## 🎯 Objetivo

Praticar:
- Ordenação decrescente (DESC)
- Limitação de resultados com LIMIT
- Trabalho com campos numéricos e de data
- Identificação de registros extremos (top N)

## 💡 Dica

Para ordenar do maior para o menor, use ORDER BY campo DESC.

---

## ✍️ Sua Resposta

```sql
select tv.id_venda, tv.id_cliente, tv.vl_venda, tv.dt_venda 
from decisionscard.t_venda tv
order by tv.vl_venda desc limit 5;


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] Retorna exatamente 5 registros
- [ ] Ordenação decrescente por valor
- [ ] Campos corretos são exibidos
- [ ] Mostra as vendas de maior valor

