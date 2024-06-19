MyToken Smart Contract

 Introduction

The `MyToken` contract is an ERC-20 token implementation on the Ethereum blockchain. This contract allows for the creation, minting, and burning of tokens with basic functionality. It includes mechanisms to track total supply and balances of token holders.

 Features

1. Public Variables: 
   - `TokenName`: The name of the token.
   - `TokenAbbrv`: The abbreviation of the token.
   - `totalSupply`: The total supply of the tokens.

2. Balances Mapping: 
   - Keeps track of each address's balance of tokens.

3. Mint Function: 
   - Increases the total supply of tokens.
   - Increases the balance of a specified address.

4. Burn Function: 
   - Decreases the total supply of tokens.
   - Decreases the balance of a specified address.
   - Includes a check to ensure the balance is sufficient before burning.

Contract Details

 Public Variables

- `string public TokenName = "ABC";`
  - This variable stores the name of the token.
  
- `string public TokenAbbrv = "DEF";`
  - This variable stores the abbreviation of the token.
  
- `uint public totalSupply = 0;`
  - This variable stores the total supply of the token and is initially set to zero.

 Balances Mapping

- `mapping(address => uint) public balances;`
  - This mapping associates each address with its corresponding token balance.

 Mint Function

The `mint` function allows for the creation of new tokens. It takes two parameters:
1. `_address`: The address to which the minted tokens will be assigned.
2. `_value`: The amount of tokens to be minted.

```solidity
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
```

 Burn Function

The `burn` function allows for the destruction of tokens. It takes two parameters:
1. `_address`: The address from which the tokens will be burned.
2. `_value`: The amount of tokens to be burned.

The function includes a check to ensure the address has enough tokens to be burned:

```solidity
function burn(address _address, uint _value) public {
    if (balances[_address] >= _value) {
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}
```
 Usage

1. Minting Tokens:
   - To mint tokens, call the `mint` function with the recipient's address and the amount of tokens to be minted.
   - Example: `mint(0xRecipientAddress, 100);` will mint 100 tokens to the specified address.

2. Burning Tokens:
   - To burn tokens, call the `burn` function with the holder's address and the amount of tokens to be burned.
   - Example: `burn(0xHolderAddress, 50);` will burn 50 tokens from the specified address if the address has enough tokens.

 License

This contract is licensed under the MIT License. See the SPDX identifier at the top of the contract for more details.

