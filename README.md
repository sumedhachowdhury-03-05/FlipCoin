🎰 FlipCoin DApp on Celo

A simple decentralized coin flip betting game built with Solidity and deployed on the Celo Blockchain (Sepolia Testnet).

This project demonstrates how smart contracts can enable transparent, verifiable, and autonomous gaming logic — with no intermediaries required.

(🖼️ Image of DApp interface will be added here)

📜 Project Description

FlipCoin DApp allows users to bet ETH (or CELO on testnet) on a coin flip — choosing Heads (true) or Tails (false).

If the player wins, they receive double their bet.

All bets and results are stored on-chain.

The game logic is fully transparent and open for everyone to inspect.

⚠️ Note: Randomness in this demo uses simple block data and is not secure for production use. It’s intended for educational purposes.

⚙️ What It Does

The owner deploys the smart contract.

Users send a small amount of ETH/CELO along with their bet (Heads/Tails).

The contract determines the result using pseudo-random data.

Winners automatically receive 2× their bet.

The owner can withdraw accumulated funds at any time.

🌟 Features

🎯 Simple & Educational: Easy-to-read Solidity code for learning smart contract basics.
💰 Automated Payouts: Winners receive winnings instantly via smart contract logic.
📊 Transparent Results: Every game outcome is recorded publicly on the blockchain.
⚡ Celo Sepolia Deployment: Uses the Celo Testnet for fast and low-cost testing.
👑 Owner Controls: Only the contract owner can withdraw funds from the game pool.

📄 Smart Contract

Language: Solidity ^0.8.20

Framework: Remix / Hardhat compatible

Network: Celo Sepolia Testnet

Contract Name: FlipCoin

Deployed Transaction or Contract Address:
👉 View on Blockscout
 (replace with actual address once deployed)

🧩 Future Enhancements

🎮 Add a React or Next.js front-end using Celo Composer or Ethers.js.
🪙 Implement Chainlink VRF or another secure randomness source.
💼 Include player history and leaderboard tracking.
📊 Display live results and statistics on the UI.
🔐 Add deposit limits and configurable house fees.

🙌 Acknowledgments

Celo Blockchain — for sustainable and developer-friendly infrastructure

Remix IDE — for quick prototyping and contract deployment

Blockscout — for transparent on-chain transaction viewing

💡 Pro Tip

Experiment, test, and learn by doing — tweak logic, observe outcomes, and see how decentralized games truly work under the hood.

🧠 Made with ❤️ by [Your Name / XXX]
