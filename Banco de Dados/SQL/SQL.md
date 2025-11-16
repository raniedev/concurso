# Structured Query Language

SQL é uma linguagem de consulta estruturada, utilizada em banco de dados relacionais sob a forma de comandos. Apesar de ter consulta no nome, ela é utilizada para realizar outras operações que envolvam dados, tais como inserções, remoções etc.
## Classificação dos comandos em SQL

- **Data Manipulation Language (DML):** Comandos em SQL de manipulação dos dados nas tabelas. Em outras palavras, não alteram as tabelas, mas podem impactar os dados armazenados nelas.
- **Data Query Language (DQL):** Comandos em SQL de consulta aos dados nas tabelas.
>**ATENÇÃO:** A adoção do DQL para os comandos de consulta não é unânime. Alguns autores consideram esses comandos como DML, enquanto outros os consideram como DQL. Normalmente, a questão trará apenas um dos dois no gabarito. Contudo, se os dois estiverem entre as alternativas possíveis, recomendamos que marque o DQL, por ser mais específico.

- **Data Definition Language (DDL):** Comandos em SQL que atuam diretamente nas estruturas dos objetos de bancos. Só para exemplificar, os objetos podem ser tabelas, índices, sequências etc.
- **Data Control Language (DCL):** Comandos em SQL envolvendo permissões de acesso ao banco. Nesse sentido, estão atrelados diretamente com a segurança da informação.
- **Data Transaction Language (DTL):** Comandos em SQL relacionados com as transações no banco. São eles que confirmam ou desfazem as operações realizadas, em caso de sucesso ou erro.

### DDL

**Comando DDL:** Criação de uma tela no banco, em sua versão padrão.

Sintaxe:
~~~SQL
CREATE TABLE Tabela
(coluna1 tipo1, coluna2 tipo2, ...)
~~~

SQL:
~~~SQL
CREATE TABLE Cliente(
	id INT PRIMARY KEY,
	nome VARCHAR(255),
	cidade VARCHAR(255),
	salario FLOAT
)
~~~

Criação de uma nova tabela no banco, a partir de uma consulta a uma tabela já existente.

~~~SQL
CREATE TABLE NovaTabela
AS SELECT coluna1, coluna2...
FROM Tabela
[WHERE condição]
~~~

>Condição pode ser diversos operadores de comparação, como: maior que, maior ou igual à, menor que, menor ou igual à, diferente, igual.
> Além de combinações com operadores lógicos AND, OR, NOT
> **Note que:**  Quando tiver colchetes na Sintaxe significa um comando opcional

SQL:
~~~SQL
CREATE TABLE Colaborador
AS SELECT *
FROM Clientes
WHERE id <= 5
~~~

**Comando ALTER:** Alteração de uma tabela para adição, exclusão ou alteração de campos.

Sintaxe:
~~~SQL
ALTER TABLE Tabela
[ADD coluna tipo] | [DROP COLUMN coluna tipo] | [RENAME COLUMN coluna TO novacoluna]
~~~
> A barra | para a Sintaxe indica um operador lógico OR

### DML

**Comando INSERT:** Inserção dos dados na tabela (padrão). 

Sintaxe:
~~~SQL
INSERT INTO Tabela
(coluna1, coluna2, coluna3, ...)
VALUES
(valor1, valor2, valor3, ...);
~~~

Inserção de dados:
~~~SQL
INSERT INTO Cliente
(id, nome, cidade, salario)
VALUES
(1, "Ana", "Rio de Janeiro", 2500);
~~~

Desde que mantida a mesma ordem, a linha que informa as colunas pode ser ocultada:
~~~SQL
INSERT INTO Cliente
VALUES
(2, "Caio", "Niterói", 3100),
(3, "Artur", "São Gonçalo", 1700),
(4, "Lívia", "Rio das Ostras", 6600),
(5, "Helen", "Rio Bonito", 3400),
(6, "Rodrigo", "Macaé", 9200),
(7, "Elena", "Maricá", 10300),
(8, "Mauro", "Cabo Frio", 4200),
(9, "Rute", "Saquarema", 5500),
(10, "Henrique", "Petrópolis", 1800);
~~~

**Comando UPDATE:** Atualização dos dados na tabela. Sintaxe:
~~~SQL
UPDATE Tabela
SET coluna1 = valor2, coluna2 = valor2 ...
WHERE condição;
~~~

