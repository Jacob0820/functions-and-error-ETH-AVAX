# functions-and-error-ETH-AVAX
# Smart Contract with Error Handling

This project demonstrates the usage of require(), assert(), and revert() statements in a Solidity smart contract. These statements are essential for handling errors and ensuring the contract's security.

## Project Structure

- contracts/ : Directory containing the smart contract source code.
- README.md : Project overview and instructions.

## Smart Contract Overview

The smart contract includes functions that showcase different scenarios where require(), assert(), and revert() are used.

- *deposit(uint256 amount)* : Demonstrates the use of require() for input validation.
- *withdraw(uint256 amount)* : Demonstrates the use of require() to check for sufficient balance.
- *testAssert()* : Demonstrates the use of assert() to check for internal errors.
- *testRevert()* : Demonstrates the use of revert() for reverting state changes.

## Getting Started

Follow these instructions to deploy and interact with the smart contract:

1. *Install Truffle:*
    sh
    npm install -g truffle
    

2. *Compile the Contract:*
    sh
    truffle compile
    

3. *Deploy the Contract:*
    sh
    truffle migrate
    

4. *Interact with the Contract:*
    Use Truffle console or any Ethereum client to interact with the deployed contract.

## Example Smart Contract

Here's an example of a smart contract that includes require(), assert(), and revert():

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ErrorHandlingExample {

    uint256 public balance;

    constructor() {
        balance = 0;
    }

    function deposit(uint256 amount) public {
        require(amount > 0, "Amount must be greater than zero");
        balance += amount;
    }

    function withdraw(uint256 amount) public {
        require(amount <= balance, "Insufficient balance");
        balance -= amount;
    }

    function testAssert() public view {
        assert(balance >= 0);
    }

    function testRevert() public view {
        if (balance < 100) {
            revert("Balance is less than 100");
        }
    }
}
