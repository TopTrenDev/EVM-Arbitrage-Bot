# **Arbitrage-Bot**  

Welcome to the `Arbitrage-Bot` repository, a tool designed to simplify and automate blockchain arbitrage strategies on **EVM-based networks** like Ethereum, Binance Smart Chain, Base, Polygon, and Arbitrum. This bot builds upon a **Uniswap bot**, extending it to work across several swap platforms to maximize trading revenue. Our goal is to help developers understand arbitrage strategies and offer step-by-step guidance to create their own successful trading bots.

---

## **Table of Contents**  

- [Commented Code](#commented-code)
- [Getting Started](#getting-started)
  - [Clone the Repository](#clone-the-repository)
  - [Install Dependencies](#install-dependencies)
  - [Create and Setup .env File](#create-and-setup-env-file)
  - [Set Deployment Environment](#set-deployment-environment)
  - [Launch Hardhat Node](#launch-hardhat-node)
  - [Deploy Trading Contract](#deploy-trading-contract)
  - [Start the Trading Bot](#start-the-trading-bot)
  - [Trigger the Arbitrage](#trigger-the-arbitrage)
- [Additional Information](#additional-information)
- [Strategy Overview](#strategy-overview)
- [Using Trading Bot on Mainnet](#using-trading-bot-on-mainnet)
- [Contributions](#contributions)
- [License](#license)
- [Project Updates](#project-updates)
- [Donations](#donations)
---

## **Commented Code**

This code is thoroughly documented with comments to clarify the functionality of each component. This ensures that users and developers alike can understand and adapt the code for their purposes.

---

## **Getting Started**

### **Clone the Repository**

Clone this repository to your local machine:

```bash
git clone https://github.com/toptrendev/Arbitrage-Bot.git
cd Arbitrage-Bot
```

### **Install Dependencies**

Ensure that you have **Node.js** and **npm** installed in your environment. Then, install the necessary dependencies:

```bash
npm install
```

### **Create and Setup .env File**

Create a `.env` file with the following variables:

```env
ARB_FOR=""             // Token0 address (in quotes)
ARB_AGAINST=""         // Token1 address (in quotes)
PRICE_DIFFERENCE=""    // Price difference between 2 DEXs
UNITS=""               // Reported price units
GAS_LIMIT=""           // Desired maximum gas limit
GAS_PRICE=""           // Desired gas price in gwei
```

Make sure that your `.env` file is **private** and never shared.

### **Set Deployment Environment**

Set up your deployment environment by forking the desired network. It's recommended to use your own RPC URL for better reliability. You can create Web3 API keys on **Infura**: [Infura](https://www.infura.io/).

Add the following variables to your `.env` file:

```env
API_KEY=""        // Your Web3 API key
PRIVATE_KEY=""    // Your Hardhat wallet private key
```

### **Launch Hardhat Node**

To launch the Hardhat node, run:

```bash
npx hardhat node
```

### **Deploy Trading Contract**

Deploy the trading contract using the following command:

```bash
npx hardhat run --network localhost scripts/1_deploy.js
```

Copy the deployed contract address and paste it into the **ARBITRAGE_ADDRESS** field in the [config.json](./config.json).

### **Start the Trading Bot**

To start the bot, run the following:

```bash
node bot.js
```

Refer to the [Arbitrage Bot Project Documentation](./Arbitrage-Bot-Project-Documentations/Trading-Bot-Functions-Explanation.md) for detailed explanations of the bot's functions.

---

### **Trigger the Arbitrage**

Because we are using a forked Ethereum mainnet, the blockchain state is frozen at the moment of the fork. We need to manipulate the price of tokens to trigger the arbitrage bot.

To trigger the arbitrage trade, run:

```bash
npx hardhat run --network localhost scripts/2_manipulate.js
```

**Note**: This script manipulates the token price on your local blockchain. If you want to trade on other **ERC20** tokens (other than LINK/WETH in this example), modify the unlocked account and token amounts accordingly.

---

## **Additional Information**

The [Server](./helpers/server.js) script spins up a local server to manage bot operations.

---

## **Strategy Overview**

The implemented strategy is an example of arbitrage between **Uniswap** and **Sushiswap**. The price of **LINK/WETH** is manipulated on the local blockchain, and the reserves are fetched from both DEXs to identify the best arbitrage opportunities.

---

## **Using Trading Bot on Mainnet**

To use the trading bot on a live Ethereum network, please refer to our [Arbitrage Bot Mainnet Documentation](./Arbitrage-Bot-Project-Documentations/Mainnet.md).

---

## **📬 Contact & Community**  

📢 **Telegram:** [@toptrendev](https://t.me/toptrendev)  
📢 **Twitter:** [toptrendev](https://x.com/toptrendev)  
