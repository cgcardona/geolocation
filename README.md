# GeoPrize (GEO)

<img alt="Avalanche Logo" width="300px" src="assets/powered-by-avalanche.png">

Location based Web3 game for ETH Denver workshop.

## Getting Started

Clone the repo

```zsh
git clone https://github.com/cgcardona/geoprize.git
cd geoprize
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

## ERC721 Smart Contract

### Compile

Compile the ERC721 smart contract

```zsh
npx hardhat compile
Compiled 12 Solidity files successfully
```

### Deploy

Deploy the ERC721 smart contract

```zsh
npx hardhat deploy
Contract deployed to address: 0x17eF28a5023c67551B5A03885826BD68FbC8647B
```

View the GEO contract [on snowtrace](https://testnet.snowtrace.io/token/0x17ef28a5023c67551b5a03885826bd68fbc8647b?a=0x46f3e64e4e3f5a46eaf5c292301c6174b9b646bf)

Add the contract address from the previous step to `NFT_CONTRACT_ADDRESS` in `.env`.

### Mint

Mint the NFT to your address

```zsh
npx hardhat mint --address 0x46f3e64E4e3f5a46Eaf5c292301c6174B9B646Bf
Transaction Hash: 0x60d2170ba768c8062c23ffc94233104d8363afa364049a0ca2d05ec8fc4cfaae
```

view the transaction [on Snowtrace](https://testnet.snowtrace.io/tx/0x60d2170ba768c8062c23ffc94233104d8363afa364049a0ca2d05ec8fc4cfaae)

## IPFS

### Images

Add images to the `images/` directory and pack them to an IPFS-compatible CAR

```zsh
npx ipfs-car --pack images --output images.car
```

### Metadata

Add metadata to the `metadata/` directory and pack them to an IPFS-compatible CAR

```zsh
npx ipfs-car --pack metadata --output metadata.car
```

### NFT Storage

Upload both CARs to [nft.storage](https://nft.storage)

## Set Base Token URI

Set the base token URI for the deployed smart contract

```zsh
npx hardhat set-base-token-uri --base-url "https://bafybeigfcvhycaqmpl75tccq4mn66r53ebjqel4gxlfp6nsizeyj3bqhbm.ipfs.dweb.link/metadata/"
Transaction Hash: 0xe7f6f75ac8d3b0d9233688c87e6552a6282804d69b7ce5121cc34758961a049a
```

## Get the Token URI

Fetch the token metadata for the given token ID

```zsh
npx hardhat token-uri --token-id 1
Metadata URL: https://bafybeigfcvhycaqmpl75tccq4mn66r53ebjqel4gxlfp6nsizeyj3bqhbm.ipfs.dweb.link/metadata/1
Metadata fetch response: {
  "description": "The Castle of Cardona is arguably the most important medieval fortress in Catalonia and one of the most important in Spain. It is situated on a hill overlooking the river valley of the Cardener and the town of Cardona.",
  "external_url": "https://example.com/?token_id=1",
  "image": "https://bafybeigpwa6i7a4cuhwlcxvu6kjku2qneoxxvvkqefx3govuogmwkndavi.ipfs.nftstorage.link/images/cardona-castle.jpeg",
  "name": "Cardona Castle"
}
```

## TODO

Update React app to compare user's longitude and latitude w/ the coords of one of the NFTs and if a user is near that location then they get the token.

## Open Questions

- How to gamify this?
- Is there only 1 token per location?
- How can we prevent people from spoofing their location and cheating?
