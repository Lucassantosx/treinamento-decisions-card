# Exercício 6: JOIN Simples - Clientes e Cartões

## 📝 Pergunta

Liste todos os clientes que possuem cartão ativo, mostrando o nome do cliente (`nm_cliente`), o número do cartão (`nu_cartao`) e a data de emissão do cartão (`dt_emissao`). Ordene pelo nome do cliente.

## 🎯 Objetivo

Praticar:
- JOIN entre duas tabelas (INNER JOIN)
- Relacionamento entre `t_cliente` e `t_cartao`
- Filtros em tabelas relacionadas
- Seleção de campos de múltiplas tabelas

## 💡 Dicas

- Use INNER JOIN para conectar `t_cliente` e `t_cartao` através do `id_cliente`
- Filtre cartões com `fl_status_cartao = 'A'`
- Qualifique os campos com o nome da tabela (ex: `c.nm_cliente`)

---

## ✍️ Sua Resposta

```sql
select tc.nm_cliente, tca.nu_cartao, tca.dt_emissao 
from decisionscard.t_cliente tc 
join decisionscard.t_cartao tca on tc.id_cliente = tca.id_cliente 
where tca.fl_status_cartao = 'A'
order by tc.nm_cliente; 

```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] Usa INNER JOIN corretamente
- [ ] Filtra apenas cartões ativos
- [ ] Campos corretos de ambas as tabelas
- [ ] Ordenação por nome do cliente

