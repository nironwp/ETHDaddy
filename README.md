# ETHDaddy

O ETHDaddy é um website inspirado no Godaddy, mas na versão Dapp. Aqui, você pode comprar e vender nomes de domínios como tokens ERC721. Aproveite essa oportunidade única de adquirir o nome de domínio perfeito para o seu projeto na blockchain Ethereum.

O código do contrato ETHDaddy está disponível [aqui](contracts/ETHDaddy.sol).


## Executando o ETHDaddy localmente

Para executar o ETHDaddy localmente em sua máquina, siga os seguintes passos:

1. Instale o Node.js e o npm.
   - Exemplo: `curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -`
   - Exemplo: `sudo apt-get install -y nodejs`
2. Instale o Hardhat CLI usando o npm: `npm install -g hardhat`.
3. Clone o repositório do ETHDaddy em sua máquina.
   - Exemplo: `git clone https://github.com/nironwp/ETHDaddy.git`
4. Navegue até a pasta do repositório do ETHDaddy no terminal e instale as dependências do projeto usando o npm: `npm install`.
5. Inicie a rede local Hardhat executando o comando `npx hardhat node` no terminal.
6. Conecte o MetaMask à rede local Hardhat, caso não saiba consulte a seguinte sessão
7. Faça o deploy do contrato ETHDaddy para a rede local Hardhat usando o MetaMask.
8. Teste o contrato ETHDaddy usando o arquivo de testes fornecido.
   - Exemplo: `npx hardhat test`

## Introdução

O frontend do ETHDaddy foi criado com o objetivo de fornecer uma interface amigável para os usuários interagirem com o contrato ETHDaddy na blockchain Ethereum. Ele foi construído utilizando o framework React e a biblioteca de gerenciamento de contas e transações ethers.js.

## Estrutura do projeto

O frontend do ETHDaddy é estruturado da seguinte forma:

- `App.js`: componente principal que gerencia a conexão com a blockchain e os dados do contrato ETHDaddy. Ele renderiza os componentes de navegação, busca e domínio.

- `Navigation.js`: componente de navegação que exibe o endereço da conta do usuário e permite que o usuário desconecte a conta atual.

- `Search.js`: componente de busca que permite que o usuário pesquise por um domínio específico.

- `Domain.js`: componente de domínio que exibe informações sobre um domínio específico e permite que o usuário compre o domínio, se ele ainda não tiver sido vendido.

## Conectando a blockchain

O componente `App` usa o hook `useEffect` para chamar a função `loadBlockchainData` assim que o componente é renderizado pela primeira vez. A função `loadBlockchainData` cria um novo provedor Web3 usando o objeto global `window.ethereum` e o armazena no estado. Em seguida, ela usa o provedor para obter a rede atual e cria uma nova instância do contrato ETHDaddy usando o endereço do contrato na rede.

```javascript
const loadBlockchainData = async () => {
  const provider = new ethers.providers.Web3Provider(window.ethereum)
  setProvider(provider)

  const network = await provider.getNetwork()
  const ethDaddy = new ethers.Contract(config[network.chainId].ETHDaddy.address, ETHDaddy, provider)
  setETHDaddy(ethDaddy)
  // ...
}
```
## Configurando a rede local Hardhat com o MetaMask

Se você já tem o MetaMask instalado e uma rede local Hardhat iniciada e deseja apenas configurar o MetaMask para se conectar à rede local, siga os seguintes passos:

1. Abra o MetaMask.
2. Clique no ícone do menu no canto superior esquerdo e selecione a opção "Settings".
3. Na aba "Networks", clique em "Add Network".
4. Insira as seguintes informações:
   - Nome da rede: HardHat
   - Novo URL da RPC: <http://127.0.0.1:8545>
   - ID da cadeia: 31337
   - Símbolo da moeda: ETH
5. Clique em "Save".
