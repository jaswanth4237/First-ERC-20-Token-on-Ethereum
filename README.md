# First-ERC-20-Token-on-Ethereum

1. Introduction
This project demonstrates the creation and testing of a custom ERC-20 token using Solidity and Remix IDE.
The token supports all essential ERC-20 functions:

totalSupply

balanceOf

transfer

approve

allowance

transferFrom

All tests were performed using Remix VM (Prague).

2. Token Details
Property	Value
Name	MyToken
Symbol	MTK
Decimals	18
Total Supply	1,000,000 MTK
Network	Remix VM

4. Project Files

├── MyToken.sol        # ERC-20 Contract
├── README.md          # Documentation
└── screenshots/       # All required screenshots

5. How to Compile
Open Remix IDE

Create file MyToken.sol

Paste contract code

Select compiler version 0.8.x

Click Compile MyToken.sol

5. How to Deploy
Go to Deploy & Run Transactions

Choose environment Remix VM (Prague)

Select contract MyToken

Enter constructor value:

1000000

Click Deploy

6. Functional Testing
✔ Transfer Test

Sent tokens between accounts using:

transfer(to, value)


Balances updated correctly.

(Screenshot in /screenshots)

✔ Approve Test
approve(spender, 50)


Allowance correctly set to 50.

(Screenshot in /screenshots)

✔ transferFrom Test
transferFrom(owner, receiver, 20)


Spender successfully transferred 20 tokens on behalf of the owner.
Allowance reduced from 50 → 30.

(Screenshot in /screenshots)

7. Edge Case Testing
Test	Result
Transfer to zero address	❌ Failed (correct behavior)
Transfer more than balance	❌ Failed (correct)
transferFrom without approval	❌ Failed (correct)

(Screenshots in /screenshots)

8. Events Generated

The following events were successfully emitted:

Transfer

Approval

(Screenshot in /screenshots)

9. Conclusion

This project fulfills all requirements for building and testing an ERC-20 token, including:

Contract creation

Deployment

Token transfers

Spending authorization (approve + transferFrom)

Handling error cases correctly

Documenting results with screenshots
