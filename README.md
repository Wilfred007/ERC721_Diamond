Here’s a refactored version of the README with updated URLs.

---

# DiamondNFT: Faceted Presale and Merkle Distribution

## Overview

DiamondNFT is an advanced Ethereum-based NFT project that employs the Diamond pattern for modular, upgradeable smart contracts. The project integrates ERC721 functionality, a presale mechanism, and a gas-optimized Merkle tree-based token distribution.

## Features

- **Diamond Pattern Architecture**: Enables modular, upgradeable contract structure using facets.
- **ERC721 Standard Compliance**: Fully compatible with the ERC721 standard for NFTs.
- **Configurable Presale Mechanism**: Supports a presale period with customizable pricing and purchase limits.
- **Efficient Merkle Distribution**: Implements a Merkle tree-based system for gas-optimized token claims.
- **Seamless Foundry Integration**: Includes Foundry tests for contract verification and deployment.

## Project Structure

```plaintext
DiamondNFT/
├── src/
│   ├── Diamond.sol
│   ├── facets/
│   │   ├── ERC721Facet.sol
│   │   ├── MerkleFacet.sol
│   │   └── PresaleFacet.sol
├── test/
│   └── DiamondNFT.t.sol
├── script/
│   └── DeployDiamondNFT.s.sol
├── lib/
├── merkle/
│   ├── generateMerkleTree.ts
│   └── whitelistAddresses.json
├── foundry.toml
└── README.md
```

## Prerequisites

- [Foundry](https://book.getfoundry.sh/getting-started/installation.html)
- [Node.js](https://nodejs.org/) (for generating Merkle trees)
- [Yarn](https://yarnpkg.com/) or [npm](https://www.npmjs.com/)

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/YourUsername/DiamondNFT.git
   cd DiamondNFT
   ```

2. **Install Foundry dependencies:**

   ```bash
   forge install
   ```

3. **Install Node.js dependencies:**

   ```bash
   yarn install
   ```

   or

   ```bash
   npm install
   ```

4. **Generate the Merkle tree:**

   ```bash
   ts-node merkle/generateMerkleTree.ts
   ```

## Compilation

Compile the smart contracts using Foundry:

```bash
forge build
```

## Testing

Run the Foundry tests:

```bash
forge test
```

## Deployment

1. **Set up environment variables:**

   ```bash
   cp .env.example .env
   ```

   Edit `.env` and configure your private key and RPC URL.

2. **Deploy the smart contracts:**

   ```bash
   forge script script/DeployDiamondNFT.s.sol:DeployDiamondNFT --rpc-url $RPC_URL --broadcast --verify -vvvv
   ```

## Usage

### Presale

Participants can buy NFTs during the presale by calling the `buyPresale` function in the `PresaleFacet`. The default presale price is 1 ETH for 30 NFTs, with a minimum purchase amount of 0.01 ETH.

### Merkle Distribution

Whitelisted users can claim their NFTs by providing a valid Merkle proof to the `claim` function in the `MerkleFacet`.

### ERC721 Functionality

All standard ERC721 functions, such as token transfers, approvals, and balance inquiries, are accessible via the `ERC721Facet`.

## Upgradeability

With the Diamond pattern, the contract can be easily upgraded. New facets can be added, or existing facets can be replaced without redeploying the entire contract.

## Security Considerations

- Restrict access to functions that set the Merkle root and presale parameters.
- Carefully manage the whitelist for the Merkle distribution.
- Consider using a multisig wallet for critical operations.

## Contributing

Contributions are encouraged! Please fork the repository, make your changes, and create a pull request.

## License

This project is licensed under the MIT License.

## Disclaimer

This software is provided as-is and should undergo a thorough security audit before production use. The authors are not liable for any losses resulting from using this software.

# ERC721_Diamond
