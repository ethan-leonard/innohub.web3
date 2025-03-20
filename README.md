# InnoHub.Web3

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Solidity](https://img.shields.io/badge/solidity-^0.8.0-blue.svg)
![React](https://img.shields.io/badge/react-18.0+-61DAFB.svg)
![Ethereum](https://img.shields.io/badge/ethereum-powered-3C3C3D.svg)

## Overview

InnoHub.Web3 is a decentralized application that combines event token staking with NFT minting capabilities. The platform encourages event attendance through a stake-to-attend model while rewarding participants with exclusive NFTs that provide additional benefits.

### Key Features

- **Event Staking System**: Users stake tokens to reserve spots at events, receiving their tokens back (plus potential rewards) upon attendance
- **NFT Marketplace**: Mint, view, and trade unique digital collectibles
- **Integrated Ecosystem**: Use staked tokens or rewards to purchase exclusive NFTs
- **User-Friendly Interface**: Seamless experience for both crypto-savvy users and newcomers

## Architecture

InnoHub.Web3 follows a modern web3 architecture with these components:

### Smart Contracts (Solidity)

- Event staking contract with attendance verification
- ERC-721 compliant NFT implementation
- Token reward management system
- Integration between staking and NFT ecosystems

### Frontend (React.js)

- Intuitive interface for discovering and staking for events
- NFT gallery to view owned and available collectibles
- Wallet connection and management
- Transaction status monitoring

## Project Structure

```plaintext
innohub.web3/
├── contracts/                 # Solidity smart contracts
│   ├── EventStaking.sol       # Event staking implementation
│   ├── InnoHubNFT.sol         # NFT contract implementation
│   ├── RewardDistributor.sol  # Token reward management
│   └── interfaces/            # Contract interfaces
│
├── frontend/                  # React.js frontend
│   ├── public/                # Static assets
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   ├── pages/             # Application pages
│   │   ├── hooks/             # Custom React hooks
│   │   ├── context/           # React context providers
│   │   ├── utils/             # Utility functions
│   │   ├── services/          # API and contract interaction
│   │   ├── App.js             # Main application component
│   │   └── index.js           # Entry point
│   ├── package.json           # Node.js dependencies
│   └── .env                   # Environment variables (gitignored)
│
├── test/                      # Smart contract tests
│   ├── EventStaking.test.js   # Tests for staking contract
│   └── InnoHubNFT.test.js     # Tests for NFT contract
│
├── scripts/                   # Deployment scripts
│   ├── deploy.js              # Main deployment script
│   └── verify.js              # Contract verification script
│
├── hardhat.config.js          # Hardhat configuration
├── .gitignore                 # Git ignore file
├── LICENSE                    # MIT License
└── README.md                  # Project documentation
```

## Getting Started

### Prerequisites

- Node.js 16+
- MetaMask or other Web3 wallet
- Hardhat (for contract development)
- Test ETH on a testnet (Sepolia or Goerli recommended)

### Smart Contract Development

```bash
# Clone the repository
git clone https://github.com/ethan-leonard/innohub.web3.git
cd innohub.web3

# Install dependencies
npm install

# Compile smart contracts
npx hardhat compile

# Run tests
npx hardhat test

# Deploy to local network
npx hardhat node
npx hardhat run scripts/deploy.js --network localhost

# Deploy to testnet
npx hardhat run scripts/deploy.js --network sepolia
```

### Frontend Development

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Start development server
npm start
```

## Smart Contract Architecture

### EventStaking.sol

The EventStaking contract manages the token staking process for events:

- Users stake a predetermined amount of tokens to reserve spots at events
- Event organizers can set various parameters like stake amount and capacity
- Attendees receive their stake back, plus potential rewards, after verification
- No-shows forfeit their stake, which is redistributed or used for platform development

### InnoHubNFT.sol

The NFT contract implements ERC-721 standard with additional features:

- Minting of unique digital collectibles with metadata
- Integration with the staking system for token-based purchases
- Special properties for NFTs that represent event attendance or achievement
- Optional royalty mechanisms for creators

## Usage Scenarios

### For Event Organizers

1. Create a new event by setting parameters (name, date, location, stake amount)
2. Monitor registrations and manage event capacity
3. Verify attendance using QR codes or other verification methods
4. Distribute rewards to attendees (optional)

### For Attendees

1. Browse available events in the platform
2. Stake tokens to secure a spot at desired events
3. Attend events and get stake back plus potential rewards
4. Use earned tokens to purchase exclusive NFTs

### For Collectors

1. Browse available NFTs in the marketplace
2. Purchase NFTs using staked tokens or other crypto
3. View owned NFTs in personal gallery
4. Trade or transfer NFTs through the platform

## Technologies Used

### Smart Contract Development
- Solidity (Contract language)
- Hardhat (Development environment)
- OpenZeppelin (Contract libraries)
- Ethers.js (Blockchain interaction)

### Frontend
- React.js (UI library)
- Web3.js/Ethers.js (Blockchain interaction)
- MetaMask integration (Wallet connection)
- IPFS (NFT metadata storage)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Commit Message Guidelines

We follow a simple commit message format to make the project history readable. Each commit message should be structured as follows:

`<emoji> <type>: <subject>`

### Types and Emojis

| Emoji | Type | Description |
|-------|------|-------------|
| ✨ | `feat` | New feature or enhancement |
| 🐛 | `fix` | Bug fix |
| 📝 | `docs` | Documentation changes |
| 💄 | `style` | Code formatting, styling (no code change) |

### Examples

- ✨ feat: add SQL injection pattern detection
- 🐛 fix: resolve false positive in XSS detection
- 📝 docs: update installation instructions
- 💄 style: format code according to style guide

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

Project Link: [https://github.com/ethan-leonard/innohub.web3](https://github.com/ethan-leonard/innohub.web3)

---

**Note**: This project is currently under development. Features and capabilities are subject to change.