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

### Erc-20 Methods

#### Constructor

The [`constructor`](./contracts/ERC20.sol#L33) function sets `name`, `symbol`, `decimals` and `totalSupply` of the token.

#### Balance

The view function [`balanceOf`](./contracts/ERC20.sol#L72) returns the account balance of an account `_owner`.

#### Allowance

The view function [`allowance`](./contracts/ERC20.sol#L127) returns the amount which address `_spender` is allowed to spend from another account - `_owner`.

#### Transfer and Transfer From

The method  [`transfer`](./contracts/ERC20.sol#L52) is called by `msg.sender` account and transfers `_value` amount of tokens to another address `_to`.

The method [`transferFrom`](./contracts/ERC20.sol#L102) allows one third account `msg.sender` transfers `_value` amount of tokens from other address `_from` to other address `_to`. The `_from` address needs to approve `msg.sender` spend the `_value` first.

Both methods fire the `Transfer` event.

#### Approve

The method [`approve`](./contracts/ERC20.sol#L84) allows one account - `_spender` - to spend from another account - `msg.sender` - the `_amount`.

#### Increase Approval and Decrease Approval

Those methods are not a ERC-20 standard but can be used to manage the value of the account allowances.

The method [`increaseApproval`](./contracts/ERC20.sol#L140) allows another account - `_spender` - to spend from another account - `msg.sender` - adding to current allowance the `_addedValue` amount.

The method [`decreaseApproval`](./contracts/ERC20.sol#L157) reduces the value approved to `_spender` to spend from another account - `msg.sender` - subtracting the `_subtractedValue` from the current approval amount. If the `_subtractedValue` is bigger than current approval the value will reduce to 0.

#### Mint, Burn and Burn From

Those methods are not a ERC-20 standard but are commonly used to create and destroy tokens.

The [`mintTo`](./contracts/ERC20.sol#L180) function creates `_amount` tokens and assigns them to account `_to`, increasing the total supply. Only the smart contract owner can mint.

The [`burn`](./contracts/ERC20.sol#L199) function destroys `_amount` tokens from `msg.sender`, reducing the total supply.

The [`burnFrom`](./contracts/ERC20.sol#L218) function destroys `_amount` tokens from account `_from`, reducing the total supply. The `_from` address needs to approve the `msg.sender` address spend the `_amount` first.

All these methods fire the `Transfer` event.

## Erc-20 Modules in this example

#### Ownable

The [`ownable`](./contracts/ownership/Ownable.sol) smart contract module provides a basic access control mechanism, where there is an account - an owner - that has exclusive access to specific functions.

This module is used through inheritance.

It will make available the modifier `onlyOwner`, which can be applied to smart contract functions to restrict their use to the owner.

By default, the owner account will be the one that deploys the contract.

The owner address can be changed by smart contract owner with method `transferOwnership`.

#### Pausable

The [`Pausable`](./contracts/lifecycle/Pausable.sol) module is smart contract which allows children to implement an emergency stop mechanism that can be triggered by an authorized account.

This module is used through inheritance.

It will make available the modifiers `whenNotPaused` and `whenPaused`, which can be applied to the functions of your contract.

In this example, only the owner account can trigger call `pause` and `unpause` methods.


