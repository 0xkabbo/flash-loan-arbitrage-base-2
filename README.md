# Flash Loan Arbitrage Base (Aave V3)

This repository provides a professional-grade boilerplate for interacting with Aave V3 Flash Loans. It allows you to borrow millions in liquidity, execute custom logic, and repay the loan in a single transaction.

### How it Works
1. **Request:** The contract calls `flashLoanSimple` on the Aave Pool.
2. **Execute:** Aave sends the funds to this contract and calls the `executeOperation` callback.
3. **Arbitrage:** You implement your logic (e.g., Uniswap vs. Sushiswap price discrepancy) inside the callback.
4. **Repay:** The contract automatically approves Aave to pull the principal plus the flash loan fee (0.05%).

### Safety Features
* **Strict Callback:** Only the official Aave Pool can trigger the execution function.
* **Transaction Reversion:** If the arbitrage profit doesn't cover the fee, the entire transaction reverts, ensuring you never lose your own capital (minus gas).
* **Owner Withdrawals:** Secure functions to withdraw accumulated profits in any ERC-20 token.

### Requirements
* Alchemy/Infura RPC for Mainnet Forking.
* Test tokens for gas (e.g., Sepolia ETH).
