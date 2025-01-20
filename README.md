# DELIVERABLE-THE-SOLIDITY-CODE-AND-DEPLOYMENT-STEPS-ON-A-TEST-ETHEREUM-NETWORK.
DELIVERABLE


pragma solidity ^0.8.0;

contract SimpleToken {
    string public name = "Simple Token";
    string public symbol = "ST";
    uint8 public decimals = 18;
    uint256 totalSupply = 100000000000000000000000000; 
    mapping(address => uint256) balances;
    constructor() {
        balances[msg.sender] = totalSupply;
    }
    function balanceOf(address owner) public view returns (uint256) {
        return balances[owner];
    }
    function transfer(address recipient, uint256 amount) public returns (bool) {
        require(balances[msg.sender] >= amount, "Insufficient balance");
        balances[msg.sender] -= amount;
        balances[recipient] += amount;
        return true;
    }
}
