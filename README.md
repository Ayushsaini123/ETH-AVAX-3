### "PIE Token Smart Contract" ###
The **PIE** project introduces an **ERC20** token named PIE(PIE) built on the Ethereum blockchain. It leverages OpenZeppelin's secure and tested contracts for token functionality and ownership management. This contract ensures a secure and efficient token management system with the essential capabilities for minting, burning, and transferring tokens.
## Description
The PIE Token Smart Contract is a custom implementation of an ERC-20 token on the Ethereum blockchain, utilizing the OpenZeppelin library for enhanced security and functionality. This contract defines a token named "PIE" with the symbol "PIE" and includes features for minting, burning, and transferring tokens. The contract is controlled by an owner who has exclusive rights to mint new tokens.

## Getting Started
### Executing Program
To execute this program you can go to the Remix IDE which is open IDE for Solidity. For that you can click on this link https://remix.ethereum.org/

Once you successfully reached to the IDE create a new file by clicking on the '+' icon and saving that file with .sol extension (e.g. project code). After this copy and paste the code in your file that is given below 

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity 0.8.25;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.0.0/contracts/token/ERC20/ERC20.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.0.0/contracts/access/Ownable.sol";

contract PIE is ERC20, Ownable {
    string constant tokenName = "PIE";
    string constant Symbol = "PIE";

    constructor() ERC20(tokenName, Symbol) {
        // Initialize the token with a total supply of 1000 tokens
        _mint(owner(), 1000 * (10 ** decimals()));
    }

    function decimals() public virtual override view returns(uint8){
        return 0;
    }

    function mint(address a , uint money) public onlyOwner {
        _mint(a, money);
    }

    function burn(uint money) public {
        _burn(msg.sender, money);
    }

    function transfer(address a, uint money) public virtual override returns (bool) {
        _transfer(msg.sender, a,money);
        return true;
    }
}

```

After pasting this code you have to compile the code from the left hand sidebar. click on the 'Solidity Compiler' then click on the 'Compile project code' button.

After the successful compilation of the code you have to deploy the program. For that you have again another option on the left sidebar that is 'Deploy & Run Transactions' and then you will see a deploy button; before clicking on it make sure that the file showing there is 'project code'. Then you will be able to see the file in the 'Deployed/Unpinned Contracts' click on that now all the public variable and functions are visible to you now execute and fetch the values according to you. And be aware that here you will see the function that you have neither created nor implemented, these extra functions are the functions of the libraries we have inherited (ERC20 and ownable) and it is up to you that you gonna use them or not.

## Authors
Ayush Saini

#Gittup Link: https://github.com/Ayushsaini123

## License
This project is licensed under the MIT license(https://github.com/Ayushsaini123/ETH-AVAX-3/blob/main/LICENSE)
