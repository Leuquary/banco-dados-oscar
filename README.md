# E o Oscar vai para... ?

Hoje vamos trabalhar com o Oscar.
A ideia de premiar ou ser premiado é para reconhecer:
- Reconhecer uma qualidade
- Reconhecer um atributo
- Reconhecer o esforço... 

Alguns diriam que prêmios são apenas um reconhecimento superficial do nosso trabalho, uma forma de massagear o ego e nos deixar com a sensação de que estamos fazendo algo certo. Outros, no entanto, defendem que os prêmios são uma forma de validação do nosso trabalho, uma prova de que estamos no caminho certo e de que estamos fazendo a diferença.

Prêmios têm sim o seu valor, mas que eles não são o único indicador de sucesso. É claro que é sempre bom ser reconhecido pelo nosso trabalho e ter um troféu ou uma placa para pendurar na parede, mas o mais importante mesmo é a satisfação pessoal que sentimos quando fazemos algo que amamos e que acreditamos ser importante. Então, sim, prêmios importam, mas não devemos deixá-los ser o único fator que determina o nosso sucesso e a nossa felicidade.

Nem todos os prêmios são merecidos e nem todos que merecem ganham prêmios. 
Então vale mesmo a pena, premiar? 

1. Quantas vezes Natalie Portman foi indicada ao Oscar?
```sql
select count(*) from indicados_ao_oscar where nome_do_indicado = "Natalie Portman";
```

2. Quantos Oscars Natalie Portman ganhou?
```sql
select count(*) from indicados_ao_oscar where nome_do_indicado = "Natalie Portman" and vencedor = "true";
```

3. Amy Adams já ganhou algum Oscar?
```sql
select count(*) from indicados_ao_oscar where nome_do_indicado = "Amy Adams" and vencedor = "true";
```

4. A série de filmes Toy Story ganhou um Oscar em quais anos?
```sql
select nome_do_filme, ano_cerimonia from indicados_ao_oscar where nome_do_filme like "%Toy Story%";
```

5. A partir de que ano que a categoria "Actress" deixa de existir?
```sql
select categoria, max(ano_cerimonia) as ultimo_ano from indicados_ao_oscar where categoria = "Actress";
```

6. O primeiro Oscar para melhor Atriz foi para quem? Em que ano?
```sql
select nome_do_indicado, min(ano_cerimonia) as primeiro_ano, categoria from indicados_ao_oscar where categoria = "Actress" group by nome_do_indicado limit 1;
```

7. Na coluna/campo "Vencedor", altere todos os valores com "Sim" para 1 e todos os valores "Não" para 0.
```sql
update filmes
set vencedor = 1
where vencedor = "Sim";

update filmes
set vencedor = 0
where vencedor = "Não";
```
8. Em qual edição do Oscar "Crash" concorreu ao Oscar?
```sql
select nome_filme, edicao_cerimonia from filmes where nome_filme = "Crash" limit 1;
```

9. Bom... dê um Oscar para um filme que merece muito, mas não ganhou.
```sql
insert into filmes (id_registro, ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor)
values (default, "1941", "1942", "14", "ACTOR", "Orson Welles", "Cidadão Kane", 1);
```

10. O filme Central do Brasil aparece no Oscar?
```sql
select * from indicados_ao_oscar where nome_do_filme = "Central do Brasil";
```

11. Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser.
```sql
insert into indicados_ao_oscar(ano_filmagem, ano_cerimonia, cerimonia, categoria, nome_do_indicado, nome_do_filme, vencedor) values
(2000, 2001, 73, "Melhor Filme", null, "Memento", "false"),
(2014, 2015, 87, "Melhor Filme", null, "Nightcrawler", "false"),
(2018, 2019, 91, "Melhor Filme", null, "First Reformed", "false");
```

13. Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor?
```sql
insert into filmes (id_registro, ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor)
values (default, "2004", "2005", "77", "ACTRESS", "Hilary Swank", "Menina de Ouro", 1);
```
