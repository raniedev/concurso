# Componentes da Infraestrutura

A infraestrutura oferece a plataforma para suporte de todos os sistemas de informação na empresa. A infraestrutura da TI de uma empresa compõe-se de Hardware, Software, Tecnologia de Gestão, Tecnologia de Rede e Serviços de Tecnologia.
## Hardware

- **Tipos de Computadores:** Computador Desktop, Smartphones, Notebooks, Netbooks, Smartwatches, Leitores de E-book, Tablet etc.
- **[Servidores](Servidores.md):** Suporta redes de computadores, compartilhando arquivos e recursos.
- **Mainframes:** Computador de maior capacidade e de mais alto desempenho que consegue processar rapidamente grandes volumes de dados.
- **Supercomputadores:** Computador mais sofisticado, de projeto especial, usado para executar tarefas que requerem cálculos complexos e extremamente rápidos, com milhares de variáveis, milhões de medidas.
- **Computadores Quânticos:** Um computador quântico é uma nova categoria de máquina de computação que utiliza princípios da física quântica para processar informações, ao invés de bits (0 ou 1). Em vez de bits, ele usa qubits, que podem estar em uma superposição de estados (0 e 1 simultaneamente), permitindo realizar cálculos complexos em paralelo e de forma exponencialmente mais rápida que os supercomputadores convencionais para certos problemas.
- **Computação em Grade:** Conecta, em uma única rede, computadores geograficamente distantes, criando assim um “supercomputador virtual”.
- **Computação cliente/servidor:** Forma de computação distribuída, divide o processo entre "clientes" e "servidores". Os clientes são ponto de entrada do usuário e os servidores armazenam e processam dados compartilhados e executam funções de gerenciamento de rede.

### Client Server Model
Existem dois tipos de computação cliente/servidor: o de duas camadas e de multicamadas.
#### Cliente Servidor de 2 Camadas
Nesta computação, o processamento computacional é dividido entre máquinas clientes e máquinas servidoras conectadas por uma rede através do [protocolo TCP/IP](TCP%20IP.md). O usuário interage com a interface das máquinas clientes e estas se comunicam com as máquinas servidoras conectadas por uma rede.

#### Cliente Servidor de Multicamadas (N-Tier ou 3-Tier)
Divide as funções da aplicação em **três ou mais camadas**, para melhorar desempenho, segurança e escalabilidade.

A forma mais comum é a **arquitetura de três camadas (3-tier):**

1. **Camada de Apresentação (Cliente):**  
    Interface com o usuário (navegador, aplicativo, etc.).
    
2. **Camada de Lógica/Negócio (Servidor de Aplicação):**  
    Onde ficam as regras do sistema e o processamento das solicitações.
    
3. **Camada de Dados (Servidor de Banco de Dados):**  
    Onde os dados são armazenados e consultados.