Atualização de dados:
~~~SQL
UPDATE Cliente
SET cidade = "São Gonçalo"
WHERE id = 2;
~~~

Caso a condição seja omitida, todas as linhas da tabela serão atualizadas.
~~~SQL
UPDATE Cliente
SET idade = 18;
~~~

**Comando DELETE:** Remoção de dados da tabela. Sintaxe:
~~~SQL
DELETE FROM Tabela
WHERE condição;
~~~

Exclusão de dados:
~~~SQL
DELETE FROM Cliente
WHERE id = 1;
~~~

Se a condição não for informada, todas as linhas da tabela serão removidas.
~~~SQL
DELETE FROM Cliente;
~~~
### DQL

**Comando SELECT:** Consulta a todos os campos da tabela (padrão).
~~~SQL
SELECT * FROM Tabela
WHERE condição
~~~

Seleção de dados
~~~SQL
SELECT * FROM Cliente
WHERE nome = "Ana"
~~~

Caso a condição seja omitida, todas as linhas da tabela serão consultadas.
~~~SQL
SELECT * FROM Cliente
~~~
### Funções de Agregação

Essas funções agrupam um conjunto de valores em um único resultado, após a realização de uma determinada operação por um comando em SQL, o agrupamento é dado pelo `GROUP BY`.

Após o agrupamento pode ser efetuado uma filtragem (opcional), essa filtragem sobre o agrupamento realizado é feita com o `HAVING`.

| Comando  |         Descrição          |
| :------: | :------------------------: |
|  SELECT  |     Consulta os dados      |
| GROUP BY |      Agrupa os dados       |
|  HAVING  | Filtra os valores do grupo |

Dessa forma, as principais funções de agregação são:

| Função de Agregação |               Descrição               |
| :-----------------: | :-----------------------------------: |
|        COUNT        |     Total de linhas no resultado      |
|         SUM         |    Somatório de valores da coluna     |
|         AVG         | Média aritmética de valores da coluna |
|         MAX         |         Maior valor da coluna         |
|         MIN         |         Menor valor da coluna         |
Consulta aos dados da tabela, aplicando função de agregação. Se a função for aplicada, o agrupamento é obrigatório.
~~~SQL
SELECT função(campo1), campo2
FROM Tabela
[WHERE condição] Pode ser oculta
GROUP BY campo2
~~~

Contar e Agrupar
~~~SQL
SELECT COUNT(*), cidade
FROM Cliente
GROUP BY cidade
~~~

Consulta aos dados da tabela, aplicando função de agregação e filtragem dos dados agregados. Se a função for aplicada, o agrupamento é obrigatório. 
~~~SQL
SELECT função(campo1), campo2
FROM Tabela
[WHERE condição1] Pode ser oculta
GROUP BY campo2
[HAVING condição2] Pode ser oculta
~~~

A filtragem do agrupamento é opcional
~~~SQL
SELECT COUNT(*), cidade
FROM Cliente
GROUP BY cidade
HAVING COUNT(*) > 10
~~~

### Ordenação

Caso deseje que o resultado da consulta pode vir ordenado. A ordenação poderá ser crescente (ASC) ou decrescente (DESC). Lembre-se, é sempre a última coisa a ser aplicada na consulta elaborada com um comando SQL, independente se ela tenha funções de agregação ou não:

Sintaxe:
~~~SQL
SELECT * FROM Tabela
[WHERE condição] Pode ser oculta
ORDER BY campo1, campo2 [ASC|DESC]
~~~

Exemplo de aplicar ordenação crescente/ascendente (ASC)
~~~SQL
SELECT * FROM Cliente
ORDER BY nome, cidade ASC
~~~

Consulta aos dados da tabela, aplicando função de agregação e ordenação crescente (ASC) ou decrescente (DESC) combinadas.

Sintaxe:
~~~SQL
SELECT função(campo1), campo2
FROM Tabela
[WHERE condição1] Pode ser oculta
GROUP BY campo2
[HAVING condição2] Pode ser oculta
ORDER BY função(campo1), campo2 [ASC|DESC]
~~~

SQL:
~~~SQL
SELECT COUNT(*), cidade
FROM Cliente
GROUP BY cidade
HAVING COUNT(*) > 10
ORDER BY cidade DESC
~~~
## Referências
- [SQL](https://www.estrategiaconcursos.com.br/blog/banco-dados-principais-comandos-sql/)