# WithdrawSelf.sol
WithdrawSelf.sol
pragma solidity ^0.8.20;
contract WithdrawSelf {
    mapping(address => uint) public balance;

    function deposit() public payable {
        balance[msg.sender] += msg.value;
    }

    function withdraw(uint amount) public {
        require(balance[msg.sender] >= amount);
        balance[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);
    }
}
