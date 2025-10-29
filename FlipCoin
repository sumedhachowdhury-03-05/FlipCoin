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
