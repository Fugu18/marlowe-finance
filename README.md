# marlowe-finance
Modular Marlowe for DeFi primitives, finance and trading use cases.

We follow the journey of the **Citizen Developer** to learn how Cardano's Domain Specific Language [Marlowe](https://marlowe.iohk.io/) can be used to safely and simply deploy financial smart contracts to the blockchain.

*Web3 User Journey*
A DApp user who fulfills their role as a participant in a contract transaction. Connects their wallet to a specific DApp. 

*Contract designer journey*
A developer working with code and the Marlowe DSL language. Uses the Playground to test, iterate, and refine the contract design. May reference contract examples found in places like the Marlowe starter kit and Marlowe Github repository.

*DApp developer journey*
A developer working with code and the Marlowe DSL language. Uses developer tools such as the prototype example DApps and TS-SDK. The prototype examples offer guidance on ways to implement DApp functionality.

*Builder (citizen developer) journey*
A business owner or entrepreneur who is managing a team of developers to build smart contracts and DApps. Lines up all the pieces to make a project happen. Needs to understand the big picture.

There are three paths to start if one does not want to start from scratch. ACTUS is the [Algorithmic Contract Types Unified Standards organization](https://www.actusfrf.org/) and provides a useful but complex scaffolding for financial contract standardization that is years ahead of the current sophistication of Decentralized Finance. Templates and Libraries exist from Catalyst funding and open source contribution. The official Real World Marlowe looks at sample contracts of which the ten most important are featured here.

(1) NFT/FT sale for ADA
A Simple Sale of a Token
The simplest token sale is the exchange of a token for Ada.
This example consists of five transactions:
    1. Christopher Marlowe creates the token-sale Marlowe contract.
    2. Christopher Marlowe deposits 1 BearGarden token in the contract.
    3. Jane Lumley deposits 50 Ada in the contract, causing the contract to pay the token to her and the Ada to Christopher Marlowe.
    4. Christopher Marlowe withdraws his 50 Ada from Marlowe's role-payout address.
    5. Jane Lumley withdraws her 1 BearGarden from Marlowe' role-payout address.

(2) NFT/FT sale for Stablecoin
This token sale exchanges a token for either the Djed or iUSD stablecoins.
This example consists of five transactions:
    1. Christopher Marlowe creates the token-sale Marlowe contract.
    2. Christopher Marlowe deposits 1 BearGarden token in the contract.
    3. Jane Lumley deposits 50 Djed in the contract, causing the contract to pay the token to her and the Djed to Christopher Marlowe.
    4. Christopher Marlowe withdraws his 50 Djed from Marlowe's role-payout address.
    5. Jane Lumley withdraws her 1 BearGarden from Marlowe' role-payout address.

(3) NFT/FT Sale of a Token with Royalties
This token sale exchanges a token for either the iUSD stablecoins and pays a royalty to the NFT artist. See CIP-27 for more information about NFT royalties in Cardano.
This example consists of six transactions:
    1. Christopher Marlowe creates the token-sale Marlowe contract.
    2. Christopher Marlowe deposits 1 BearGarden token in the contract.
    3. Jane Lumley deposits 50.175 iUSD in the contract, causing the contract to pay the token to her and iUSD to Christopher Marlowe and the artist Elizabeth Cary.
    4. Christopher Marlowe withdraws his 50 iUSD from Marlowe's role-payout address.
    5. Jane Lumley withdraws her 1 BearGarden from Marlowe's role-payout address.
    6. Elizabeth Cary withdraws her 0.175 iUSD royalty from Marlowe's role-payout address.

(4) Swap of tokens
This contract swaps one type of token for another.
This example consists of four transactions:
    1. Francis Beaumont creates the token-sale Marlowe contract.
    2. Francis Beaumont deposits 500 Globe tokens in the contract.
    3. John Webster deposits 300 Swan tokens in the contract, causing it to close and pay the tokens for the benefit of the other parties.
    4. Francis Beaumeont withdraws his 300 Swan tokens from Marlowe's role-payout address.
    5. John Webster withdraws his 500 Globe tokens from Marlowe's role-payout address.

(5) Airdrop of token
This mini-airdrop of tokens to five parties illustrates the difficulties of making multiple payments in the same Marlowe transaction: the limit on Plutus execution costs forces the five payments to be split into two transactions.
This example consists of nine transactions:
    1. Christopher Marlowe creates the airdrop Marlowe contract.
    2. Christopher Marlowe deposits 500 BearGarden token in the contract.
    3. After ten minutes, Christopher Marlowe notifies the contact to pay out the first batch of tokens.
    4. In a second notification, Christopher Marlowe notifies the contract to pay out the remaining tokens.
    5. Francis Beaumont withdraws his 100 BearGarden tokens from the Marlowe payout address.
    6. Elizabeth Cary withdraws her 100 BearGarden tokens from the Marlowe payout address.
    7. Mary Herbert withdraws her 100 BearGarden tokens from the Marlowe payout address.
    8. Jane Lumley withdraws her 100 BearGarden tokens from the Marlowe payout address.
    9. John Webster withdraws his 100 BearGarden tokens from the Marlowe payout address.

(6) NFT Shared Ownership
Shared Purchase of an NFT, with an Option to Buy Out Other Co-Owners
Three parties contribute equal amounts towards the purchase of a NFT that they jointly own. At any time, one of them may pay the other two the value of the token so that they can have the token all for themselves.

  1. Elizabeth Cary deposits 100 Ada into the contract.
  2. Jane Lumely deposits 100 Ada into the contract.
  3. Mary Herbert deposits 100 Ada into the contract.
  4. Christopher Marlowe deposits 1 BearGarden token into the contract, causing it to pay 300 Ada for his benefit.
  5. Christopher Marlowe withdraws the 300 Ada from the role-payout address.
  6. Later, Mary Herbert deposits 300 Ada into the contract so she can have the token all for herself; this causes 150 Ada each for Elizabeth Cary and Jane Lumley to be paid for their behalves.
  7. Elizabeth Cary withdraws 150 Ada from the Marlowe payout address.
  8. Jane Lumley withdraws 150 Ada from the Marlowe payout address.
  9. Mary Herbert withdraws 1 BearGarden tokens from the Marlowe payout address.


(7) NFT/FT Loan Collateral
A Bullet Loan with an NFT as Collateral
The party borrows 90 Djed with a BearGarden token as collateral; after they pay back the 90 Djed principal and 10 Djed interest to the counterparty, they receive their BearGarden token back. If they do not pay before the deadline, the counterparty keeps their BearGarden token.

This example consists of seven transactions:

  1. Elizabeth Cary creates the token-sale Marlowe contract.
  2. Elizabeth Cary deposits 1 BearGarden token in the contract.
  3. Mary Herbet deposits 90 Djed in the contract, causing the contract to loan the 90 Djed to Elizabeth Cary.
  4. Elizabeth Cary withdraws her 90 Djed from Marlowe's role-payout address.
  5. Later, Elizabeth Cary deposits 100 Djed into the contract, which returns her token and pays the 100 Djed to Mary Herbert.
  6. Elizabeth Cary withdraws her 1 BearGarden token from Marlowe's role-payout address.
  7. Mary Herbet withdraws her 100 Djed from Marlowe's role-payout address.


(8) NFT/FT Pawn for stablecoin
Pawning an NFT for iUSD
The party receives 100 iUSD for pawning a BearGarden token as collateral; if they pay back the 100 iUSD, they receive their BearGarden token back. However, at any time before such a redemption, the counterparty may decide to keep the BearGarden token.

This example consists of six transactions:

1. Elizabeth Cary creates the token-sale Marlowe contract.
2. Elizabeth Cary deposits 1 BearGarden token in the contract.
3. Mary Herbet deposits iUSD Djed in the contract, causing the contract to pay the 100 iUSD to the role-payout address for Elizabeth Cary.
4. Elizabeth Cary withdraws her 100 iUSD from Marlowe's role-payout address.
5. Later, Mary Herbert chooses to have the token withdrawn from the contract, depriving Elizabeth Cary of the chance to repay the 100 iUSD and receive her token back.
6. Mary Herbert withdraws her 1 BearGarden token from Marlowe's role-payout address.


(9) Token Sale with Oracle
This token sale uses a price oracle to set the cost of the tokens.
This example consists of six transactions:
    1. John Webster creates the token-sale Marlowe contract.
    2. John Webster deposits 1,000,000 HOSKY tokens in the contract.
    3. The price oracle reports the exchange rate of 1 ADA = 11074197 HOSKY.
    4. Elizabeth Cary deposits 90,300 lovelace in the contract, causing the contract to pay the token to her and the Ada to John Webster.
    5. John Webster withdraws his lovelace from Marlowe's role-payout address.
    6. Elizabeth withdraws her 1,000,000 HOSKY from Marlowe' role-payout address.


(10) English Auction
This English Auction with five bidders and three rounds of bidding demonstrates the use of merkleization for Marlowe contracts. Because bidders may bid in any order and may bid more than once, unless they are disqualified by an illegal bid or timeout, the contract involves a combinatorial explosion of possibilities. Without merkleization, the contract JSON file is 990MB in size and contains 940k Case statements, but after merkleization the JSON file is 9.8MB and it contains just 1150 merkleized Case statements.

Characteristic of this contract

A seller auctions one unit of an asset.
Any number of bidders bid on the contract.
Bids may occur in any order.
There are a fixed number of bids (rounds of bidding) allowed.
A bid is rejected if it isn't higher than all previous bids.
A bid is rejected if it isn't immediately followed by a deposit of the Lovelace that was bid.
Funds are returned to unsuccessful bidders.
There is deadline for depositing the asset.
Each bidding round has a deadline.
