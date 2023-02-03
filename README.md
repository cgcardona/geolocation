# Geolocation (GEO)

<img alt="Avalanche Logo" width="300px" src="assets/powered-by-avalanche.png">

Geolocation for ETH Denver Web3 game workshop

## Getting Started

Clone the repo

```zsh
git clone https://github.com/cgcardona/geolocation.git
cd geolocation
```

Install the dependencies

```zsh
yarn install
```

Create a .env file

```zsh
touch .env
```

Add the following values to `.env`

```zsh
ACCOUNT_PRIVATE_KEY = "hex-encoded-private-key-with-no-0x-prefix"
NETWORK = "https://api.avax-test.network/ext/bc/C/rpc"
NFT_CONTRACT_ADDRESS = ""
```

Make sure that your address has Fuji AVAX by visiting the [Avalanche Fuji Faucet](https://faucet.avax.network/) and getting a drip of 2 AVAX.

Compile the ERC721 smart contract

```zsh
npx hardhat compile
Compiled 12 Solidity files successfully
```

Deploy the ERC721 smart contract

```zsh
npx hardhat deploy
Contract deployed to address: 0x17eF28a5023c67551B5A03885826BD68FbC8647B
```

View the GEO contract [on snowtrace](https://testnet.snowtrace.io/token/0x17ef28a5023c67551b5a03885826bd68fbc8647b?a=0x46f3e64e4e3f5a46eaf5c292301c6174b9b646bf)

Add the contract address from the previous step to `NFT_CONTRACT_ADDRESS` in `.env`.

Mint the NFT to your address

```zsh
npx hardhat mint --address 0x46f3e64E4e3f5a46Eaf5c292301c6174B9B646Bf
Transaction Hash: 0x60d2170ba768c8062c23ffc94233104d8363afa364049a0ca2d05ec8fc4cfaae
```

view the transaction [on Snowtrace](https://testnet.snowtrace.io/tx/0x60d2170ba768c8062c23ffc94233104d8363afa364049a0ca2d05ec8fc4cfaae)
