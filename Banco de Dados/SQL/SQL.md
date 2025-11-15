# Structured Query Language

SQL é uma linguagem de consulta estruturada, utilizada em banco de dados relacionais sob a forma de comandos. Apesar de ter consulta no nome, ela é utilizada para realizar outras operações que envolvam dados, tais como inserções, remoções etc.
## Classificação dos comandos em SQL

- **Data Manipulation Language (DML):** Comandos em SQL de manipulação dos dados nas tabelas. Em outras palavras, não alteram as tabelas, mas podem impactar os dados armazenados nelas.
- **Data Query Language (DQL):** Comandos em SQL de consulta aos dados nas tabelas.
>**ATENÇÃO:** A adoção do DQL para os comandos de consulta não é unânime. Alguns autores consideram esses comandos como DML, enquanto outros os consideram como DQL. Normalmente, a questão trará apenas um dos dois no gabarito. Contudo, se os dois estiverem entre as alternativas possíveis, recomendamos que marque o DQL, por ser mais específico.

- **Data Definition Language (DDL):** Comandos em SQL que atuam diretamente nas estruturas dos objetos de bancos. Só para exemplificar, os objetos podem ser tabelas, índices, sequências etc.
- **Data Control Language (DCL):** Comandos em SQL envolvendo permissões de acesso ao banco. Nesse sentido, estão atrelados diretamente com a segurança da informação.
- **Data Transaction Language (DTL):** Comandos em SQL relacionados com as transações no banco. São eles que confirmam ou desfazem as operações realizadas, em caso de sucesso ou erro.

### DML

**Comando INSERT:** Inserção dos dados na tabela (padrão). Sintaxe:

~~~SQL
INSERT INTO tabela
(coluna1, coluna2, coluna3, ...)
VALUES
(valor1, valor2, valor3, ...);
~~~

Inserção de dados:
~~~SQL
INSERT INTO Cliente
(id, nome, cidade, idade)
VALUES
(1, "Ana", "Rio de Janeiro", 25);
~~~

Desde que mantida a mesma ordem, a linha que informa as colunas pode ser ocultada:

~~~SQL
INSERT INTO Cliente
VALUES
(2, "Caio", "Niterói", 31);
~~~

**Comando UPDATE:** Atualização dos dados na tabela. Sintaxe:

~~~SQL
UPDATE Tabela
SET coluna1 = valor2, coluna2 = valor2 ...
WHERE condição;
~~~

> Condição pode ser diversos operadores de comparação, como: maior que, maior ou igual à, menor que, menor ou igual à, diferente, igual.
> Além de combinações com operadores lógicos AND, OR, NOT

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
DELETE FROM Cliente
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
## Referências
- [SQL](https://www.estrategiaconcursos.com.br/blog/banco-dados-principais-comandos-sql/)