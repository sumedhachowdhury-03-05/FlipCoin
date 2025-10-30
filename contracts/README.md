// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

/// @title FlipCoin Betting Game (Demo)
/// @author You
/// @notice A simple coin flip betting contract for educational purposes
/// @dev Randomness is derived from block data and NOT secure for production use.

contract FlipCoin {
    /// @notice Address of the contract owner
    address public owner;

    /// @notice Emitted when a player places a bet
    /// @param player Address of the player
    /// @param amount Amount of ETH bet
    /// @param choice Player’s choice: true = heads, false = tails
    /// @param result Actual result of the coin flip
    /// @param won Whether the player won the bet
    event BetPlaced(
        address indexed player,
        uint256 amount,
        bool choice,
        bool result,
        bool won
    );

    /// @notice Constructor sets the deployer as the owner
    constructor() {
        owner = msg.sender;
    }

    /// @notice Player makes a bet choosing heads (true) or tails (false)
    /// @dev Uses `block.timestamp` and `block.prevrandao` for pseudo-randomness
    /// @param _choice Player’s choice: true = heads, false = tails
    function flip(bool _choice) external payable {
        require(msg.value > 0, "You must send ETH to play");

        // ⚠️ Not secure randomness — for learning purposes only
        bool result = (block.timestamp + block.prevrandao) % 2 == 0;

        bool won = (result == _choice);

        if (won) {
            payable(msg.sender).transfer(msg.value * 2);
        }

        emit BetPlaced(msg.sender, msg.value, _choice, result, won);
    }

    /// @notice Allows the owner to withdraw contract funds
    /// @param amount The amount to withdraw (in wei)
    function withdraw(uint256 amount) external {
        require(msg.sender == owner, "Only owner can withdraw");
        payable(owner).transfer(amount);
    }

    /// @notice Allows the contract to receive ETH
    receive() external payable {}
}
