# OLTP (Online Transaction Processing)

O OLTP permite a execução em tempo real de um grande número de transações de bancos de dados por um grande número de pessoas, geralmente pela internet. É um modelo de banco de dados otimizado para **operações transacionais**: inserções, atualizações, consultas simples e rápidas, feitas por muitos usuários simultaneamente.


1. **Transações curtas e rápidas:** Essas transações duram milissegundos e precisam ter um tempo de resposta quase que imediato, são elas: INSERT, UPDATE, DELETE, SELECT (Simples)
2. **Suporte a muitos usuários ao mesmo tempo:** Bancos OLTP lidam com <u>alta concorrência</u>, com milhares ou milhões de operações diárias, usam controle como: Bloqueios, Controle de concorrência, Níveis de isolamento.
3. **Dados altamente normalizados:** Geralmente usam 3FN (3ª forma normal ou superior) para evitar redundância, garantir integridade e facilitar atualizações rápidas.
4. **Alta integridade e consistência (ACID):** Transações OLTP seguem os princípios de <u style="font-weight: bold">A</u>tomicidade, <u style="font-weight: bold">C</u>onsistência, <u style="font-weight: bold">I</u>ntegridade e <u style="font-weight: bold">D</u>urabilidade.
5. **Consultas simples e de pequeno volume:** Consulta complexas são evitadas, pois prejudicam o desempenho das transações. Por isso a análise de dados é geralmente feita em outro tipo de banco ([OLAP](../OLAP/OLAP.md) ou Data Warehouse)
6. **Manutenção em tempo real:** Os dados são atualizados constantemente, refletindo o estado atual do sistema.

### ACID

- **Atomicidade:** Todas as alterações são realizadas como se fossem uma única operação. Ou seja, todas as mudanças serão realizadas ou o processo será cancelado e nenhuma delas serão alteradas.
- **Consistência:** Os dados estão em um estado consistente quando uma transação começa e quando ela termina. O banco de dados seguem todas as regras, o banco de dados nunca deve terminar em um estado "impossível", "quebrado" ou com regras violadas. 
	Ex.: Para realizar uma transferência em uma conta bancária o saldo nunca pode ser negativo, se o cliente tem R$500 reais na conta e está tentando transferir iria violar a regra. Logo, a transação é cancelada.
- **Isolabilidade:** Uma transação é "invisível" para outras transações. 
- **Durabilidade:** Após uma transação ser concluída com sucesso, as mudanças nos dados persistem e não são desfeitas, mesmo em caso de falha no sistema.

#### Como que o sistema falha e consegue garantindo a durabilidade?

1. **Uso do Write-Ahead Log (WAL) - Registro de Log:** Antes de gravar a mudança no banco, o SGBD escreve em um arquivo de log (em disco) tudo o que a transação vai alterar. Se o sistema cair antes de gravar os dados finais, o banco pode reconstruir tudo a partir do log.
2. **Commit só é confirmado depois que o log está no disco:** O SGBD só responde “Transação concluída” se:
	- O log com todas as operações já está gravado com sucesso no disco (não só em cache!)
	- O sistema tem certeza de que pode recuperar os dados em caso de queda
## Referências

- [OLTP](https://www.ibm.com/br-pt/think/topics/oltp)
- [ACID](https://www.ibm.com/docs/pt-br/cics-tx/11.1.0?topic=processing-acid-properties-transactions)