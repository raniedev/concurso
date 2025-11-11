# Protocolo HTTP

**HTTP** é um protocolo que permite a obtenção de recursos, como documentos HTML. É a base de qualquer troca de dados na Web e um protocolo cliente-servidor, o que significa que as requisições são iniciadas pelo destinatário, geralmente um navegador da Web. Um documento completo é reconstruído a partir dos diferentes sub-documentos obtidos, como por exemplo texto, descrição do layout, imagens, vídeos, scripts e muito mais.

![Fetching a Page](../imgs/fetching-a-page.svg)

Clientes e servidores se comunicam trocando mensagens individuais (ao contrário de um fluxo de dados). As mensagens enviadas pelo cliente, geralmente um navegador da Web, são chamadas de **solicitações** _(requests)_, ou também **requisições**, e as mensagens enviadas pelo servidor como resposta são chamadas de **respostas** _(responses)_.

![HTTP Layers](../imgs/http-layers.svg)

O HTTP é um protocolo cliente-servidor, as requisições são enviadas por uma entidade, o agente-usuário (*user-agent*), ou um *proxy* em nome dele. Na maioria dos casos, o agente-usuário é um navegador na web, mas pode ser outras coisas, como: um robô varrendo a web para preencher e manter um índice de mecanismo de pesquisa e coletar informações.

Cada Requisição individual é enviada para um servidor, que irá lidar com isso e fornecer um resultado chamado de resposta. Entre a solicitação e a resposta existem várias entidades, designadas coletivamente como **proxies**, que executam operações diferentes e atuam como _gateways_ (intermediários) ou **caches**, por exemplo.
## Referências

- [Visão Geral do HTML](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Guides/Overview)