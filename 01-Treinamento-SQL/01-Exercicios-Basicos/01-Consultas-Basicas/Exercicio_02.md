# Exercício 2: Filtros Simples em Redes Parceiras

## 📝 Pergunta

Liste todas as redes parceiras (`t_rede`) que estão localizadas no estado de 'SP' (São Paulo). Mostre os campos `id_rede`, `nm_fantasia`, `nm_cidade` e `cd_uf`. Ordene alfabeticamente pelo nome fantasia.

## 🎯 Objetivo

Praticar:
- Cláusula WHERE para filtros
- Ordenação alfabética
- Trabalho com campos de texto

## 💡 Dica

O campo `cd_uf` contém a sigla do estado (ex: 'SP', 'RJ', 'MG').

---

## ✍️ Sua Resposta

```sql
select tr.id_rede, tr.nm_fantasia, tr.nm_cidade, tr.cd_uf 
from decisionscard.t_rede tr 
where tr.cd_uf like 'SP' 
order by tr.nm_fantasia;


```

---

## 📋 Critérios de Avaliação

- [ ] Query executa sem erros
- [ ] Filtra apenas redes do estado 'SP'
- [ ] Campos corretos são exibidos
- [ ] Ordenação alfabética por nome fantasia
- [ ] Usa WHERE corretamente

