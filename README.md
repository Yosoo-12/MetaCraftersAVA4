# DegenToken Smart Contract

## Overview

The DegenToken smart contract is a simple ERC-20 token with the ability to mint, transfer, burn, and redeem tokens for in-game items. This contract allows users to interact with in-game assets such as items and use the Degen tokens to redeem them.

## Features

- **ERC-20 Token**: The contract inherits from OpenZeppelin's ERC-20 implementation and provides the standard functionalities like minting, transferring, and burning tokens.
- **In-game Items**: Users can redeem their Degen tokens for in-game items, such as Medkits, Flames, and Compasses.
- **Owned Items**: The contract keeps track of the items owned by each address, allowing players to see their inventory.
- **Custom Functions**:
  - Mint tokens
  - Transfer tokens
  - Redeem tokens for in-game items
  - Fetch available game items
  - View owned items
  
## Requirements

- **Solidity Version**: `^0.8.18`
- **OpenZeppelin Contracts**: For ERC-20 and Ownable implementations.
  - Install dependencies using npm: 
    ```bash
    npm install @openzeppelin/contracts
    ```

## Functions

### 1. **mint(address to, uint256 amount)**
   Mints new Degen tokens to the specified address.
   - Only the contract owner can mint tokens.
   
### 2. **decimals()**
   Returns the number of decimal places for the token, which is set to 0 to prevent fractional tokens.
   
### 3. **getBalance()**
   Returns the balance of Degen tokens for the caller.

### 4. **burnTokens(uint256 amount)**
   Burns a specific amount of Degen tokens from the caller’s balance.

### 5. **transferTokens(address recipient, uint256 amount)**
   Allows users to transfer Degen tokens to another address.

### 6. **redeem(uint256 itemId)**
   Redeems a specific in-game item by burning Degen tokens equal to the item’s cost. The user receives the item and it is stored in their inventory.

### 7. **getGameItems()**
   Returns an array of all available in-game items that can be redeemed.

### 8. **getOwnedItems()**
   Returns an array of items owned by the caller.

## Game Items

- **Medkit**: Cost 10 Degen Tokens
- **Flames**: Cost 20 Degen Tokens
- **Compass**: Cost 55 Degen Tokens

## Events

### 1. **ItemRedeemed(address indexed redeemer, uint256 itemId, string itemName, uint256 itemCost)**
   Emitted when a user successfully redeems an item. Contains details about the redeemer, item ID, name, and cost.

## Contract Deployment

1. **Deploy the contract**:
   - The contract owner is the address that deploys the contract.
   - Upon deployment, some initial in-game items (Medkit, Flames, Compass) are added to the `gameItems` list.

2. **Interacting with the Contract**:
   - Users can mint tokens, transfer them, and redeem them for in-game items.
   - Each user’s balance and inventory are stored in the contract, ensuring transparency and security.

## Security Considerations

- **Access Control**: Only the owner of the contract can mint new tokens.
- **Token Burn**: Tokens used for redeeming items are burned from the caller's balance, preventing them from being reused.

## License

This project is licensed under the MIT License.
