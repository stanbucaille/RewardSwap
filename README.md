# rewardswap-web-app

## I. Description of the smart contract

**Smart contract**: Token

**Inheritance**: ERC20

### 1. State variables 

- **__symbol** (constant): symbol of the token
- **__name** (constant): name of the restaurant
- **__owner** (constant): account address of the restaurant
- **__discount** (variable): the reward token value represents the discount in % that restaurant is willing to give out to each customer when they spend $1 
  - example: if the __discount is 20, then each token is worth $0.20
- **decimals** (constant): the granularity allowed to split a token
- **__totalSupply** (variable): total number of token

### 2. Mapping

- **__balanceOf**: number of token that belongs to a given address

### 3. Modifiers 

- **isOwner**: this modifier is required in order to ensure that only the owner of the contract (the restaurant) is able to achieve certain tasks. In particular, it will be used in the mint and setDiscount functions.


### 4. Constructor

- **Constructor**: we deploy a new Token contract for each restaurant. We need to precise the owner of the contract (the account address of the restaurant), as well as the symbol and the name of the token. By default, the discount is set to 20%, but can be changed if needed.


### 5.Functions

- **setDiscount**: this function enables the restaurant (owner of the contract) to modify the discount it is willing to make for its customers 

- **totalSupply**: this function enables to get the total amount of tokens present in the ecosystem

- **balanceOf**: this function enables anyone to see the number of tokens held in a given account address.

- **mint**: this function enables the restaurant to mint new tokens. We can see that we used the modifier isOwner for security purposes to make sure that the restaurant (owner of the contract) is the only address able to mint new tokens.

- **transfer**: this function enables any address to send tokens to another address.

- **giveReward**: this function enables restaurants to reward customers with tokens whenever customers make a payment in cash. Customers will receive N tokens for N dollars spent in cash. In order to give rewards to customers, the restaurant needs to first mint the number of tokens it wants to give out, then transfer these tokens to the customer account.

- **redeemReward**: this function enables customers to use their tokens in order to get a discounted price. If the customer has enough tokens to make the full payment, he will use them and the discounted price will be 0. Otherwise, the customer will have to use all of its token to pay a part of the price that will be discounted on the original price to return the new discounted price.

## II. Deploy smart contract

The smart contract can be deployed using Remix : http://remix.ethereum.org/

Follow these steps:

- upload the **contract_RewardToken.sol** on Remix
- compile the smart contract using the compiler **0.6.12+commit27D51765**
- deploy the smart contract:
  - Network: **Rinkeby**
  - Environment: **Inject Web3**
  - Inputs: 
    - _adress : account adress of the owner of the contract (the restaurant)
    - name: name of the restaurant
    - symbol: symbol of the token
- go on Etherscan and click **Verify and Publish** to verify the contract
- click on the adress of the contract and go on **Read Contract** and **Write Contract** to interact with the contract

