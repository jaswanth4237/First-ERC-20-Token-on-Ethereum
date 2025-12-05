# MyToken (MTK)

## Overview
MyToken is an ERC-20 compatible cryptocurrency token built on Ethereum using Solidity.  
This project demonstrates how tokens work, how balances are stored, how transfer operations function, and how approvals and allowances operate in real ERC-20 systems.

The smart contract was deployed and tested using Remix IDE.

---

## Token Details
Name: MyToken  
Symbol: MTK  
Decimals: 18  
Total Supply: 1,000,000 MTK  

---

## Features
- Standard ERC-20 implementation  
- Transfer tokens between addresses  
- Approve another address to spend tokens  
- Spend approved tokens using transferFrom  
- Logs Transfer & Approval events  
- Uses mapping for balance and allowance storage  

---

# How to Deploy (Remix IDE)

1. Open Remix IDE  
2. Create a file named MyToken.sol  
3. Paste the ERC-20 contract code  
4. Go to the Solidity Compiler (0.8.x) and click Compile  
5. Go to Deploy & Run Transactions  
6. Select environment: Remix VM (Prague)  
7. Enter constructor value: 1000000  
8. Click Deploy  

Your token is now deployed.

---

# How to Use the Token

Below is the complete explanation of each ERC-20 function with examples.

---

# 1. Check Balance  
## Function: balanceOf(address account)

```solidity
balanceOf(address account)
This function returns the number of tokens a wallet owns.
Example:
balanceOf(0x5B38...) → 1000000
Meaning the address holds 1,000,000 MTK.
If an address has never received tokens, it returns 0.
Balances are stored as:
mapping(address => uint256) public balanceOf;
Use this after transfers to confirm updated balances.
---
#2. Transfer Tokens
##Function: transfer(address to, uint256 amount)
```solidity
transfer(address to, uint256 amount)
This sends tokens from the sender’s account to another address.
Example:
transfer(0xAb84..., 100)
Result:
Sender balance: minus 100
Receiver balance: plus 100
A Transfer event is logged
Important:
Transfer will fail if:
Sender does not have enough balance
Receiver is the zero address (0x000...0000)

#3. Approve Spending
##Function: approve(address spender, uint256 amount)
approve(address spender, uint256 amount)
This lets another address spend some of your tokens.
Example:
approve(0xAb84..., 50)
Meaning:
Spender can spend up to 50 MTK from your wallet
They cannot spend more than 50
They cannot spend without approval
Allowances are stored as:
mapping(address => mapping(address => uint256)) public allowance;
Example:
allowance(Owner, Spender) → 50

#4. Spend Approved Tokens
##Function: transferFrom(address from, address to, uint256 amount)
transferFrom(address from, address to, uint256 amount)
This lets the spender transfer tokens from the owner’s wallet to another address, using approved allowance.
Example (after approve):
Owner runs:
approve(Spender, 50)
Then Spender runs:
transferFrom(Owner, Receiver, 20)
Result:
Owner: -20 tokens
Receiver: +20 tokens
Allowance: 50 → 30
Transfer event is logged
transferFrom fails if:
Allowance < amount
Owner does not have enough balance

This is how exchanges and DeFi apps move tokens on behalf of users.
