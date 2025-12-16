# Sistemas de Controle de Versão

## Concurrent Versions System (CVS)

Um sistema de versões concorrente (CVS na sigla em inglês) é uma ferramenta para gerenciar o desenvolvimento de software colaborativo que permite que um grupo de desenvolvedores trabalhe no mesmo conjunto de arquivos fontes de forma que as alterações sejam integradas e persistidas em um repositório que guarde todas essas alterações.

As funcionalidades básicas de um sistema de controle de versão (CVS) são manter o histórico e os respectivos estados das alterações realizadas nos arquivos ao longo do tempo e integrar as contribuições dos diferentes desenvolvedores que atuam no projeto. Esse conjunto de histórico e estado dos arquivos é mantido em um diretório estruturado pelo servidor do CVS como repositório, desempenhando o servidor CVS um papel central e permitindo que os desenvolvedores trabalhem remotamente (seja na mesma rede local ou via internet) de forma colaborativa.

## Subversion (SVN)

Apache Subversion,  é um sistema de controle de versão de código aberto, criado em 2000 pela CollabNet e é atualmente um software mantido como um projeto da Apache Software Foundation. Foi desenvolvido para funcionar de forma similar ao CVS, mas corrigindo algumas falhas de seu antecessor e para prover algumas funcionalidades não existentes no CVS. O SVN é multiplataforma (tanto no que tange o servidor quanto os clientes) e pode ser usado por clientes com diferentes sistemas operacionais acessando um mesmo servidor que mantém o repositório.

O SVN é um sistema de versionamento flexível, que mantém o histórico mesmo após a ocorrência de eventos como mover, copiar ou renomear. Essas três características não estão presentes em muitos sistemas de controle de versão, mais notavelmente no CVS. Além disso, o SVN trabalha com o conceito e atomicidade nas operações, não permitindo operações parciais, que poderiam prejudicar a consistência do repositório.

### Solução Lock - Modifica - Unlock

Somente uma pessoa por vez modifica o mesmo arquivo. Os outros terão acesso apenas para leitura, é a solução mais simples e menos propensa a ter conflitos de edição.

**Desvantagens:**
- Pessoas podem esquecer de dar "unlock" para liberar o arquivo ao finalizar a modificação
- Impede que modificações sejam feitas ao mesmo tempo por duas ou mais pessoas, que desejam aplicar modificações em lugares diferentes do documento, o que dificilmente resultaria em um conflito

### Solução Copia - Modifica - Merge

Nesse modelo, cada um lê o repositório e cria uma cópia de trabalho local do projeto. Os usuários trabalham em paralelo, modificando as suas cópias dos arquivos e por fim o merge com a versão anterior é feito, criando uma nova versão. O sistema de controle de versões ajuda nessa etapa mas a responsabilidade do sucesso da operação de merge recai sobre o usuário.

Se um usuário tentar atualizar o repositório com as suas alterações e o arquivo de origem não for mais o mesmo que resultou na sua cópia local, um erro de "arquivo desatualizado" seguido de uma sugestão de update é retornada.
## SVN CheatSheet

#### Adicionar
 
 Adicionar todos arquivos ou pastas
~~~svn
svn add *
~~~

Adicionar um determinado item, se for uma pasta também irá adicionar suas subpastas e arquivos
~~~svn
svn add arquivo
~~~

Por padrão o `svn add` não entra em diretórios já versionados, ele adiciona apenas novos arquivos e pastas não versionadas no nível atual. Ao usar o comando `--force` será forçado a entrada em diretórios versionados e adiciona novos arquivos dentro deles
~~~svn
svn add * --force
~~~
#### Apagar

Apagar diretórios ou arquivos
~~~svn
svn delete "Pasta/"
~~~

Se desejar apagar e ao mesmo tempo informar uma mensagem
~~~svn
svn -m "Apagar pasta de filmes." delete "Movies/"
~~~

Copiar arquivo de um determinado lugar para um outro destino
~~~svn
svn copy "arquivo.pdf" "Documents/Arquivos/arquivo.pdf"
svn commit -m "Copiando arquivo.pdf para Documents/Arquivos/"
~~~

Mover diretório ou arquivo segue o mesmo padrão de passar o "lugar de origem" e o "lugar de destino".
~~~svn
svn move "Pasta/" "Documents/Arquivos/"
svn commit -m "Movendo diretório Pasta/ para Documents/Arquivos/"
~~~
#### Argumentos

| Argumento             | Significado                                                         |
| --------------------- | ------------------------------------------------------------------- |
| -m ou --message       | adiciona mensagem de log/commit.                                    |
| -q ou --quiet         | oculta saídas, modo silencioso., mostra apenas erros, sem detalhes. |
| -v ou --version       | modo detalhado, mostra mais informações.                            |
| -r  ou --revision     | Eescolhe uma revisão específica.                                    |
| -c ou --change        | aplica ou mostra uma alteração específica.<br>                      |
| -t ou --transation    | trabalha com transações (uso avançado/admin).                       |
| -R ou --recursive     | executa de forma recursiva (entra nas pastas).                      |
| -N ou --non-recursive | executa de forma não recursiva (somente o nível atual).             |

Envia mudanças para o repositório.

~~~cmd
svn commit -m "Arquivo adicionado"
~~~

Atualizar o repositório local com as últimas modificações do repositório remoto.

~~~cmd
svn update
~~~

Checar status do repositório

~~~cmd
svn status
~~~

Checar mudanças do diretório

~~~cmd
svn diff arquivo.txt
~~~

Checar o histórico

~~~cmd
svn log arquivo.txt
~~~

Reverter mudanças não receberam commit ainda

~~~cmd
svn revert arquivo.txt
~~~

Apagar arquivo ou diretório

~~~cmd
svn delete arquivo.txt
svn delete folder/
~~~

Mover/Renomear arquivo ou diretório

~~~cmd
svn move arquivo.txt meus-arquivos/arquivo.txt
svn move arquivo.txt file.txt
~~~

Obter metadados do arquivo

~~~cmd
svn info arquivo.txt 
~~~

Copiar arquivo 

~~~cmd
svn copy foo.txt bar.txt
~~~

Copiar arquivo local para repositório remoto e já commitar

~~~cmd
svn copy near.txt https://svn.example.com/repos/test/far.txt -m "Remote copy."
~~~

Copiar do repositório remoto para local e entre duas URLs também é possível.

## Referências

- [Sistema de Controle de Versão](https://www.devmedia.com.br/sistema-de-controle-de-versao-em-projetos-web/31876)
- [SVN CheatSheet 1](https://www.cheat-sheets.org/saved-copy/subversion-cheat-sheet-v1.pdf)
- [SVN CheatSheet 2](https://overapi.com/svn)