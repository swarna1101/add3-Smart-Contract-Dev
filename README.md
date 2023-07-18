# add3-Smart-Contract-Dev

This is an implementation of ERC-20 standard Ethereum Token, mintable and burnable, with owner access permissions and pausable module.

In this repository you can:


* Deploy an ERC-20 in different networks using Hardhat, Truffle and Foundry
* Run tests on ERC-20 smart contracts using Hardhat, Truffle and Foundry

The ERC20 Smart Contract has to allow only the owner to:
* **Mint** an input amount of tokens to an arbitrary wallet.
* **Burn** an input amount of only ERC20 Smart Contract owner’s tokens (to be clear: the smart
contract has to allow only the tokens of the smart contract owner to be burnt )
* **Pause** the contract (by default the contract is not paused).


## Erc-20 implementation

This smart contract is an implementation of the ERC20 token standard in the Solidity programming language.

ERC-20 is a standard interface for tokens widely used standard for creating fungible tokens, which are tokens that are interchangeable and have a uniform value.

More Information about Solidity Language and ERC-20 Standard:

- [Solidity](https://solidity.readthedocs.io/en/v0.8.4/): `v0.8.4`
- [ERC-20](https://eips.ethereum.org/EIPS/eip-20)

This repository contains an [`ERC-20`](./contracts/ERC20.sol) smart contract implementetion that can be found in `./contracts` folder.



