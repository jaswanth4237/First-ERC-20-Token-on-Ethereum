# MyToken (MTK)

## Overview
MyToken is an ERC-20 compatible token built on Ethereum for learning purposes.  
It demonstrates token transfers, approvals, allowances, and event logging.

---

## Token Details
- **Name:** MyToken  
- **Symbol:** MTK  
- **Decimals:** 18  
- **Total Supply:** 1,000,000 MTK  

---

## Features
- ERC-20 standard functions  
- Transfer tokens  
- Approve spending  
- Spend via transferFrom  
- Emits Transfer & Approval events  
- Uses mappings for balances & allowances  

---

# 🔧 How to Deploy (Remix IDE)

1. Open Remix IDE  
2. Create file: `MyToken.sol`  
3. Paste the ERC-20 code  
4. Compile using Solidity 0.8.x  
5. Go to Deploy & Run  
6. Environment: **Remix VM (Prague)**  
7. Enter constructor value: **1000000**  
8. Click **Deploy**  

Your token is deployed.

---

# 📘 How to Use the Token  
Below are **separate clean blocks** explaining each ERC-20 function:

---

# 1️⃣ Check Balance  
### Function: `balanceOf(address account)`

Returns how many tokens an address owns.

#### Example

balanceOf(0x5B38...) → 1000000

2️⃣ Transfer Tokens
Function: transfer(address to, uint256 amount)

Sends tokens from the sender to another address.

Example
transfer(0xAb84..., 100)

Result

Sender balance → decreases by 100

Receiver balance → increases by 100

A Transfer event is emitted

Transfer will fail if:

Sender does not have enough balance

Receiver is the zero address

3️⃣ Approve Spending
Function: approve(address spender, uint256 amount)

Lets another address spend up to a specified number of tokens from your wallet.

Example
approve(0xAb84..., 50)


Meaning:
The spender can spend 50 MTK on your behalf.

Allowances stored as:

mapping(address => mapping(address => uint256)) public allowance;

Example check:
allowance(Owner, Spender) → 50

4️⃣ Spend Approved Tokens
Function: transferFrom(address from, address to, uint256 amount)

Allows the spender to transfer tokens from the owner using the approved amount.

Example Workflow

Owner approves:

approve(Spender, 50)


Spender transfers:

transferFrom(Owner, Receiver, 20)

Result

Owner balance → decreases by 20

Receiver balance → increases by 20

Allowance → 50 → 30

A Transfer event is emitted

transferFrom will fail if:

Allowance < amount

Owner does not have enough balance

This is how exchanges and DeFi apps move tokens automatically.
