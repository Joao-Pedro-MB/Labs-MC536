# Lab05 - Marcadores e Taxonomia em Cypher

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
~~~

# Aluno
* `218733`: `Joao Pedro de Moraes Bonucci`

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.

### Resolução
~~~cypher
MATCH(Marcador)-[:Pertence]->(Categoria{id: 'Serviços'})
RETURN Marcador,Categoria
~~~


## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

### Resolução
~~~cypher
MATCH(Marcador)
WHERE (Marcador)-[:Pertence]->()-[:Superior*1..]->({id: 'Serviços'}) OR (Marcador)-[:Pertence]->({id: 'Serviços'})
RETURN  DISTINCT Marcador
~~~

