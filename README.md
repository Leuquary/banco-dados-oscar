# Atividade para trabalhar com o Oscar
1. Quantas vezes Natalie Portman foi indicada ao Oscar?
```sql
select count(*) from oscar_database.indicados_ao_oscar where nome_do_indicado = "Natalie Portman";
```

2. Quantos Oscars Natalie Portman ganhou?
```sql
select count(*) from oscar_database.indicados_ao_oscar where nome_do_indicado = "Natalie Portman" and vencedor = 'true';
```

3. Amy Adams já ganhou algum Oscar?
```sql
select count(*) from oscar_database.indicados_ao_oscar where nome_do_indicado = "Amy Adams" and vencedor = 'true';
```

4. A série de filmes Toy Story ganhou um Oscar em quais anos?
```sql
select * from oscar_database.indicados_ao_oscar WHERE nome_do_filme like '%Toy Story%';
```

5. A partir de que ano que a categoria "Actress" deixa de existir?
```sql
select max(ano_cerimonia) as ultimo_ano FROM indicados_ao_oscar where categoria = 'Actress';
```
