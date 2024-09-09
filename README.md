<h1 align="center">Desenvolvimento de ambiente de teste para blockchain utilizando Kubernetes</h1>

## Descrição do projeto

- [Dicionário de termos](GLOSSARY.md)

### Levantamento de tecnologias

As seguintes imagens foram consideradas para essa pesquisa:

1. [ethereum/client-go](https://geth.ethereum.org): implementação oficial em Golang da camada de execução do protocolo Ethereum.
1. [openethereum/openethereum](https://github.com/openethereum/openethereum)
1. [hyperledger/fabric-peer](https://hyperledger-fabric.readthedocs.io/en/latest/): uma estrutura de ledger distribuído permissionada de nível empresarial para desenvolver soluções e aplicações.
1. [quorumengineering/quorum](https://github.com/Consensys/quorum)

Analizando as imagens, foi escolhida a ethereum/client-go, também chamada de Geth, por sua documentação mais organizada e comunidade mais ativa.

### Particularidades das tecnologias

O Geth é um client de execução, e assim é necessário que haja também um client de concenso para formar um nó Ethereum, uma vez que ele funciona com cnonsenso baseado em proof-of-stake.

Existem cinco clients de consenso disponíveis para o Geth (ver [Consensus clients](https://geth.ethereum.org/docs/getting-started/consensus-clients#consensus-clients)). E utilizaremos o Kurtosis para auxiliar nessa tarefa.

### Requisitos

* [Docker](https://www.docker.com/) (versão 4.33.1 ou superior)
* [Kurtosis CLI](https://docs.kurtosis.com/) (versão 1.2 ou superior)