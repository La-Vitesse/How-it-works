# How-it-works
Explains the mechanism behind La Vitesse

La-Vyf (La Vitesse Yield Farming) Protocol
La-Vyf Protocol is designed as a special uncollateralised loan contract that allows the borrowing of an asset, as long as the borrowed amount (and a fee) is returned before the end of the transaction. The essence of this technology is speed.
This Protocol is a developers oriented feature that allow to borrow any available amount of assets without collateral. For this to happen, the borrowing trader is required to build a contract that will request a La-Vyf contract through the La-Vyf Protocol, take the required actions and pay back the loan + interest and fees in the same transaction.

For a simple understanding of how La-Vyf Protocol functions:
1.	The borrowing trader’s contract calls our La-Vyf contract, requesting a loan of a certain amount of a reserve.
2.	After some sanity checks, our La-Vyf Protocol transfers the requested amount of the reserve from our LiquidityVault to the trader’s contract, then calls executeOperation() on the trader’s contract (or another contract that is specified as the _receiver).
3.	The trader’s contract, now holding the loan amount, executes any arbitrary operation in its code. When the code has finished, the trader transfers the loaned amount of reserve back to our LiquidityVault.
4.	Our La-Vyf contract compares the balance of the reserve before and after the code execution, ensuring that the balance of the reserve is exactly the same as before plus the loan fee. 
o	If the balance of the reserve before and after the code execution is correct, then the La-Vyf Protocol function continues to completion.
o	If the balance of the reserve after the code execution is incorrect, then the function reverts, undoing any state changes the contract made.
5.	All of the above happens in 1 transaction (hence in a single block).
 

La-Vyf Protocol is an advanced technology aimed at developers, and an innovative service provided for traders. 
It is necessary to have a good understanding of programming and smart contracts to take advantage of them.

La-Vyf Protocol is able to satisfy the DeFi community by providing the three novel properties absent in centralized financial economies:

•	No debt default risk: As a La Vitesse yield farmer offering a loan through the La-Vyf Protocol, the transaction bears no risk that the borrower defaults on its debt. Because a transaction and its instructions must be executed atomically, the loan will not be granted if the transaction fails due to a debt default. 

•	No need for collateral: And because as a La Vitesse yield farmer is guaranteed to be paid back, the protocol can issue credit without upfront collateral from the borrower because the blockchain transaction can be reverted during its execution if the condition of a repayment is not satisfied.

•	Loan size: The protocol safely allows the borrower to borrow from the smallest of 100 USDT up to the entire liquidity vault at any point in time. 
These has provided traders who are actively going around performing arbitrage on different DEX, without the need to hold a monetary position or being exposed to volatility risks. The trader can simply open a loan through the La-Vyf contract, perform an arbitrage trade and pay back the loan plus interests.  

What happens if the La-Vyf contract is not returned?

If this does not happen, the whole transaction is reversed to effectively undo the actions executed until that point. This guarantees the safety of the funds in the liquidity vault. Use-cases include arbitrage, collateral swapping, self-liquidation, and many more.

Advantages of La-Vyf Protocol for borrowers and lenders.

Safeguarding the parameters of the La-Vyf contracts, the Protocol ensures the loans are paid back quickly – in the same transaction in which they are taken out.
Arbitrageurs can turn a quick profit by borrowing funds; buying low on one market; selling high on the other market; repaying the loan; and pocketing the profit. This can be done within the same on-chain transaction, since the markets are DEXs often running on ethereum.

The fee for both borrowers and lenders is decided algorithmically:
For borrowers, it depends on the cost of money - the amount of funds available in the liquidity vault at a specific time.
For lenders, this interest rate corresponds to the earn rate, with the La-Vyf Protocol safeguarding a liquidity reserve to guarantee withdrawals at any time.
As funds are borrowed from the liquidity vault, the amount of funds available decreases which raises the interest rate. 

In a nutshell, La-Vyf Protocol operates nearly risk-free. Since the ethereum network settles transactions automatically, the borrower who cannot pay back the loan with his trade loses nothing, the lender will still have the asset deposited under La-Vyf contract in the liquidity vault.
