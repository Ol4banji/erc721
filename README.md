# R - NFT Minting Smart Contract

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

## Overview

The `R` Solidity smart contract allows users to mint NFTs (Non-Fungible Tokens) with specific functionality and characteristics.

- **Token Standard**: ERC-721
- **Inherits**: ERC721Enumerable, Ownable
- **Symbol**: [R]
- **Total Supply**: 3333
- **Max Mint Amount**: 5
- **Minting Cost**: 0.002 ETH per token

## Contract Details

### State Variables

- `baseURI`: Base URI for token metadata.
- `baseExtension`: File extension for token metadata.
- `cost`: Cost to mint a token.
- `maxSupply`: Maximum total supply of tokens.
- `maxMintAmount`: Maximum number of tokens that can be minted at once per wallet.
- `paused`: Flag to pause/unpause minting.
- `revealed`: Flag indicating if tokens are revealed.

### Constructor

- `constructor`: Initializes the contract with a name, symbol, and base URI.

### Internal Functions

- `_baseURI()`: Internal function to get the base URI for token metadata.

### Public Functions

- `mint(uint256 _mintAmount)`: Mint NFTs, allowing users to mint a specified quantity of tokens.
- `walletOfOwner(address _owner)`: Get an array of token IDs owned by a specific address.
- `tokenURI(uint256 tokenId)`: Get the URI for a specific token.
- `reveal()`: Reveals the tokens.
- `setCost(uint256 _newCost)`: Set a new minting cost (Owner-only).
- `setMaxMintAmount(uint256 _newMaxMintAmount)`: Set a new maximum mint amount (Owner-only).
- `setBaseURI(string memory _newBaseURI)`: Set a new base URI for token metadata (Owner-only).
- `setBaseExtension(string memory _newBaseExtension)`: Set a new file extension for token metadata (Owner-only).
- `withdraw()`: Withdraw funds, paying 5% to another address and 95% to the contract owner (Owner-only).

## Usage

- Deploy this contract to the Ethereum network.
- Call the `mint` function to mint NFTs.
- Adjust contract parameters using owner-only functions as needed.
- Reveal the tokens when ready using the `reveal` function.

## Ownership

The contract owner has the ability to manage contract parameters, pause minting, and withdraw funds.

**Note**: This is a simplified overview of the contract. Detailed documentation and testing should be conducted before deployment.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

