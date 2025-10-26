# 🏦 IntelliVault: Decentralized RWA Trading Platform

> ETHOnline 2025 - AI-Powered Tokenized Real-World Assets Trading Hub

[![Solidity](https://img.shields.io/badge/Solidity-0.8.28-blue.svg)](https://docs.soliditylang.org/)
[![Hardhat](https://img.shields.io/badge/Hardhat-2.22-yellow.svg)](https://hardhat.org/)
[![React](https://img.shields.io/badge/React-19.0-blue.svg)](https://react.dev/)
[![LangChain](https://img.shields.io/badge/LangChain-0.3-green.svg)](https://js.langchain.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-blue.svg)](https://www.typescriptlang.org/)

Built with **Blockscout MCP**, **Hardhat**, and **PayPal USD (PYUSD)** for ETHOnline 2025

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Sponsor Integration](#sponsor-integration)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Smart Contracts](#smart-contracts)
- [AI Agent System](#ai-agent-system)
- [Frontend Application](#frontend-application)
- [Live Demo](#live-demo)

---

## 🎯 Overview

IntelliVault is a comprehensive DeFi platform that bridges traditional finance with blockchain technology by enabling secure trading of **tokenized real-world assets (RWAs)** such as stocks and bonds. The platform leverages **PayPal USD (PYUSD)** as a stable settlement currency and integrates **Blockscout's Model Context Protocol (MCP)** to provide unparalleled cross-chain transparency and security.

**Mission**: Create a secure, transparent, and efficient marketplace for real-world assets on the blockchain, combining traditional finance stability with DeFi innovation.

**ETHOnline 2025 Project** featuring:
- Smart contracts deployed on **Sepolia Testnet**
- Dual AI agent system for trading & blockchain intelligence
- Multi-chain portfolio analytics via **Blockscout MCP**
- **PYUSD** stablecoin integration for all transactions

---

## ✨ Key Features

### 🔒 **Tokenized RWA Trading**
A secure on-chain vault enabling users to buy and sell ERC-20 tokens representing real-world stocks (Tesla, Google, Microsoft).

- **Buy & Sell**: Trade RWA tokens with PYUSD
- **Instant Settlement**: On-chain transactions settle immediately
- **MetaMask Integration**: One-click transaction execution
- **Real-time Pricing**: Live token prices from vault contract

### 💰 **PayPal USD (PYUSD) Integration**
All trades, settlements, and liquidity provisions use PYUSD as the stable medium of exchange.

- **Stablecoin Settlement**: All transactions in PYUSD
- **Vault Liquidity**: PYUSD-backed liquidity pool
- **Portfolio Tracking**: View balances in stable USD terms
- **Low Volatility**: Avoid crypto price fluctuations

### 📊 **Multi-Chain Portfolio Dashboard**
Powered by **Blockscout MCP SDK**, providing comprehensive asset views across multiple blockchain networks.

- **5+ Chain Support**: Ethereum, Sepolia, Base, Optimism, Arbitrum
- **Cross-Chain Holdings**: View tokens across all networks
- **Transaction History**: Complete transaction logs per chain
- **Gas Analytics**: Track gas spending across chains

### 🤖 **Dual AI Agent System**
Intelligent agents powered by **Gemini 2.0 Flash** and **LangChain**.

**Query Mode (Blockscout MCP):**
- Smart contract security analysis
- Multi-chain transaction tracking
- Token holdings aggregation
- Address reputation scoring

**Agent Mode (Trading):**
- Natural language trading commands
- Price calculations and queries
- Automated MetaMask transactions
- Buy/sell cost estimation

### 🔍 **Address Intelligence & Security**
AI-powered address analysis for enhanced security and transparency.

- **Pre-Onboarding Check**: Analyze wallet history before connection
- **Risk Assessment**: Identify suspicious activity patterns
- **Cross-Chain Reputation**: View address activity across all chains
- **Public Lookup**: Anyone can verify any address
- **Contract Analysis**: Security audit before interactions

### 📈 **Real-Time Asset Analytics**
Live metrics and insights for all tokenized assets.

- **Trading Volume**: 24h volume tracking
- **Holder Distribution**: Token holder statistics
- **Price History**: Historical price data
- **Market Cap**: Real-time market capitalization

---

## 🏆 Sponsor Integration

### Blockscout MCP Server
**Role**: Multi-chain blockchain data provider

- **Query Mode Integration**: Provides cross-chain analytics via MCP protocol
- **Address Intelligence**: Powers AI agent for security analysis
- **Multi-Chain Data**: Real-time data from 5+ blockchain networks
- **Contract Verification**: Smart contract security checking

**Impact**: Enables transparent, verifiable on-chain data for all platform features.

### Hardhat
**Role**: Smart contract development framework

- **Vault Contract**: Core trading logic and PYUSD integration
- **RWA Tokens**: Tokenized asset contract templates (Tesla, Google, Microsoft)
- **Testing Suite**: Comprehensive contract testing
- **Deployment Scripts**: Automated deployment to Sepolia testnet

**Impact**: Robust, tested smart contracts powering the trading platform.

### PayPal USD (PYUSD)
**Role**: Stablecoin settlement currency

- **Contract Address**: `0xCaC524BcA292aaade2DF8A05cC58F0a65B1B3bB9` (Sepolia)
- **Settlement Layer**: All buy/sell transactions use PYUSD
- **Vault Liquidity**: PYUSD backing for all tokenized assets
- **Price Stability**: Eliminates crypto volatility for RWA trading

**Impact**: Provides stable, reliable settlement for real-world asset trading.

---

## 🏗️ Architecture

IntelliVault uses a modular, multi-layered architecture separating frontend, AI agents, and on-chain logic.

```
┌─────────────────────────────────────────────────────────────┐
│                    Frontend (React)                          │
│              Port: 5173 (Vite Dev Server)                    │
│                                                              │
│  • Wallet Connection (Reown AppKit)                         │
│  • Portfolio Dashboard                                       │
│  • AI Chat Interface (Query + Agent Modes)                  │
│  • MetaMask Transaction Execution                           │
└─────────────────────────────────────────────────────────────┘
                            │
        ┌───────────────────┴───────────────────┐
        │                                       │
        ▼                                       ▼
┌──────────────────┐                  ┌──────────────────┐
│  Query Mode      │                  │  Agent Mode      │
│  (Port 3000)     │                  │  (Port 3002)     │
│                  │                  │                  │
│ Blockscout MCP   │                  │ Trading Agent    │
│ • HTTP Server    │                  │ • WebSocket      │
│ • Gemini 2.0     │                  │ • LangChain      │
│ • Multi-chain    │                  │ • Gemini 2.0     │
└──────────────────┘                  └──────────────────┘
        │                                       │
        ▼                                       ▼
┌──────────────────┐                  ┌──────────────────┐
│ Docker MCP       │                  │ Ethers.js        │
│ Client           │                  │ Provider         │
│                  │                  │                  │
│ • Blockscout API │                  │ • Vault Contract │
│ • 5 Chains       │                  │ • PYUSD Token    │
└──────────────────┘                  └──────────────────┘
        │                                       │
        ▼                                       ▼
┌──────────────────────────────────────────────────────────┐
│              Sepolia Testnet (Chain ID: 11155111)        │
│                                                          │
│  • Vault Contract: 0xB6C58FDB4BBffeD7B7224634AB932518... │
│  • PYUSD Token: 0xCaC524BcA292aaade2DF8A05cC58F0a65B1... │
│  • RWA Tokens: TSLA, GOOGL, MSFT                        │
└──────────────────────────────────────────────────────────┘
```

### Architecture Layers

1. **Frontend (React + TypeScript)**
   - User-facing application with wallet integration
   - Portfolio dashboard showing multi-chain holdings
   - AI chat interface for trading and analysis
   - Real-time WebSocket communication

2. **AI Agent System (Node.js + LangChain)**
   - **Query Mode**: Multi-chain blockchain analysis via Blockscout MCP
   - **Agent Mode**: Trading operations and MetaMask integration
   - Both powered by Gemini 2.0 Flash LLM

3. **Smart Contracts (Solidity)**
   - `Vault.sol`: Core trading logic with PYUSD integration
   - `TokenizedAsset.sol`: ERC-20 token template for RWAs
   - Deployed on Sepolia testnet with Hardhat

4. **Data Layer (Blockscout MCP)**
   - Cross-chain blockchain data
   - Transaction history and token holdings
   - Smart contract verification

---

## 🛠️ Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Frontend** | React 19.0, TypeScript 5.7, Vite 6.0, Tailwind CSS 4.0, Wagmi 2.15, Reown AppKit 1.6, Ethers.js 6.13 |
| **AI Agents** | Node.js 18+, LangChain 0.3, Gemini 2.0 Flash, Socket.IO 4.8, Express.js |
| **Smart Contracts** | Solidity 0.8.28, Hardhat 2.22, OpenZeppelin Contracts 5.1 |
| **Blockchain** | Sepolia Testnet (11155111) |
| **Data & Analytics** | Blockscout MCP SDK, Model Context Protocol |
| **Settlement** | PayPal USD (PYUSD) |

---

## 📁 Project Structure

```
IntelliVault-contract/
├── contracts/                 # Smart contracts (Hardhat project)
│   ├── contracts/
│   │   ├── Vault.sol         # Main vault contract
│   │   ├── RWAToken.sol      # Tokenized asset template
│   │   └── interfaces/       # Contract interfaces
│   ├── scripts/
│   │   └── deploy.js         # Deployment scripts
│   ├── test/
│   │   └── Vault.test.js     # Contract tests
│   ├── hardhat.config.js     # Hardhat configuration
│   └── README.md             # Contract documentation
│
├── agent/                     # AI agent system
│   ├── src/
│   │   ├── intelligent-chatbot-server.ts    # Query Mode (MCP)
│   │   ├── intelligent-agent.ts             # MCP Agent logic
│   │   ├── vault-ai-websocket-server.ts     # Agent Mode (WebSocket)
│   │   ├── vault-ai-agent.ts                # Trading agent logic
│   │   ├── docker-mcp-client.ts             # Blockscout MCP client
│   │   └── vault-tokens.json                # Supported tokens
│   ├── package.json
│   └── README.md             # Agent documentation
│
├── .gitignore
├── package.json              # Root package.json
└── README.md                 # This file

IntelliVault-frontend/
├── src/
│   ├── components/       # UI components
│   ├── pages/
│   │   ├── Index.tsx     # Landing page
│   │   ├── Chat.tsx      # AI chat interface
│   │   ├── User.tsx      # Portfolio dashboard
│   │   └── Vault.tsx     # Vault analytics
│   ├── services/
│   │   └── aiAgentService.ts  # WebSocket client
│   ├── lib/
│   │   ├── contracts.ts  # Contract ABIs
│   │   └── readers.ts    # Blockchain readers
│   └── config/
│       └── constants.ts  # Contract addresses
├── package.json
└── README.md             # Frontend documentation

```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** >= 18.0.0
- **npm** >= 9.0.0
- **Docker** (for Query Mode)
- **MetaMask** wallet extension
- **Gemini API Key** from [Google AI Studio](https://makersuite.google.com/app/apikey)

### Installation

1. **Clone Repository**

```bash
git clone <repository-url>
cd IntelliVault
```

2. **Install Dependencies**

```bash
# Install all workspace dependencies
npm install

# Or install individually
cd contracts && npm install
cd ../agent && npm install
cd ../frontend && npm install
```

3. **Configure Environment Variables**

**Agent (`.env` in `agent/` directory):**
```env
GEMINI_API_KEY=your_gemini_api_key_here
API_PORT=3000
VAULT_PORT=3002
NODE_ENV=development
LOG_LEVEL=info
```

**Frontend (`.env` in `frontend/` directory):**
```env
VITE_VAULT_ADDRESS=0xB6C58FDB4BBffeD7B7224634AB932518a29e4C4b
VITE_PYUSD_ADDRESS=0xCaC524BcA292aaade2DF8A05cC58F0a65B1B3bB9
VITE_RPC_URL=https://0xrpc.io/sep
VITE_STOCK_TOKENS=0x09572cED4772527f28c6Ea8E62B08C973fc47671,0xC411824F1695feeC0f9b8C3d4810c2FD1AB1000a,0x98e565A1d46d4018E46052C936322479431CA883
VITE_WALLET_CONNECT_PROJECT_ID=your_walletconnect_project_id
```

**Contracts (`.env` in `contracts/` directory):**
```env
SEPOLIA_RPC_URL=https://0xrpc.io/sep
PRIVATE_KEY=your_private_key_here
ETHERSCAN_API_KEY=your_etherscan_api_key
```

### Running the Platform

**Terminal 1 - Query Mode (Blockscout MCP):**
```bash
cd agent
npm run dev
# Runs on port 3000
```

**Terminal 2 - Agent Mode (Trading):**
```bash
cd agent
npm run dev:ai
# Runs on port 3002
```

**Terminal 3 - Frontend:**
```bash
cd frontend
npm run dev
# Runs on port 5173
```

**Access Application:**
Open `http://localhost:5173` in your browser

---

## 📜 Smart Contracts

### Deployed Contracts (Sepolia Testnet)

| Contract | Address | Purpose |
|----------|---------|---------|
| **Vault** | `0xB6C58FDB4BBffeD7B7224634AB932518a29e4C4b` | Main trading vault |
| **PYUSD** | `0xCaC524BcA292aaade2DF8A05cC58F0a65B1B3bB9` | Settlement token |
| **Tesla Token** | `0x09572cED4772527f28c6Ea8E62B08C973fc47671` | RWA token |
| **Google Token** | `0xC411824F1695feeC0f9b8C3d4810c2FD1AB1000a` | RWA token |
| **Microsoft Token** | `0x98e565A1d46d4018E46052C936322479431CA883` | RWA token |

### Vault Contract Features

```solidity
// Buy RWA tokens with PYUSD
function buyStock(address _token, uint256 _amountInWholeTokens) external;

// Sell RWA tokens for PYUSD
function sellStock(address _token, uint256 _amountInWholeTokens) external;

// Get current token price
function getPrice(address _token) external view returns (uint256);

// View stock information
function stockList(address _token) external view returns (
    string memory name,
    uint256 pricingFactor,
    uint256 currentSupply,
    bool isSupported
);
```

### Development & Testing

```bash
cd contracts

# Compile contracts
npx hardhat compile

# Run tests
npx hardhat test

# Deploy to Sepolia
npx hardhat run scripts/deploy.js --network sepolia

# Verify on Etherscan
npx hardhat verify --network sepolia DEPLOYED_CONTRACT_ADDRESS
```

**Full documentation:** See `contracts/README.md`

---

## 🤖 AI Agent System

### Query Mode - Blockscout MCP Agent

**Port**: 3000  
**Technology**: Model Context Protocol + Blockscout + Gemini 2.0 Flash

**Capabilities:**
- Multi-chain smart contract analysis (5 chains)
- Transaction history tracking
- Token holdings aggregation
- Gas spend calculations
- Address reputation scoring

**Example Usage:**
```bash
curl -X POST http://localhost:3000/chat \
  -H "Content-Type: application/json" \
  -d '{
    "message": "Analyze contract 0xB6C5... on Sepolia"
  }'
```

### Agent Mode - Vault Trading Agent

**Port**: 3002  
**Technology**: LangChain + WebSocket + Gemini 2.0 Flash

**Capabilities:**
- Real-time token price queries
- Buy/sell cost calculations
- MetaMask transaction preparation
- Natural language trading commands

**Example Usage:**
```javascript
import { io } from 'socket.io-client';

const socket = io('http://localhost:3002');

socket.emit('chat_message', { 
  message: 'Buy 5 Tesla tokens' 
});

socket.on('chat_response', (response) => {
  console.log(response.data.response);
});
```

**Full documentation:** See `agent/README.md`

---

## 🎨 Frontend Application

### Key Pages

**Landing Page (`/`)**
- Platform overview
- Feature highlights
- Sponsor showcase
- Call-to-action

**Chat Interface (`/chat`)**
- Dual AI agent modes (Query + Agent)
- Real-time WebSocket communication
- Quick action buttons
- Message history

**User Dashboard (`/user`)**
- Portfolio value and holdings
- PYUSD balance
- Reputation score
- Risk assessment

**Vault Analytics (`/vault`)**
- Total Value Locked (TVL)
- PYUSD liquidity
- Active assets
- Token performance table

### Technologies

- **React 19.0** with TypeScript
- **Vite 6.0** for fast development
- **Tailwind CSS 4.0** for styling
- **Wagmi 2.15** for Web3 hooks
- **Reown AppKit 1.6** for wallet connection
- **Ethers.js 6.13** for blockchain interactions

**Full documentation:** See `frontend/README.md`

---

## 🌐 Live Demo

**Demo URL**: https://vimeo.com/manage/videos/1130662499

### Test Account Setup

1. **Get Sepolia ETH**: https://sepoliafaucet.com/
2. **Get PYUSD**: Contact team for testnet PYUSD
3. **Connect MetaMask**: Add Sepolia network
4. **Start Trading**: Buy/sell RWA tokens with PYUSD

---

## 🧪 Testing Guide

### Smart Contract Tests

```bash
cd contracts
npx hardhat test
```

### Agent System Tests

```bash
cd agent

# Test Query Mode
curl http://localhost:3000/health

# Test Agent Mode  
curl http://localhost:3002/health
```

### Frontend Tests

```bash
cd frontend

# Manual testing checklist in frontend/README.md
npm run dev
```

---

## 🐛 Troubleshooting

### Common Issues

**Query Mode Not Working**
- Ensure Docker is running
- Check port 3000 is available
- Verify Gemini API key

**Agent Mode Connection Failed**
- Check port 3002 is available
- Verify WebSocket connection
- Check Gemini API key

**MetaMask Transactions Failing**
- Ensure on Sepolia network (Chain ID: 11155111)
- Check PYUSD balance
- Verify contract addresses

**Portfolio Not Loading**
- Check wallet is connected
- Verify RPC URL in .env
- Check contract addresses

**Detailed troubleshooting:** See individual README files in each directory.

---

## 📚 Documentation

- **Main README** (this file) - Project overview
- **Contracts README** - Smart contract details (`contracts/README.md`)
- **Agent README** - AI agent system (`agent/README.md`)
- **Frontend README** - Frontend application (`frontend/README.md`)

---

## 🏆 ETHOnline 2025

### Bounty Categories

✅ **Blockscout** - Multi-chain blockchain analytics via MCP  
✅ **Hardhat** - Smart contract development and testing  
✅ **PayPal USD** - PYUSD stablecoin integration  

### Key Innovations

1. **Dual AI Agent Architecture** - Separate agents for trading and analysis
2. **PYUSD Settlement** - Stablecoin-backed RWA trading
3. **Multi-Chain Intelligence** - Cross-chain portfolio and reputation
4. **Natural Language Trading** - Buy/sell with conversational AI
5. **Address Security** - Pre-onboarding reputation checks

---

## 🙏 Acknowledgments

- **Blockscout** - Multi-chain blockchain data and MCP infrastructure
- **Hardhat** - Robust smart contract development framework
- **PayPal USD** - Stable settlement layer for RWA trading
- **Google Gemini** - Powerful LLM capabilities
- **LangChain** - AI agent orchestration framework
- **OpenZeppelin** - Secure smart contract libraries
- **ETHOnline 2025** - For the opportunity to innovate and build

---

## 📄 License

MIT License - See LICENSE file for details

---


**Built with ❤️ for ETHOnline 2025**

*Bringing Real-World Assets to DeFi with AI-Powered Intelligence*
