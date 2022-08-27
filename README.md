# Flash Loans

![image](https://user-images.githubusercontent.com/102557215/187034729-0a1366eb-bb73-42e9-8af6-2057fcc4d31f.png)

## What are Flash Loans?
### Flash loans are smart contracts. This is a feature of blockchain technology that prevents funds from leaving one account to the other unless certain obligations have been fulfilled. When a flash loan has been issued, the smart contract rules ensure that the borrower pays back the loan before the transaction ends.


## How do Flash Loans Works?

There are 4 basic steps to any flash loan. To execute a flash loan, you first need to write a smart contract that has a transaction that uses a flash loan. Assume the function is called createFlashLoan(). The following 4 steps happen when you call that function, in order:

- Your contract calls a function on a Flash Loan provider, like Aave, indicating which asset you want and how much of it
- The Flash Loan provider sends the assets to your contract, and calls back into your contract for a different function, executeOperation
- executeOperation is all custom code you must have written - you go wild with the money here. At the end, you approve the Flash Loan provider to withdraw back the         borrowed assets, along with a premium
- The Flash Loan provider takes back the assets it gave you, along with the premium.

![image](https://user-images.githubusercontent.com/102557215/187034877-d47ccef0-560e-4123-92fb-fb9f29c4f966.png)

If you look at this diagram, you can see how a flash loan helped the user make a profit in an arbitrage trade. Initially the user started a transaction by calling lets say a method createFlashLoan in your contract which is named as FlashLoan Contract. When the user calls this function, your contract calls the Pool Contract which exposes the liquidity management methods for a given pool of assets and has already been deployed by Aave. When the Pool Contract receives a request to create a flash loan, it calls the executeOperation method on your contract with the DAI in the amount user has requested. Note that the user didn't have to provide any collateral to get the DAI, he just had to call the transaction and that Pool Contract requires you to have the executeOperation method for it to send you the DAI.


## Libraries 

- Openzepplin Contracts
- Aave/Core v3 Contracts
