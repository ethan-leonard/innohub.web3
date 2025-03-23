# InnoHub.Web3

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Solidity](https://img.shields.io/badge/solidity-^0.8.0-blue.svg)
![React](https://img.shields.io/badge/react-18.0+-61DAFB.svg)
![TypeScript](https://img.shields.io/badge/typescript-4.9+-blue.svg)
![Ethereum](https://img.shields.io/badge/ethereum-powered-3C3C3D.svg)
![Polygon](https://img.shields.io/badge/polygon-ready-8247E5.svg)

## Overview

InnoHub.Web3 is a decentralized application that implements a closed-loop token ecosystem for event management and exclusive NFT rewards. The platform uses a custom ERC-20 token (ClubToken) for event registration through staking, with attendance verification unlocking token refunds and the ability to acquire exclusive NFTs.

### Key Features

- **Closed-Loop Token System**: Custom ERC-20 token with controlled distribution and transfer mechanisms
- **Event Staking System**: Users stake tokens to reserve spots at events, receiving tokens back upon attendance verification
- **Exclusive NFT Marketplace**: Redeem tokens for unique NFTs with IPFS-stored metadata
- **User-Friendly Interface**: Intuitive UI for event discovery, token management, and NFT redemption

### Progress

| Phase | Status | Progress |
|-------|--------|----------|
| Planning | 🔄 In Progress | 50% |
| Smart Contract Development | 🔜 Not Started | 0% |
| Frontend Development | 🔜 Not Started | 0% |
| Testing | 🔜 Not Started | 0% |
| Deployment | 🔜 Not Started | 0% |

**Overall Progress**: `[🟩⬜⬜⬜⬜⬜⬜⬜⬜⬜]` 10%

## Architecture

InnoHub.Web3 follows a modern web3 architecture optimized for the Polygon PoS chain:

### Smart Contracts (Solidity)

- **ClubToken (ERC-20)**: Non-transferable token with owner-controlled distribution
- **EventStaking Contract**: Manages event registrations and attendance verification
- **NFT Redemption System**: ERC-721 implementation with token-based redemption mechanics

### Frontend (React + TypeScript)

- Wallet integration (MetaMask/WalletConnect)
- Dynamic event display with countdown timers and staking status
- NFT gallery with ownership tracking and redemption interface
- Transaction history and notification system

## Project Structure

```plaintext
innohub.web3/
├── contracts/                 # Solidity smart contracts
│   ├── ClubToken.sol          # Custom ERC-20 implementation
│   ├── EventStaking.sol       # Event staking implementation
│   ├── ClubNFT.sol            # NFT redemption contract
│   └── interfaces/            # Contract interfaces
│
├── frontend/                  # React TypeScript frontend
│   ├── public/                # Static assets
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   │   ├── EventCard/     # Event display component
│   │   │   ├── NFTGallery/    # NFT display and redemption
│   │   │   ├── WalletConnect/ # Wallet integration component
│   │   │   └── ProgressBar/   # Animated progress indicators
│   │   ├── pages/             # Application pages
│   │   ├── hooks/             # Custom React hooks
│   │   ├── context/           # React context providers
│   │   ├── utils/             # Utility functions
│   │   ├── services/          # API and contract interaction
│   │   ├── types/             # TypeScript type definitions
│   │   ├── App.tsx            # Main application component
│   │   └── index.tsx          # Entry point
│   ├── package.json           # Node.js dependencies
│   ├── tsconfig.json          # TypeScript configuration
│   └── .env                   # Environment variables (gitignored)
│
├── test/                      # Smart contract tests
│   ├── ClubToken.test.ts      # Tests for ERC-20 token
│   ├── EventStaking.test.ts   # Tests for staking contract
│   └── ClubNFT.test.ts        # Tests for NFT contract
│
├── scripts/                   # Deployment scripts
│   ├── deploy.ts              # Main deployment script
│   └── verify.ts              # Contract verification script
│
├── hardhat.config.ts          # Hardhat configuration
├── .gitignore                 # Git ignore file
├── LICENSE                    # MIT License
└── README.md                  # Project documentation
```

## Technical Requirements

### ClubToken (ERC-20)
- Name: "ClubToken", Symbol: "CLUB"
- Non-transferable except for owner-initiated distributions
- Disabled approval system to prevent DEX listings
- Mintable only by contract owner
- Initial supply: 1,000,000 tokens (18 decimals)
- Built with OpenZeppelin libraries for security

### EventStaking Contract
- Accepts ClubToken for event registration
- Stores stakes per event ID with:
  - Minimum stake amount
  - Event timeframe (start/end dates)
  - Attendance verification flag
- Auto-refund mechanism post-event verification
- Reentrancy protection for all external calls

### NFT Redemption Contract (ERC-721)
- Mint exclusive NFTs using ClubToken
- Price: 100 tokens per NFT
- Metadata storage on IPFS
- Royalty system (5% to contract owner)
- Configurable supply limits

## Getting Started

### Prerequisites

- Node.js 16+
- MetaMask or WalletConnect-compatible wallet
- Hardhat (for contract development)
- Test MATIC on Mumbai testnet (recommended)

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
npx hardhat run scripts/deploy.ts --network localhost

# Deploy to testnet
npx hardhat run scripts/deploy.ts --network mumbai
```

### Frontend Development

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Start development server
npm start

# Type checking
npm run type-check

# Build for production
npm run build
```

## Smart Contract Implementation

### ClubToken.sol

The ClubToken contract is a custom ERC-20 implementation with:

- Restricted transfer functions that only allow the contract owner to initiate transfers
- Disabled approval mechanisms to prevent DEX listings or unauthorized transfers
- Minting capabilities restricted to the contract owner
- Initial supply of 1,000,000 tokens with 18 decimals
- Complete NatSpec documentation for all functions

### EventStaking.sol

The EventStaking contract manages token staking for events:

- Admins can create events with customizable parameters
- Users can stake tokens to register for events
- Attendance verification triggers token refunds
- Built-in safeguards against reentrancy attacks
- Gas-optimized data structures for efficient operations

### ClubNFT.sol

The NFT contract implements ERC-721 standard with additional features:

- Token redemption using ClubToken (100 tokens per NFT)
- IPFS integration for metadata storage
- 5% royalty mechanism for secondary sales
- Limited edition collections tied to specific events
- Owner-controlled minting parameters

## Frontend Features

### Wallet Integration
- Support for MetaMask and WalletConnect protocols
- Persistent connection state
- Network detection and switching
- Transaction signing and confirmation flows

### Event Interface
- Filterable event listings with search functionality
- Countdown timers to event start/end
- Staking interface with clear status indicators
- Attendance verification QR codes for event organizers

### NFT Gallery
- Visual display of owned NFTs with metadata
- Redemption interface with token balance tracking
- IPFS-powered image loading with fallback mechanisms
- NFT detail view with ownership history

### Enhanced Progress Bar
The application includes an animated progress bar component with:
- Smooth animations using CSS transitions
- Color-coded status indicators
- Loading states with shimmer effects
- Customizable themes to match the application's design system
- Support for different progress types (determinate, indeterminate)

## Implementation Guidelines

1. Start with ClubToken implementation, ensuring all transfer restrictions work correctly
2. Develop EventStaking contract with proper token integration and refund mechanisms
3. Build the NFT redemption system with IPFS metadata support
4. Implement frontend components with responsive design and wallet connectivity
5. Add comprehensive test coverage for all contract functionalities
6. Optimize contracts for deployment on Polygon PoS chain

## Technologies Used

### Smart Contract Development
- Solidity 0.8.x (Contract language)
- Hardhat (Development environment)
- OpenZeppelin (Contract libraries)
- Ethers.js (Blockchain interaction)
- IPFS (Metadata storage)

### Frontend
- React.js (UI library)
- TypeScript (Type-safe JavaScript)
- Ethers.js (Blockchain interaction)
- MetaMask/WalletConnect integration
- Framer Motion (Animation library)

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

- ✨ feat: implement ClubToken transfer restrictions
- 🐛 fix: resolve event staking refund mechanism
- 📝 docs: add NatSpec documentation to contracts
- 💄 style: improve animated progress bar

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

Project Link: [https://github.com/ethan-leonard/innohub.web3](https://github.com/ethan-leonard/innohub.web3)

---

**Note**: This project is currently under development. Features and capabilities are subject to change.