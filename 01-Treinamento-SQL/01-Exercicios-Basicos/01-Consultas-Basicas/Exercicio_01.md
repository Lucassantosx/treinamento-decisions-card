# Exercício 1: Listagem Básica de Clientes

## 📝 Pergunta

Escreva uma query para selecionar os primeiros 10 clientes cadastrados na base, mostrando apenas os campos `id_cliente`, `nm_cliente`, `dt_nascimento` e `dt_cadastro`. Ordene do cliente mais antigo (primeiro cadastrado) para o mais recente.

## 🎯 Objetivo

Praticar consultas básicas com:
- SELECT de campos específicos
- ORDER BY para ordenação
- LIMIT para limitação de resultados

## 💡 Dica

Lembre-se de usar o schema `decisionscard` antes do nome da tabela.

---

## ✍️ Sua Resposta

```sql

select tc.id_cliente,tc.nm_cliente, tc.dt_nascimento, tc.dt_cadastro
from decisionscard.t_cliente tc
order by tc.dt_cadastro limit 10;


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] Retorna exatamente 10 registros
- [ ] Campos corretos são exibidos
- [ ] Ordenação está correta (mais antigo primeiro)
- [ ] Usa o schema `decisionscard` corretamente

