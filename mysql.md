# Comandos MySql

## Comandos de Database

| Comando | Descrição |
| ---|--- |
| CREATE DATABASE (nome) | Cria um banco de dados |
| DROP DATABASE (nome) | Apaga o banco de dados |
| USE (Nome DB) | muda pro banco em questão |

## Comandos de Tabela

| Comando | Descrição |
| ---|--- |
| CREATE TABLE (nome) | Cria uma tabela |
| DROP TABLE (nome) | Apaga uma tabela |

## Alterar Tabela

| Comando | Descrição |
| ---|--- |
| INSERT INTO (nomeTabela) (campos) VALUES (valores) | insere valores nos campos informados |
| UPDATE (nomeTabela) SET (campo) = (valor) WHERE (campo) = (valor) | altera a informação do campo |
| DELETE FROM (nomeTabela) WHERE (campo) = (valor) | apaga determinado campo da tabela |

| Comando | Descrição |
| ---|--- |
| ALTER TABLE (nomeTabela) ADD PRIMARY KEY (campo) | adiciona uma PK no campo informado |
| ALTER TABLE (nomeTabela) ADD COLUMN (nome tipo) | adiciona uma coluna |

## Comandos de Seleção

| Comando | Descrição |
| ---|--- |
| SELECT (campos) from (nomeTabela) | seleciona determinados campos da tabela |
| SELECT * from (nomeTabela) | seleciona todos os campos da tabela |

| Comando | Descrição |
| ---|--- |
| SELECT * from (nomeTabela) LIMIT (num) | limita a busca para os N primeiros|
| SELECT * from (nomeTabela) LIMIT (num, N próximos) | limita a busca dentro do intervalo|

| Comando | Descrição |
| ---|--- |
| SELECT * FROM (nomeTabela) WHERE (campo) = (value) | seleciona determinado campo |
| SELECT * FROM (nomeTabela) WHERE (campo) > (value) | seleciona intervalo |
| SELECT * FROM (nomeTabela) WHERE (campo) BETWEEN (value) AND (value) | seleciona intervalo |
| SELECT * FROM (nomeTabela) WHERE YEAR(DATA) = (value) | seleciona pelo ano da data |
| SELECT * from (nomeTabela) WHERE (cond1) AND (cond2) | filtro múltiplo |
| SELECT * from (nomeTabela) WHERE (cond1) OR (cond2) | filtro múltiplo |
| SELECT * from (nomeTabela) WHERE (campo) IN (valores) | o campo deve estar contido nos valores |
| SELECT * from (nomeTabela) WHERE (campo) LIKE (texto) | campo o deve ter o texto |

| Comando | Descrição |
| ---|--- |
| SELECT DISTINCT * FROM (nome Tabela) | Não vai retornar linhas iguais |
| SELECT * FROM (nomeTabela) ORDER BY campo (DESC) | Ordena a listagem com base no campo. DESC é opcional, o padrão é ASC |
| SELECT * FROM (nomeTabela) GROUP BY (campo) | agrupa os valores repetidos |
| SELECT SUM(campo) AS (alias) FROM (nomeTabela) | aplica alguma função no campo | 

| Comando | Descrição |
| ---|--- |
| HAVING | Filtro aplicado sobre o resultado de um GROUP BY |
| SELECT * FROM (nomeTabela) GROUP BY (campo) HAVING (cond)| agrupa os valores repetidos |

| Comando | Descrição |
| ---|--- |
| SELECT CASE WHEN (cond1) THEN (valor1) ELSE (valorElse) END AS (alias) | é um if |

## Comandos de Junção

| Comando | Descrição |
| ---|--- |
| INNER JOIN | É como se fosse a interseção |
| LEFT JOIN | Todos da esquerda |
| RIGHT JOIN | Todos da direita |
| FULL JOIN | Todos de todos |
| CROSS JOIN | Produto cartesiano |
| SELECT * FROM (nomeTabela) A INNER JOIN (nomeTabela) B ON A.(campoComum) = B.(campoComum) | Exemplo |
| SELECT * FROM (nomeTabela) A LEFT JOIN (nomeTabela) B ON A.(campoComum) = B.(campoComum) | Exemplo |
 
 | Comando | Descrição |
| ---|--- |
| UNION | Junta duas tabelas 'iguais' e aplica um distinc |
| UNION ALL | Junta sem aplicar o distinc |

## Funções

| Funções | Descrição |
| ---|--- |
| SUM | Soma |
| MAX | Maximo |
| MIN | Minimo |
| AVG | Media |
| COUNT | Conta ocorrências |

| String Functions | Descrição |
| --- | --- |
| LTRIM | Remove os espaços da esquerda |
| CONCAT | Concatena |
| UPPER | Coloca em uppercase |
| SUBSTRING('texto', index)| é um slice |

| Date Functions | Descrição |
| --- | --- |
| CURDATE() | Trás a data atual |
| CURRENT_TIME() | Trás a hora atual |
| CURRENT_TIMESTAMP() | Data e hora atual |
| YEAR | extrai o ano |
| DAY | extrai o dia |
| MONTHNAME | trás o nome do mês |
| MONTH | extrai o mês |
| DATEDIFF(date1, date2) | diferença entre as datas |
| DATA_SUB(data, INTERVAL (n) DAY) | diminui um intervalo de N dias |

| Math Functions | Descrição |
| --- | --- |
| CEILING | arredonda pra cima |
| FLOOR | arredonda pra baixo |
| ROUND(param, casas decimais) | arredonda certinho |
| RAND | número aleatório de 0 a 0.99 |

## Comandos de Conversão

| Conversão| Descrição |
| ---|--- |
| DATE_FORMAT(data, 'formato de saida') | transforma a data |
| CONVERT(num, char) | converte numero em string |

## Símbolos

| Simbolos | Descrição |
| ---|--- |
| > | Maior |
| < | Menor |
| >= | Maior igual |
| <= | Menor igual |
| <> | Diferente |
