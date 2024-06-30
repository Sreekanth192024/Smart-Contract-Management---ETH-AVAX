# Eth + Avax Proof Smart Contract Management

This is a Solidity smart contract named `Assesment` that demonstrates various error-handling techniques, Connecting the Front end to a wallet and etc.

## Table of Contents

- [Requirements](#requirements)
- [Contract Overview](#contract-overview)
- [Index_Overview](#index-overview)
- [Usage](#usage)
- [Authors](#authors)
- [License](#license)

## Requirements

Four Project Requirements
There are four requirements for the project which we will explain in detail in the video:
 
1. You will submit your project on GitHub, so you will need an account and know how to share a public repository
2. You will include a README.md file in your project's GitHub repository (root folder). The README should provide a concise and clear overview of your project's purpose and functionality.
3. You will record a video of 5 mins or less reviewing the three contracts you choose - Loom is a great tool to use if needed.
4. For some assessments/projects, you will need to share a transaction ID. (This project is NOT one of them.)

# Contract Overview

This Solidity smart contract, named "Assessment," is designed to manage the deposit, withdrawal, and transfer of Ether. It offers various functions and events to interact with the contract's balance, all while enforcing the `onlyOwner` modifier to ensure that only the contract owner has control over key operations.

## Functions

### `deposit(uint256 _amount)`

This function allows the owner of the contract to deposit Ether into the contract. It takes one parameter, `_amount`, which represents the amount of Ether to be deposited. The function increases the contract's balance by the deposited amount and emits a `Deposit` event to record the deposit.

### `withdraw(uint256 _withdrawAmount)`

This function enables the owner of the contract to withdraw Ether from the contract. It takes one parameter, `_withdrawAmount`, which specifies the amount of Ether to be withdrawn. The function checks if the contract's balance is sufficient for the withdrawal, performs the withdrawal, and emits a `Withdraw` event to record the withdrawal.

### `transfer(address _to, uint256 _amount)`

This function allows the owner of the contract to transfer Ether to a specified address. It takes two parameters: `_to` (the recipient's address) and `_amount` (the amount of Ether to be transferred). The function checks if the contract's balance is sufficient for the transfer, transfers the Ether to the specified address, and emits a `Transfer` event to record the transfer.

### `getBalance()`

This read-only function allows anyone to check the current balance of the contract without making any changes to the contract state.

## Events

The contract emits the following events during execution:

### `Deposit(uint256 amount)`

Emits when the `deposit` function is called. Logs the amount of Ether deposited into the contract.

### `Withdraw(uint256 amount)`

Emits when the `withdraw` function is called. Logs the amount of Ether withdrawn from the contract.

### `Transfer(address indexed to, uint256 amount)`

Emits when the `transfer` function is called. Logs the recipient's address and the amount of Ether transferred.

## Modifiers

### `onlyOwner`

This modifier restricts certain functions (deposit, withdraw, and transfer) to be callable only by the owner of the contract. It checks whether the sender of the transaction is the same as the contract's owner and reverts the transaction if not.

## Contract Variables

- `owner`

  A public address variable that stores the address of the contract owner. The owner is the account that deployed the contract and has special privileges.

- `balance`

  A public unsigned integer variable that stores the current balance of Ether held by the contract. This balance is updated when deposits, withdrawals, or transfers occur.

# Index Overview



This React-based decentralized application (DApp) provides a user interface to interact with a smart contract deployed on the Ethereum blockchain. The DApp allows users to connect their MetaMask wallets and perform various operations on the smart contract, including depositing, withdrawing, and transferring Ether.

## Components

### Connection Setup (`getWallet` and `connectAccount` functions)

- The `getWallet` function checks if the MetaMask wallet extension is available in the user's browser and retrieves the current account if available.
- The `connectAccount` function enables users to connect their MetaMask wallets to the DApp. It also initializes the interaction with the smart contract.

### Smart Contract Interaction (`getATMContract`, `getBalance`, `deposit`, `withdraw`, `transferFunds` functions)

- The `getATMContract` function creates an instance of the smart contract using the ethers library.
- The `getBalance` function retrieves the user's account balance from the smart contract and displays it.
- The `deposit` function allows users to deposit a specified amount of Ether into the smart contract.
- The `withdraw` function enables users to withdraw a specified amount of Ether from the smart contract.
- The `transferFunds` function facilitates the transfer of Ether to a recipient's address.

### User Interface (`initUser` function)

- The `initUser` function dynamically renders different components based on the user's interaction and wallet status. It displays the user's account, balance, and provides input fields for deposit, withdrawal, and transfers.
- Users can also exit the DApp using the "Exit" button.

## Styling

The DApp includes basic styling using CSS to create a visually appealing interface. It features a gradient background animation.

## Usage

1. Users must have the MetaMask wallet extension installed in their browser.
2. They can connect their MetaMask wallets to the DApp by clicking the "Connect Your MetaMask Wallet" button.
3. Once connected, users can check their account balance, deposit funds, withdraw funds, and transfer Ether to other addresses.
4. The DApp provides real-time updates of the account balance after each transaction.
5. Users can exit the DApp using the "Exit" button.

This DApp serves as a simple demonstration of how to interact with a smart contract using React and MetaMask, enabling users to manage their Ethereum assets seamlessly.

## Usage

### Starter Next/Hardhat Project

Inside the gitpod, you will want to do the following to get the code running on your computer.

1. Inside the project directory, in the terminal type: npm i
2. Open two additional terminals in your VS code
3. In the second terminal type: npx hardhat node
4. In the third terminal, type: npx hardhat run --network localhost scripts/deploy.js
5. Back in the first terminal, type npm run dev to launch the front-end.

After this, the project will be running on your localhost. 
Typically at http://localhost:3000/

Addionally:

1. Make your hardhat port public to access `https://8545-metacrafterc-scmstarter-msotxik1s10.ws-us104.gitpod.io` for the RPC url.
2. Set up your metamask: make sure you have the account 0 as an account, you should also make a new net work using the RPC url above.
3. Make use of `31337` for Chain ID & `ETH` for Currencey Symbol. Save your network and change into that network.
4. Once set up you can run your code and try my codes.
## Authors

Metacrafter Randel Jason B. Espiritu

## License

This contract is released under the MIT License. You can find the license information in the contract source code.

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;
