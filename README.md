# ETHDaddy

ETHDaddy is a Dapp version of GoDaddy, where you can buy and sell domain names as ERC721 tokens. Take advantage of this unique opportunity to acquire the perfect domain name for your project on the Ethereum blockchain.

The ETHDaddy contract code is available [here](contracts/ETHDaddy.sol).


## Running ETHDaddy Locally

To run ETHDaddy locally on your machine, follow these steps:

1. Install Node.js and npm.
   - Example: `curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -`
   - Example: `sudo apt-get install -y nodejs`
2. Install the Hardhat CLI using npm: `npm install -g hardhat`.
3. Clone the ETHDaddy repository to your machine.
   - Example: `git clone https://github.com/nironwp/ETHDaddy.git`
4. Navigate to the ETHDaddy repository folder in your terminal and install the project dependencies using npm: `npm install`.
5. Start the local Hardhat network by running the command `npx hardhat node` in the terminal.
6. Connect MetaMask to the local Hardhat network, see following section if you don't know how to do this.
7. Deploy the ETHDaddy contract to the local Hardhat network using MetaMask.
8. Test the ETHDaddy contract using the provided test file.
   - Example: `npx hardhat test`

## Introduction

The ETHDaddy frontend was created with the goal of providing a user-friendly interface for users to interact with the ETHDaddy contract on the Ethereum blockchain. It was built using the React framework and the ethers.js account and transaction management library.

## Project Structure

The ETHDaddy frontend is structured as follows:

- `App.js`: the main component that manages the blockchain connection and ETHDaddy contract data. It renders the navigation, search, and domain components.

- `Navigation.js`: the navigation component that displays the user's account address and allows the user to disconnect the current account.

- `Search.js`: the search component that allows the user to search for a specific domain.

- `Domain.js`: the domain component that displays information about a specific domain and allows the user to purchase the domain if it has not already been sold.

## Connecting to the Blockchain

The `App` component uses the `useEffect` hook to call the `loadBlockchainData` function as soon as the component is first rendered. The `loadBlockchainData` function creates a new Web3 provider using the global `window.ethereum` object and stores it in state. It then uses the provider to get the current network and creates a new instance of the ETHDaddy contract using the contract address on the network.

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
## Configuring the Hardhat Local Network with MetaMask

If you already have MetaMask installed and a Hardhat local network running, and you only want to configure MetaMask to connect to the local network, follow these steps:

1. Open MetaMask.
2. Click on the menu icon in the top left corner and select "Settings."
3. In the "Networks" tab, click "Add Network."
4. Enter the following information:
   - Network Name: HardHat
   - New RPC URL: <http://127.0.0.1:8545>
   - Chain ID: 31337
   - Currency Symbol: ETH
5. Click "Save."
