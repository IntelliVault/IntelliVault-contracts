# 🤖 IntelliVault AI Agent System

> ETHOnline 2025 - Dual AI Agent Architecture for Blockchain Intelligence & DeFi Trading

[![Gemini](https://img.shields.io/badge/LLM-Gemini%202.0%20Flash-blue.svg)](https://ai.google.dev/)
[![LangChain](https://img.shields.io/badge/LangChain-0.3-green.svg)](https://js.langchain.com/)
[![MCP](https://img.shields.io/badge/Protocol-Model%20Context%20Protocol-orange.svg)](https://modelcontextprotocol.io/)
[![Socket.IO](https://img.shields.io/badge/Socket.IO-4.8-purple.svg)](https://socket.io/)

Built with **Blockscout MCP**, **Hardhat**, and **PayPal USD (PYUSD)** for ETHOnline 2025

---

## 📋 Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Requirements](#requirements)
- [Installation](#installation)
- [Running the Agents](#running-the-agents)
- [Agent Capabilities](#agent-capabilities)
- [How It Works](#how-it-works)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)

---

## 🎯 Overview

IntelliVault implements a **dual AI agent system** combining blockchain intelligence and DeFi trading:

### 1. Query Mode - Blockscout MCP Agent (Port 3000)
- **Technology**: Model Context Protocol + Blockscout API
- **Purpose**: Multi-chain blockchain analysis
- **Features**: Smart contract analysis, transaction history, gas analytics, token holdings

### 2. Agent Mode - Vault Trading Agent (Port 3002)
- **Technology**: LangChain + WebSocket + Gemini 2.0 Flash
- **Purpose**: DeFi trading operations
- **Features**: Real-time pricing, buy/sell transactions, MetaMask integration

**Both agents use Gemini 2.0 Flash LLM** for intelligent natural language understanding and tool calling.

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────┐
│              Frontend (React + TypeScript)               │
│                     Port: 5173                           │
└──────────────────────────────────────────────────────────┘
                            │
        ┌───────────────────┴───────────────────┐
        │                                       │
        ▼                                       ▼
┌──────────────────┐                  ┌──────────────────┐
│  Query Mode      │                  │  Agent Mode      │
│  (Port 3000)     │                  │  (Port 3002)     │
│                  │                  │                  │
│ • HTTP Server    │                  │ • WebSocket      │
│ • Gemini 2.0     │                  │ • Gemini 2.0     │
│ • Tool Calling   │                  │ • LangChain      │
│ • MCP Protocol   │                  │ • Token Trading  │
└──────────────────┘                  └──────────────────┘
        │                                       │
        ▼                                       ▼
┌──────────────────┐                  ┌──────────────────┐
│ Docker MCP       │                  │ Ethers.js        │
│ Client           │                  │ Provider         │
│                  │                  │                  │
│ • Blockscout API │                  │ • Vault Contract │
│ • Multi-chain    │                  │ • PYUSD Token    │
│   (5 chains)     │                  │ • RWA Tokens     │
└──────────────────┘                  └──────────────────┘
        │                                       │
        ▼                                       ▼
┌──────────────────┐                  ┌──────────────────┐
│ Blockchain Data  │                  │ Sepolia Testnet  │
│ (Blockscout)     │                  │                  │
│                  │                  │ Vault: 0xB6C5... │
│ • Ethereum (1)   │                  │ PYUSD: 0xCaC5... │
│ • Sepolia (...)  │                  │ Tokens: 3        │
│ • Base (84532)   │                  │                  │
│ • Optimism (10)  │                  │                  │
│ • Arbitrum (...)│                  │                  │
└──────────────────┘                  └──────────────────┘
```

---

## 📦 Requirements

### System Requirements
- **Node.js**: >= 18.0.0
- **npm**: >= 9.0.0
- **Docker**: Latest version (for Query Mode)
- **RAM**: 4GB minimum
- **OS**: Windows, macOS, or Linux

### API Keys Required
- **Gemini API Key**: Get from [Google AI Studio](https://makersuite.google.com/app/apikey)

### Optional
- **MetaMask**: For executing transactions
- **Sepolia ETH + PYUSD**: For testing vault operations

---

## 🚀 Installation

### 1. Clone Repository

```bash
cd agent
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment

Create `.env` file:

```env
# API Keys (REQUIRED)
GEMINI_API_KEY=your_gemini_api_key_here

# Server Configuration
API_PORT=3000
VAULT_PORT=3002
NODE_ENV=development

# Logging
LOG_LEVEL=info
```

### 4. Start Docker (for Query Mode)

```bash
# Ensure Docker Desktop is running
docker ps
```

---

## ▶️ Running the Agents

### Query Mode - Blockscout MCP Agent

```bash
npm run dev
```

**Server Details:**
- **Port**: 3000
- **Protocol**: HTTP (POST /chat)
- **Technology**: MCP + Blockscout API + Gemini 2.0 Flash

**Health Check:**
```bash
curl http://localhost:3000/health
```

**Example Request:**
```bash
curl -X POST http://localhost:3000/chat \
  -H "Content-Type: application/json" \
  -d '{
    "message": "Analyze contract 0xB6C58FDB4BBffeD7B7224634AB932518a29e4C4b on Sepolia"
  }'
```

### Agent Mode - Vault Trading Agent

```bash
npm run dev:ai
```

**Server Details:**
- **Port**: 3002
- **Protocol**: WebSocket + HTTP
- **Technology**: LangChain + Socket.IO + Gemini 2.0 Flash

**Health Check:**
```bash
curl http://localhost:3002/health
```

**WebSocket Connection:**
```javascript
import { io } from 'socket.io-client';

const socket = io('http://localhost:3002');

socket.on('connect', () => {
  console.log('Connected to Vault AI Agent');
});

socket.emit('chat_message', { 
  message: 'What is the Tesla token price?' 
});

socket.on('chat_response', (response) => {
  console.log(response.data.response);
});
```

---

## 🎯 Agent Capabilities

### Query Mode - Blockscout MCP Agent

**Powered by**: Model Context Protocol + Blockscout

| Feature | Description | Supported Chains |
|---------|-------------|------------------|
| **Contract Analysis** | Security assessment, verification status | 5 chains |
| **Transaction History** | Gas analysis, pattern detection | 5 chains |
| **Token Holdings** | Cross-chain token balances | 5 chains |
| **Address Investigation** | Complete address profile | 5 chains |
| **Gas Analytics** | Total spend, efficiency analysis | 5 chains |

**Supported Blockchains:**
- Ethereum Mainnet (1)
- Sepolia Testnet (11155111)
- Base Sepolia (84532)
- Optimism (10)
- Arbitrum One (42161)

**Example Queries:**
```
- "Show transactions for 0x49f5... across all chains"
- "Analyze contract 0xB6C5... on Sepolia"
- "What tokens does 0x49f5... hold?"
- "Calculate total gas spent for 0x49f5..."
- "Which chain is most active for 0x49f5...?"
```

### Agent Mode - Vault Trading Agent

**Powered by**: LangChain + Gemini 2.0 Flash

| Feature | Description | Payment Method |
|---------|-------------|----------------|
| **Token Pricing** | Real-time prices from vault | PYUSD |
| **Buy Operations** | Calculate costs & prepare transactions | PYUSD |
| **Sell Operations** | Calculate returns & prepare transactions | PYUSD |
| **MetaMask Integration** | One-click transaction execution | PYUSD |

**Supported Tokens:**
| Symbol | Name | Address |
|--------|------|---------|
| TSLA | Tesla Token | `0x09572cED4772527f28c6Ea8E62B08C973fc47671` |
| GOOGL | Google Token | `0xC411824F1695feeC0f9b8C3d4810c2FD1AB1000a` |
| MSFT | Microsoft Token | `0x98e565A1d46d4018E46052C936322479431CA883` |

**Settlement Currency:** PayPal USD (PYUSD) - `0xCaC524BcA292aaade2DF8A05cC58F0a65B1B3bB9`

**Example Queries:**
```
- "What's the Tesla token price?"
- "How much to buy 5 Google tokens?"
- "Buy 3 Microsoft tokens" (auto-triggers MetaMask)
- "Sell 2 Tesla tokens"
- "Calculate sell return for 10 GOOGL"
```

**Token Resolution:**
Users can refer to tokens by name, symbol, or address:
```
"Tesla" / "TSLA" / "0x09572c..." → Tesla Token
"Google" / "GOOGL" / "0xC411..." → Google Token
"Microsoft" / "MSFT" / "0x98e5..." → Microsoft Token
```

---

## 🔍 How It Works

### Query Mode - MCP Architecture

**Step-by-Step Flow:**

```typescript
// 1. User sends query
POST http://localhost:3000/chat
{ "message": "Analyze contract 0xB6C5... on Sepolia" }

// 2. Intelligent Agent classifies query
const queryType = classifyQuery(message);
// → "contract_analysis"

// 3. Gemini LLM decides to call MCP tool
const toolCall = {
  tool: 'get_address_info',
  args: { address: '0xB6C5...', chain_id: '11155111' }
};

// 4. Docker MCP Client fetches from Blockscout
const result = await dockerMCPClient.callTool(toolCall);

// 5. LLM processes result and generates response
const analysis = await gemini.analyze(result);

// 6. Returns formatted response
return {
  success: true,
  response: "Contract Analysis: Vault (0xB6C5...)\n✅ SAFE TO INTERACT\n...",
  toolCalls: [{ tool: 'get_address_info', result }]
}
```

**MCP Tools Available:**
- `get_address_info` - Address details & verification
- `get_transactions_by_address` - Transaction history
- `get_tokens_by_address` - Token holdings
- `get_token_info` - Specific token details
- `get_transaction_by_hash` - Single transaction lookup

### Agent Mode - LangChain Architecture

**Step-by-Step Flow:**

```typescript
// 1. User sends message via WebSocket
socket.emit('chat_message', { message: 'Buy 5 Tesla tokens' });

// 2. LangChain + Gemini analyzes intent
const intent = await langchain.analyze(message);
// → "buy_transaction"

// 3. Agent calls vault tools
const tools = [
  { name: 'get_token_price', execute: (token) => {...} },
  { name: 'prepare_buy_transaction', execute: (token, amount) => {...} }
];

// 4. Executes tools via Ethers.js
const price = await vaultContract.getPrice(teslaAddress);
const tx = prepareBuyTransaction(teslaAddress, 5);

// 5. Returns MetaMask-ready transaction
return {
  success: true,
  response: "To buy 5 TSLA tokens:\n- Cost: 5.0 PYUSD\n...",
  toolCalls: [{
    tool: 'prepare_buy_transaction',
    result: {
      requiresMetaMask: true,
      steps: [
        { action: 'approve_pyusd', amount: '5.0' },
        { action: 'buy_stock', params: {...} }
      ]
    }
  }]
}

// 6. Frontend auto-triggers MetaMask
```

**Vault Tools Available:**
- `get_token_price` - Real-time price from vault
- `calculate_buy_cost` - Calculate purchase cost
- `calculate_sell_return` - Calculate sell return
- `get_stock_info` - Token details from vault
- `prepare_buy_transaction` - Prepare MetaMask buy tx
- `prepare_sell_transaction` - Prepare MetaMask sell tx
- `analyze_contract` - Call Query Mode for analysis
- `get_address_transactions` - Call Query Mode for txs

### MetaMask Transaction Flow

```typescript
// 1. User: "Buy 5 Tesla tokens"

// 2. Agent calculates cost
const price = await vault.getPrice(teslaAddress);
const cost = price * 5; // e.g., 5.0 PYUSD

// 3. Agent prepares transaction steps
return {
  steps: [
    {
      step: 1,
      action: 'approve_pyusd',
      description: 'Approve 5.0 PYUSD for vault',
      contract: PYUSD_ADDRESS,
      spender: VAULT_ADDRESS,
      amount: '5000000' // 6 decimals (PYUSD)
    },
    {
      step: 2,
      action: 'buy_stock',
      description: 'Buy 5 TSLA tokens',
      contract: VAULT_ADDRESS,
      function: 'buyStock',
      params: { token: teslaAddress, amount: 5 }
    }
  ],
  requiresMetaMask: true
};

// 4. Frontend detects requiresMetaMask flag
// 5. Opens MetaMask for user approval
// 6. User confirms → Transaction executes
// 7. Agent confirms success
```

---

## ⚙️ Configuration

### Environment Variables

| Variable | Description | Default | Required |
|----------|-------------|---------|----------|
| `GEMINI_API_KEY` | Google Gemini API key | - | ✅ Yes |
| `API_PORT` | Query Mode port | 3000 | ❌ No |
| `VAULT_PORT` | Agent Mode port | 3002 | ❌ No |
| `NODE_ENV` | Environment | development | ❌ No |
| `LOG_LEVEL` | Logging level | info | ❌ No |

### Smart Contract Addresses

**Sepolia Testnet (Chain ID: 11155111)**

```typescript
// Vault Contract
VAULT_ADDRESS = '0xB6C58FDB4BBffeD7B7224634AB932518a29e4C4b';

// PayPal USD (Settlement Currency)
PYUSD_ADDRESS = '0xCaC524BcA292aaade2DF8A05cC58F0a65B1B3bB9';

// RWA Tokens
TSLA = '0x09572cED4772527f28c6Ea8E62B08C973fc47671'; // Tesla
GOOGL = '0xC411824F1695feeC0f9b8C3d4810c2FD1AB1000a'; // Google
MSFT = '0x98e565A1d46d4018E46052C936322479431CA883'; // Microsoft
```

### Adding New Tokens

Edit `src/vault-tokens.json`:

```json
{
  "tokens": [
    {
      "address": "0x...",
      "name": "New Token",
      "symbol": "NEW",
      "decimals": 18,
      "isActive": true,
      "description": "Token description",
      "addedAt": "2025-01-17T00:00:00.000Z"
    }
  ],
  "metadata": {
    "version": "1.0.0",
    "vaultAddress": "0xB6C58FDB4BBffeD7B7224634AB932518a29e4C4b",
    "chainId": "11155111",
    "chainName": "Sepolia Testnet"
  }
}
```

---

## 🐛 Troubleshooting

### Query Mode Issues

**Problem**: "Docker MCP client not connected"

**Solution:**
```bash
# 1. Check Docker is running
docker ps

# 2. Restart Docker Desktop

# 3. Check MCP configuration
cat mcp-config.json

# 4. Restart server
npm run dev
```

**Problem**: "Tool call failed"

**Solution:**
```bash
# Check tool availability
curl http://localhost:3000/tools

# Check agent logs
tail -f logs/intelligent-agent.log
```

### Agent Mode Issues

**Problem**: "WebSocket connection failed"

**Solution:**
```bash
# 1. Check server is running
curl http://localhost:3002/health

# 2. Check port not in use
netstat -ano | findstr :3002

# 3. Check CORS settings in vault-ai-server.ts
```

**Problem**: "LLM invocation failed"

**Solution:**
```bash
# 1. Verify Gemini API key
echo $GEMINI_API_KEY

# 2. Test API key
curl https://generativelanguage.googleapis.com/v1beta/models \
  -H "x-goog-api-key: YOUR_KEY"

# 3. Check LangChain configuration
```

**Problem**: "Token not found"

**Solution:**
```bash
# 1. Check vault-tokens.json
cat src/vault-tokens.json

# 2. Ensure token is active
# isActive: true

# 3. Verify token address matches vault contract
```

### MetaMask Transaction Issues

**Problem**: "Transaction failed"

**Solution:**
```bash
# 1. Ensure you're on Sepolia testnet
# Chain ID: 11155111

# 2. Check PYUSD balance
# Need sufficient PYUSD for transactions

# 3. Verify contract addresses
# Vault: 0xB6C58FDB4BBffeD7B7224634AB932518a29e4C4b
# PYUSD: 0xCaC524BcA292aaade2DF8A05cC58F0a65B1B3bB9

# 4. Check gas settings
# Increase gas limit if needed
```

### Common Issues

**Port Already in Use:**
```bash
# Windows
netstat -ano | findstr :3000
netstat -ano | findstr :3002
taskkill /PID <PID> /F

# Linux/Mac
lsof -ti:3000 | xargs kill -9
lsof -ti:3002 | xargs kill -9
```

**Module Not Found:**
```bash
rm -rf node_modules package-lock.json
npm install
```

**TypeScript Errors:**
```bash
npm run build
npx tsc --noEmit
```

---

## 🏆 ETHOnline 2025 Integration

### Blockscout MCP Server
- **Usage**: Query Mode for multi-chain blockchain analytics
- **Integration**: Docker-based MCP client with Blockscout API
- **Chains**: Ethereum, Sepolia, Base, Optimism, Arbitrum

### Hardhat
- **Usage**: Smart contract development and deployment
- **Contracts**: Vault, RWA tokens (TSLA, GOOGL, MSFT)
- **Network**: Sepolia Testnet

### PayPal USD (PYUSD)
- **Usage**: Settlement currency for all vault transactions
- **Contract**: `0xCaC524BcA292aaade2DF8A05cC58F0a65B1B3bB9`
- **Features**: Buy/sell RWA tokens, stablecoin-backed liquidity

---

## 📚 Resources

### Documentation
- [Blockscout MCP](https://docs.blockscout.com/)
- [Hardhat](https://hardhat.org/docs)
- [LangChain](https://js.langchain.com/)
- [Gemini AI](https://ai.google.dev/)
- [Model Context Protocol](https://modelcontextprotocol.io/)
- [PayPal USD](https://developer.paypal.com/docs/pyusd/)

### Smart Contracts
- **Explorer**: https://eth-sepolia.blockscout.com/
- **Vault**: `0xB6C58FDB4BBffeD7B7224634AB932518a29e4C4b`
- **PYUSD**: `0xCaC524BcA292aaade2DF8A05cC58F0a65B1B3bB9`

---

## 📝 Project Structure

```
agent/
├── src/
│   ├── intelligent-chatbot-server.ts    # Query Mode HTTP Server
│   ├── intelligent-agent.ts             # MCP Agent + LLM Logic
│   ├── vault-ai-websocket-server.ts     # Agent Mode WebSocket Server
│   ├── vault-ai-agent.ts                # Vault Agent + LangChain
│   ├── docker-mcp-client.ts             # MCP Client (Blockscout)
│   ├── analysis/
│   │   └── response-generator.ts        # Response Formatting
│   ├── config/
│   │   └── index.ts                     # Configuration
│   ├── utils/
│   │   └── logger.ts                    # Logging
│   └── vault-tokens.json                # Token Definitions
├── public/
│   └── vault-ai-client.html             # Test Client UI
├── mcp-config.json                      # MCP Configuration
├── package.json                         # Dependencies
├── tsconfig.json                        # TypeScript Config
└── .env                                 # Environment Variables
```

---

## 🙏 Acknowledgments

- **Blockscout** - Multi-chain blockchain data and MCP server
- **Hardhat** - Smart contract development framework
- **PayPal USD** - Stablecoin settlement layer
- **Google Gemini** - LLM capabilities
- **LangChain** - AI agent orchestration
- **ETHOnline 2025** - For the opportunity to innovate

---

## 📄 License

MIT License

---

**Built with ❤️ for ETHOnline 2025**
