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

O Geth é um client de execução, e assim é necessário que haja também um client de concenso para formar um nó Ethereum, uma vez que ele funciona com consenso baseado em proof-of-stake.

Existem cinco clients de consenso disponíveis para o Geth (ver [consensus clients](https://geth.ethereum.org/docs/getting-started/consensus-clients#consensus-clients)). E utilizaremos o Kurtosis para auxiliar nessa tarefa.

### Requisitos

* [Docker](https://www.docker.com/) (versão 4.33.1 ou superior)
* [Kurtosis CLI](https://docs.kurtosis.com/) (versão 1.2 ou superior)

Após a instalação dos requisitos, execute o Docker e execute o comando na raiz desse repositório:

```
kurtosis run github.com/ethpandaops/ethereum-package --args-file ./network_params.yaml --image-download always
```

Como resultado, alguns containers serão criados e poderemos ver as rotas disponíveis, como abaixo por exemplo.

```
INFO[2024-10-11T23:42:46-03:00] ========================================================== 
INFO[2024-10-11T23:42:46-03:00] ||          Created enclave: weathered-glacier          || 
INFO[2024-10-11T23:42:46-03:00] ==========================================================
Name:            weathered-glacier
UUID:            1a76978c64f6
Status:          RUNNING
Creation Time:   Wed, 11 Oct 2024 23:35:56 -03
Flags:

========================================= Files Artifacts =========================================
UUID           Name
b3c75a73254f   1-lighthouse-geth-0-63-0
756cbcad2ae1   2-lighthouse-geth-64-127-0
de19a8fe5fd1   3-teku-geth-128-191-0
5ab387d70d9c   dora-config
2b33eec69f98   el_cl_genesis_data
f772881b21e7   final-genesis-timestamp
22d9f52f3793   genesis-el-cl-env-file
a92e1684d2a4   genesis_validators_root
00200677e2d6   jwt_file
7baebb5ba750   keymanager_file
f143a9162a3b   prysm-password
337bcd4d7f97   validator-ranges

========================================== User Services ==========================================
UUID           Name                                             Ports                                         Status
3d21f2f10823   cl-1-lighthouse-geth                             http: 4000/tcp -> http://127.0.0.1:56161      RUNNING
                                                                metrics: 5054/tcp -> http://127.0.0.1:56162   
                                                                tcp-discovery: 9000/tcp -> 127.0.0.1:56163    
                                                                udp-discovery: 9000/udp -> 127.0.0.1:62682    
4262b81ccb0d   cl-2-lighthouse-geth                             http: 4000/tcp -> http://127.0.0.1:56846      RUNNING
                                                                metrics: 5054/tcp -> http://127.0.0.1:56843   
                                                                tcp-discovery: 9000/tcp -> 127.0.0.1:56845    
                                                                udp-discovery: 9000/udp -> 127.0.0.1:59781    
f6a7a0f97c7c   cl-3-teku-geth                                   http: 4000/tcp -> http://127.0.0.1:56934      RUNNING
                                                                metrics: 8008/tcp -> http://127.0.0.1:56935
                                                                tcp-discovery: 9000/tcp -> 127.0.0.1:56938    
                                                                udp-discovery: 9000/udp -> 127.0.0.1:53188
53d5fc9c5ec2   dora                                             http: 8080/tcp -> http://127.0.0.1:58428      RUNNING
8bdd7c6a3771   el-1-geth-lighthouse                             engine-rpc: 8551/tcp -> 127.0.0.1:55916       RUNNING
                                                                metrics: 9001/tcp -> http://127.0.0.1:55917   
                                                                rpc: 8545/tcp -> 127.0.0.1:55919
                                                                tcp-discovery: 30303/tcp -> 127.0.0.1:55918   
                                                                udp-discovery: 30303/udp -> 127.0.0.1:65461
                                                                ws: 8546/tcp -> 127.0.0.1:55915
6ae9a280d8cd   el-2-geth-lighthouse                             engine-rpc: 8551/tcp -> 127.0.0.1:55994       RUNNING
6ae9a280d8cd   el-2-geth-lighthouse                             engine-rpc: 8551/tcp -> 127.0.0.1:55994       RUNNING
                                                                metrics: 9001/tcp -> http://127.0.0.1:55995
                                                                rpc: 8545/tcp -> 127.0.0.1:55997
                                                                tcp-discovery: 30303/tcp -> 127.0.0.1:55996
                                                                udp-discovery: 30303/udp -> 127.0.0.1:65505
                                                                ws: 8546/tcp -> 127.0.0.1:55998
abebdf22a294   el-3-geth-teku                                   engine-rpc: 8551/tcp -> 127.0.0.1:56092       RUNNING
6ae9a280d8cd   el-2-geth-lighthouse                             engine-rpc: 8551/tcp -> 127.0.0.1:55994       RUNNING
                                                                metrics: 9001/tcp -> http://127.0.0.1:55995
                                                                rpc: 8545/tcp -> 127.0.0.1:55997
                                                                tcp-discovery: 30303/tcp -> 127.0.0.1:55996
                                                                udp-discovery: 30303/udp -> 127.0.0.1:65505
6ae9a280d8cd   el-2-geth-lighthouse                             engine-rpc: 8551/tcp -> 127.0.0.1:55994       RUNNING
                                                                metrics: 9001/tcp -> http://127.0.0.1:55995
                                                                rpc: 8545/tcp -> 127.0.0.1:55997
                                                                tcp-discovery: 30303/tcp -> 127.0.0.1:55996
6ae9a280d8cd   el-2-geth-lighthouse                             engine-rpc: 8551/tcp -> 127.0.0.1:55994       RUNNING
                                                                metrics: 9001/tcp -> http://127.0.0.1:55995
6ae9a280d8cd   el-2-geth-lighthouse                             engine-rpc: 8551/tcp -> 127.0.0.1:55994       RUNNING
                                                                metrics: 9001/tcp -> http://127.0.0.1:55995
                                                                rpc: 8545/tcp -> 127.0.0.1:55997
                                                                tcp-discovery: 30303/tcp -> 127.0.0.1:55996
                                                                udp-discovery: 30303/udp -> 127.0.0.1:65505
                                                                ws: 8546/tcp -> 127.0.0.1:55998
abebdf22a294   el-3-geth-teku                                   engine-rpc: 8551/tcp -> 127.0.0.1:56092       RUNNING
                                                                metrics: 9001/tcp -> http://127.0.0.1:56093
                                                                rpc: 8545/tcp -> 127.0.0.1:56090
                                                                tcp-discovery: 30303/tcp -> 127.0.0.1:56094
                                                                udp-discovery: 30303/udp -> 127.0.0.1:60599
                                                                ws: 8546/tcp -> 127.0.0.1:56091
bd930f8075a5   validator-key-generation-cl-validator-keystore   <none>                                        RUNNING
eb8369bee66a   vc-1-geth-lighthouse                             metrics: 8080/tcp -> http://127.0.0.1:58171   RUNNING
312d690b3025   vc-2-geth-lighthouse                             metrics: 8080/tcp -> http://127.0.0.1:58332   RUNNING
```

Juntamente com a rede blockchain, o explorador de blocos Dora poderá ser acessado como um serviço pelo link designado (no exemplo está como `http://127.0.0.1:54628`).

### Leitura Adicional

* [ethpandas](https://ethpandaops.io/posts/kurtosis-deep-dive/)
