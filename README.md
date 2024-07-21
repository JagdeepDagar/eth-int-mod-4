DegenToken Smart Contract
This is the Solidity code for the ETH: Intermediate Module 4 project. In this project, we create an ERC20 token named DegenToken with minting, burning, and redeeming functionalities.

Overview
The DegenToken contract is built using the OpenZeppelin library, leveraging the ERC20 and Ownable contracts. The ERC20 standard implementation provides essential functions for token operations, while the Ownable contract restricts certain functions to be callable only by the contract owner.

Dependencies
@openzeppelin/contracts/token/ERC20/ERC20.sol: Provides the standard implementation for ERC20 tokens, including functions for transferring tokens, checking balances, and managing allowances.
@openzeppelin/contracts/access/Ownable.sol: Adds ownership functionality, allowing the contract to have an owner and enabling access control for specific functions.
Contract Details
DegenToken Contract
The DegenToken contract inherits from ERC20 and Ownable. It includes the following functions:

Constructor: Initializes the ERC20 token with the name "Degen" and the symbol "DGN". It also sets the initial owner of the contract.
constructor(address initialOwner) ERC20("Degen", "DGN") Ownable(initialOwner) {}
mint: Allows the owner to mint new tokens to a specified address.
function mint(address to, uint256 amount) public onlyOwner {
    _mint(to, amount);
}
burn: Allows any token holder to burn their own tokens.

function burn(uint256 amount) public {
    _burn(msg.sender, amount);
}
redeem: Allows any token holder to redeem their tokens. This function is identical to the burn function.

function redeem(uint256 amount) public {
    _burn(msg.sender, amount);
}
Minting Tokens: Only the contract owner can mint new tokens. Use the mint function to create new tokens and assign them to a specific address.
mint(address to, uint256 amount)
Burning Tokens: Any token holder can burn their own tokens, reducing the total supply.
burn(uint256 amount)
Redeeming Tokens: Token holders can redeem their tokens using the redeem function, which internally calls the burn function.
redeem(uint256 amount)
