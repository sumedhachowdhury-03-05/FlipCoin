# FlipCoin
Solidity smart contract for a decentralized coin flip betting game using on-chain randomness. Includes ETH betting, payouts, and event logging.
# 🪙 FlipCoin - Simple Decentralized Coin Flip Betting Game

**FlipCoin** is a simple, beginner-friendly decentralized **coin flip betting game** built with **Solidity**.  
Players can wager ETH on **Heads (true)** or **Tails (false)** and instantly win **2× their bet** if they guess correctly!  

This project demonstrates the fundamentals of smart contract development, randomness (even if basic), and decentralized game mechanics.

---



// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

/*
 * FlipCoin - Simple coin flip betting game (demo version)
 * Players bet on heads (true) or tails (false).
 * Randomness comes from block data (not secure!).
 */

contract FlipCoin {
    address public owner;

    event BetPlaced(address indexed player, uint256 amount, bool choice, bool result, bool won);

    constructor() {
        owner = msg.sender;
    }

    // Player makes a bet choosing heads (true) or tails (false)
    function flip(bool _choice) public payable {
        require(msg.value > 0, "You must send ETH to play");

        // ⚠️ Not secure randomness — for learning only
        bool result = (block.timestamp + block.prevrandao) % 2 == 0;

        bool won = (result == _choice);

        if (won) {
            payable(msg.sender).transfer(msg.value * 2);
        }

        emit BetPlaced(msg.sender, msg.value, _choice, result, won);
    }

    // Owner can withdraw contract balance
    function withdraw(uint256 amount) public {
        require(msg.sender == owner, "Only owner can withdraw");
        payable(owner).transfer(amount);
    }

    // Allow contract to receive ETH
    receive() external payable {}
}



## 🎯 Project Description

The **FlipCoin** smart contract allows users to bet Ether (ETH) on a coin toss outcome.  
The flip result is determined using pseudo-randomness derived from block data — making it **a great learning project** for beginners exploring Solidity, Ethereum, and blockchain-based gaming.

> ⚠️ **Note:** This version uses on-chain pseudo-randomness (`block.timestamp + block.prevrandao`) which is **not secure** for real betting.  
> It is intended **for educational and demonstration purposes only.**

---

## ⚙️ What It Does

1. A player calls the `flip()` function and sends ETH with their transaction.  
2. The player chooses either:
   - **Heads** → `true`
   - **Tails** → `false`
3. The contract uses simple block data to decide the result.  
4. If the player guessed correctly → they automatically receive **2×** their wager.  
5. All results are stored and can be tracked through emitted blockchain events.

---

## 🌟 Features

✅ **Fully On-Chain Betting** — Every action happens on Ethereum  
✅ **Instant Rewards** — Winners are paid automatically  
✅ **Event Logging** — Every bet is recorded with results  
✅ **Beginner-Friendly Solidity Code** — Clean, simple, and easy to understand  
✅ **No Centralized Control** — Once deployed, anyone can play  

---

## 🧠 Smart Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

/*
 * FlipCoin - Simple coin flip betting game (demo version)
 * Players bet on heads (true) or tails (false).
 * Randomness comes from block data (not secure!).
 */

contract FlipCoin {
    address public owner;

    event BetPlaced(address indexed player, uint256 amount, bool choice, bool result, bool won);

    constructor() {
        owner = msg.sender;
    }

    // Player makes a bet choosing heads (true) or tails (false)
    function flip(bool _choice) public payable {
        require(msg.value > 0, "You must send ETH to play");

        // ⚠️ Not secure randomness — for learning only
        bool result = (block.timestamp + block.prevrandao) % 2 == 0;

        bool won = (result == _choice);

        if (won) {
            payable(msg.sender).transfer(msg.value * 2);
        }

        emit BetPlaced(msg.sender, msg.value, _choice, result, won);
    }

    // Owner can withdraw contract balance
    function withdraw(uint256 amount) public {
        require(msg.sender == owner, "Only owner can withdraw");
        payable(owner).transfer(amount);
    }

    // Allow contract to receive ETH
    receive() external payable {}
}
