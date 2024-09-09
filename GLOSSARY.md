<h1 align="center">Dicionário de termos</h1>

Este documento contém a definição de termos estudados durante a pesquisa do projeto.

### Beacon Chain Light Client
* **Beacon Chain**: É uma parte central da arquitetura do Ethereum 2.0, responsável pela coordenação da rede, incluindo a seleção de validadores e a aplicação de regras de consenso para a rede PoS. A Beacon Chain gerencia a prova de stake e introduz o conceito de sharding, que é essencial para escalabilidade.
* **Light Client**: Um light client é uma versão simplificada de um cliente blockchain que não precisa baixar toda a blockchain para operar. Ele se comunica com full nodes para verificar transações e blocos de forma eficiente e segura, tornando-o ideal para dispositivos com recursos limitados, como smartphones. Um Beacon Chain Light Client especificamente lida com interações com a Beacon Chain de forma simplificada, permitindo que dispositivos menores participem da rede Ethereum 2.0 sem precisar processar toda a Beacon Chain.

### Consensus Client
* **Função**: O consensus client é responsável por garantir que todos os nós da rede concordem sobre o estado da blockchain. Ele implementa o protocolo de consenso, como o Proof of Stake (PoS) no Ethereum 2.0, e gerencia a sincronização entre os nós da rede, garantindo que todos tenham uma visão consistente da blockchain.
* **Responsabilidades**: Participar do consenso (Proof of Stake); escolher validadores e propor/validar blocos; sincronizar a rede e aplicar punições/recompensas aos validadores.

### Execution Client
* **Função**: O execution client é responsável por executar as transações e manter o estado da blockchain. Ele processa transações, cria novos blocos (baseado nas regras do Ethereum), e gerencia a Ethereum Virtual Machine (EVM), onde os contratos inteligentes são executados.
* **Responsabilidades**:Validar e aplicar transações; manter o banco de dados da blockchain; executar contratos inteligentes.

### Proof of Authority (PoA)
* É um algoritmo de consenso utilizado em blockchains que é baseado na reputação de validadores em vez de um recurso computacional (como em Proof of Work) ou de quantidade de criptomoedas (como em Proof of Stake). No PoA, a identidade dos validadores é a parte mais importante e os validadores são selecionados com base em sua confiança e reputação.
* **Validadores**: Em uma rede PoA, um conjunto fixo e conhecido de validadores é responsável por criar novos blocos e adicionar transações à blockchain. Esses validadores geralmente são entidades ou indivíduos conhecidos e confiáveis, como empresas, organizações ou indivíduos de confiança.

### Proof of Stake (PoS)
* **Como funciona**: Em vez de minerar blocos, os validadores são escolhidos com base na quantidade de criptomoedas que possuem e estão dispostos a "travar" (ou seja, colocar em stake). Quanto mais tokens um validador tem em stake, maior a chance de ser escolhido para validar o próximo bloco e ganhar recompensas.
* **Vantagens**: Consome menos energia do que PoW, é mais rápido e pode ser mais seguro, pois desencoraja ataques, já que os validadores têm um grande investimento na rede.
* **Desvantagens**: A centralização pode ocorrer se poucos validadores controlarem a maioria dos tokens em stake.

### Proof of Work (PoW)
* **Como funciona**: Os mineradores competem para resolver complexos problemas matemáticos. O primeiro a resolver o problema tem o direito de adicionar o próximo bloco de transações à blockchain e é recompensado com criptomoedas. Esse processo é chamado de mineração.
* **Vantagens**: Alta segurança, já que atacar a rede requer um poder computacional extremamente alto.
* **Desvantagens**: Consumo elevado de energia e recursos computacionais, tornando-se ambientalmente insustentável em grande escala.

### Web3
Ver o artigo [Introdução à Web3](https://ethereum.org/pt-br/web3/).