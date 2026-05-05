# Exercício 9: Relacionamento com Tabelas de Domínio

## 📝 Pergunta

Liste os clientes mostrando `nm_cliente`, a descrição da escolaridade (`ds_escolaridade` da tabela `t_escolaridade`) e a descrição do estado civil (`ds_estado_civil` da tabela `t_estado_civil`). Considere apenas clientes cadastrados nos últimos 2 anos a partir da maior data de cadastro existente na base. Ordene por data de cadastro decrescente.

## 🎯 Objetivo

Praticar:
- JOIN com tabelas de domínio/lookup
- Substituição de códigos por descrições
- Filtros baseados em datas relativas
- Uso de subconsulta para encontrar data máxima

## 💡 Dicas

- Use `(SELECT MAX(dt_cadastro) FROM decisionscard.t_cliente)` para encontrar a maior data
- Subtraia 2 anos: `INTERVAL '2 years'`
- Faça JOIN com `t_escolaridade` e `t_estado_civil` usando os IDs correspondentes

---

## ✍️ Sua Resposta

```sql
select tc.nm_cliente, te.ds_escolaridade, tec.ds_estado_civil 
from decisionscard.t_cliente tc
join decisionscard.t_escolaridade te on tc.id_escolaridade = te.id_escolaridade 
join decisionscard.t_estado_civil tec on tc.id_estado_civil = tec.id_estado_civil 
where tc.dt_cadastro >= (select max(dt_cadastro) - interval '2 years'
from decisionscard.t_cliente)
order by tc.dt_cadastro desc;


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] JOINs corretos com tabelas de domínio
- [ ] Filtra clientes dos últimos 2 anos
- [ ] Usa subconsulta para data máxima
- [ ] Mostra descrições ao invés de códigos

