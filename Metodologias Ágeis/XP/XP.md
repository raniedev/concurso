# Extreme Programming

É uma tecnologia ágil de desenvolvimento de software, que visa entregar valor ao cliente de forma rápida e contínua, adaptando-se às mudanças e priorizando a qualidade do produto final. Suas práticas consistem de práticas extremas de programação colaborativa, testes contínuos e feedback rápido.

## O Clico de Release

No XP, o desenvolvimento de software é organizado em ciclos curtos e repetitivos chamados de *releases*. Cada release representa uma versão funcional do software que é entregue ao cliente para obtenção de feedback. O ciclo de release contínuo do XP segue uma abordagem **iterativa e incremental**, em que novas funcionalidades são adicionadas em cada iteração, priorizadas com base no valor para o cliente.

![Ciclo Release do XP](../imgs/ciclo-release.png)
## Princípios ou Práticas do XP

### Planejamento Incremental

O planejamento do XP é feito de forma incremental, com foco em entregar funcionalidades de alto valor de forma iterativa. Isso permite que o software evolua de maneira adaptativa, à medida que novos requisitos são descobertos ou priorizados.

### Pequenos Releases

O XP preconiza a entrega de pequenos releases frequentes, permitindo que o cliente experimente e forneça feedback rapidamente. Isso ajuda a mitigar o risco e a incerteza, garantindo que o software atenda às necessidades reais do usuário.

### Projeto Simples

A simplicidade é valorizada no XP, com foco na implementação da solução mais simples que atenda aos requisitos. Isso promove uma arquitetura flexível e fácil de dar manutenção, evitando o excesso de complexidade desnecessária.

### Desenvolvimento Test-First

No XP, os testes são escritos antes da implementação do código, seguindo o princípio do Test-Driven Development (TDD). Isso garante que o código seja testado continuamente e que novas funcionalidades sejam implementadas com base em requisitos claros e testáveis.

Os testes incluem tanto os testes unitários, escritos antes da implementação do código (TDD), quanto os testes de aceitação, que validam o comportamento do sistema como um todo. Essa abordagem garante a qualidade do software, detecta problemas precocemente e permite uma entrega contínua de valor ao cliente.

### Refatoração

A refatoração é uma prática essencial no XP, que consiste na melhoria contínua do código sem alterar seu comportamento externo. Isso ajuda a manter o código limpo, legível e fácil de dar manutenção, promovendo a evolução constante do software.

### Programação em Pares

Os programadores trabalham em pares no XP, colaborando e revisando o código uns dos outros em tempo real. Isso promove a comunicação eficaz, o compartilhamento de conhecimento e a melhoria da qualidade do código.

A prática de programação em pares no XP envolve dois programadores trabalhando juntos em um único computador. Um dos programadores escreve o código, enquanto o outro observa, revisa e oferece sugestões em tempo real. 

Essa colaboração promove a troca de conhecimento, a melhoria da qualidade do código e a redução de erros, resultando em um software mais robusto e de alta qualidade.

### Propriedade Coletiva

No XP, todo o código pertence à equipe como um todo, incentivando a colaboração e a responsabilidade compartilhada pela qualidade do software. Isso evita silos de conhecimento e garante que todos os membros da equipe se sintam responsáveis pelo sucesso do projeto.

### Integração Contínua

A integração contínua é uma prática essencial no XP, em que as alterações de código são integradas e testadas automaticamente várias vezes ao dia. Isso ajuda a detectar e corrigir problemas rapidamente, mantendo o software sempre em um estado funcional e pronto para entrega.

### Ritmo Sustentável

O XP promove um ritmo de trabalho sustentável, evitando o esgotamento da equipe e priorizando a qualidade do trabalho ao invés da quantidade de horas trabalhadas. Isso ajuda a manter a motivação e o engajamento da equipe ao longo do tempo.

### Cliente no Local

No XP, o cliente é uma parte integrante da equipe de desenvolvimento, fornecendo feedback contínuo e colaborando na definição de prioridades. Isso garante que o software atenda às necessidades reais do usuário e que as decisões sejam baseadas em dados concretos.

## Papéis

**Programador:** escrevem testes e mantém o programa o mais simples e conciso possível. A primeira característica que torna o XP possível é a habilidade de comunicação e coordenação com outros membros da equipe.

**Cliente:** escreve as estórias e os testes funcionais, além de decidir quando cada requisito foi satisfeito. O cliente também define a prioridade de implementação de cada requisito.

**Testador:** ajuda o cliente a escrever os testes funcionais. Ele também realiza os testes funcionais regularmente, comunicando os resultados dos testes e mantém o conjunto de testes.

**Monitor:** fornece a realimentação para a equipe do projeto. Ele acompanha a conformidade das estimativas feitas pela equipe de desenvolvimento (por exemplo, estimativas de esforço) e fornece comentários de quanto acuradas elas estão, para poder melhorar futuras estimativas. Ele também acompanha o progresso de cada iteração e avalia se o objetivo é viável dentro das limitações de tempo e recursos, ou se alguma mudança é necessária no processo.

**Treinador:** é a pessoa responsável pelo processo como um todo. Um profundo conhecimento do XP é importante para este papel, pois é ele que guiará os outros envolvidos no projeto a executar o processo de forma adequada.

**Consultor:** é um membro externo com conhecimento técnico específico necessário para o projeto. O consultor auxilia a equipe a resolver problemas específicos.

**Chefe:** responsável pelas tomadas de decisões. Para isso, ele comunica-se com a equipe de projeto para determinar a situação atual e para identificar qualquer dificuldade ou deficiência do processo.

**Os 5 Valores Fundamentais do XP:**

1. **Comunicação:** Comunicação constante e clara entre todos os membros da equipe e com o cliente para garantir alinhamento e entendimento.
2. **Simplicidade:** Fazer o essencial para o problema atual, evitando complexidades desnecessárias e construindo apenas o que é necessário.
3. **Feedback:** Entregar software funcional frequentemente para obter retorno rápido, permitindo ajustes e melhorias contínuas.
4. **Coragem:** Ter a ousadia de mudar o rumo, refatorar o código, adaptar requisitos e dizer a verdade sobre o progresso e estimativas.
5. **Respeito:** Valorizar cada membro da equipe e seu trabalho, reconhecendo que todos contribuem para o objetivo comum

Princípios Básicos (Como os Valores se Aplicam)

- **Feedback Rápido:** Entregar software em ciclos curtos para obter retorno constante.
- **Presumir Simplicidade:** Implementar a solução mais simples possível para o problema atual.
- **Mudanças Incrementais:** Fazer pequenas mudanças constantes, em vez de grandes saltos.
- **Abraçar Mudanças:** Ver a mudança como uma oportunidade, não como um problema.
- **Trabalho de Qualidade:** Manter um código limpo e bem testado, com alta qualidade desde o início. 

Práticas Comuns (A Implementação)

- **Test-Driven Development (TDD):** Escrever testes antes do código.
- **Programação em Par:** Dois desenvolvedores trabalhando juntos em um computador.
- **Integração Contínua:** Integrar o código frequentemente.
- **Cliente no Local:** O cliente participa ativamente do projeto.
- **Refatoração:** Melhorar o código existente sem mudar sua funcionalidade.

## Referências

- [eXtreme Programming  - Estratégia Concursos](https://www.estrategiaconcursos.com.br/blog/extreme-programming-xp-cef-ti/)

