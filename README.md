# Marlowe for Finance

Modular Marlowe for DeFi primitives, finance and trading use cases.

This repository contains code snippets, background information and files for the educational series Marlowe for Finance. The series covers the use of Cardano's Domain Specific Language *MARLOWE* for non-technical financial users for whom the DSL was originally intended for. As Marlowe is transitioning to an easy and more secure Special Purpose Language for the development of decentralized Apps, we also cover the latest tools and future plans for example Typescript capabilities, Oracle integration and micropayments, as they are very useful for financial applications as well and expand or simplify functionality for the target user.

**Marlowe is now a fully community-led project**

*Special Interest Group:* [Github](https://github.com/marlowe-foundation/org/blob/main/sig-charter.md)

*Fortnightly Call:* [Discord Link](https://discord.com/events/826816523368005654/1316801221604016158)

*Governed by:* [**MARLOWE LANGUAGE CIC**](https://find-and-update.company-information.service.gov.uk/company/16010921)

### Purpose of Marlowe for Finance

We follow the journey of the **Citizen Developer** to learn how Cardano's Domain Specific Language [Marlowe](https://marlowe.iohk.io/) can be used to safely and simply deploy financial smart contracts to the blockchain.

![CD](https://github.com/Fugu18/marlowe-finance/blob/main/images/citizen-developer.png)

*Web3 User Journey*
A DApp user who fulfills their role as a participant in a contract transaction. Connects their wallet to a specific DApp. 

*Contract designer journey*
A developer working with code and the Marlowe DSL language. Uses the Playground to test, iterate, and refine the contract design. May reference contract examples found in places like the Marlowe starter kit and Marlowe Github repository.

*DApp developer journey*
A developer working with code and the Marlowe DSL language. Uses developer tools such as the prototype example DApps and TS-SDK. The prototype examples offer guidance on ways to implement DApp functionality.

**Builder (citizen developer) journey:
A business owner or entrepreneur who is managing a team of developers to build smart contracts and DApps. 
Lines up all the pieces to make a project happen. 
Needs to understand the big picture.**

There are three paths to start if one does not want to start from scratch. ACTUS is the [Algorithmic Contract Types Unified Standards organization](https://www.actusfrf.org/) and provides a useful but complex scaffolding for financial contract standardization that is years ahead of the current sophistication of Decentralized Finance. Templates and Libraries exist from Catalyst funding and open source contribution. The official Marlowe Playground and Real World Marlowe Repository both look at sample contracts. This is a good place to start.

## Mission
It is important to me that DeFi projects migrating from other blockchains and traditional finance can easily understand and deploy Marlowe for their projects. [Marlowe 2025](https://projectcatalyst.io/funds/13/f13-cardano-use-cases-concept/marlowe-2025-marlowe-v2) was funded in Catalyst Fund-13 and this will start the exciting new "V2" phase of Marlowe as an easy-to-deploy Domain Specific Language. Existing Catalyst community projects from previous funds and their compatibility with the Marlowe 2025 stack will be introduced and discussed as well.

***

## Overview of Contents

### Introduction to Cardano and Marlowe within it
Cardano's architecture offers unique advantages for decentralized applications, including deterministic transactions, predictable fees, and its robust Extended UTXO model. However, developing smart contracts on Cardano has traditionally required specialized knowledge. This is where Marlowe comes in - a domain-specific language (DSL) that makes financial smart contract development more accessible, especially for developers coming from traditional web backgrounds. For those developers and founders familiar with React and web development, Marlowe offers several compelling advantages:

* Familiar Development Model: While Cardano uses a UTXO model (different from Ethereum's account-based system), Marlowe abstracts this complexity away, providing a more familiar account-based model that web developers will find intuitive.
* TypeScript Integration: Marlowe offers a TypeScript SDK that integrates seamlessly with modern web frameworks, allowing you to build end-to-end DApps using familiar tools and REST APIs.
* Built-in Safety Guarantees: Unlike general-purpose smart contract languages, Marlowe's domain-specific nature allows it to provide inherent safety guarantees. For example, it ensures that assets won't be trapped indefinitely in contracts - a common concern in blockchain development.


Marlowe takes advantage of Cardano's unique features while adding its own benefits. Cardano's deterministic transaction model means it is possible to predict exactly how smart contracts will behave. When combined with Marlowe's high-level abstractions, this makes contract development more reliable. Marlowe builds on this by optimizing contract execution for efficiency. Marlowe provides tools to analyze contracts for potential issues before deployment - a crucial feature for financial applications where bugs can be costly. Marlowe is particularly well-suited for financial applications such as:

* Escrow services with automated dispute resolution
* Token swaps with built-in safety checks
* Payment channels for micro-transactions
* Oracle-based financial contracts

Getting Started
For React developers looking to enter blockchain development, Marlowe offers perhaps the lowest barrier to entry on Cardano. You can start with:

The TypeScript SDK for familiar development patterns
The Runtime service for handling on-chain interactions
Pre-built contract templates for common financial use cases


### Marlowe teasers, syntax and Playground
Covers what new users can expect from a Cardano DSL and Marlowe in particular, with Google Blockly visual programming editor making code creation inside Marlowe Playground extremely easy and safe. We look at the types of constructs (blocks) available, how they translate back and forth into Marlowe synatx or JSON, how to simulate your newly created smart contracts, and what this means for use cases.

### Dependencies, Requirements and Setup
We look at the possible user setups and installations recommended for deploying on Cardano, taking advantage of plug-and-play infrastructure or running our own node.

### Building FinTx DApps with Marlowe
As our focus is Marlowe for Finance, we spend some time establishing the framework for building financial applications with Marlowe. Despite it's recent shift to dApp development in general, the DSL was originally intended to limit itself to financial contracts and excel at those. Roles, currencies, timeouts and the account model make building with Marlowe a lot easier on Cardano, as long as we stick to what the language was intended for in the first place.

### Overview of Financial Products and DeFi
After a solid understanding of the basics has been established, we survey the worlds of Decentralized Finance and TradFi, and see where innovation, underserved customers and Marlowe's particular strengths create ideal condition for projects using Marlowe. Contains theory about financial derivatives and popular DeFi ideas, trading and fintech decentralized applications. We also discuss some forward-looking and novel use cases and more sophisticated financial contracts and how they could add value to the Cardano ecosystem.

### Deploying FinTx on Cardano with Marlowe
This section combines the foundational information and theory into practical advice and examples how Marlowe can be used to simplify financial interactions on Cardano. This also examines existing resources from previous Catalyst funding projects and contributions from IOG Marlowe team members to open source repositories, such as JSON-format code snippets, sample code and ACTUS financial contracts as code.

***

## Getting Started
What is really nice about Marlowe is its use of Blockly and the [Marlowe Playground](https://playground.marlowe-lang.org/#/) interactive coding and simulation web environment. Some example contracts exist that can be shown as either Blockly blocks (each representing an "operation"), native Marlowe script or JSON. This is a great starting point to gain an intuitive understanding of how Marlowe works and what kind of guarantees it provides compared to writing smart contracts from scratch.

~~~
When
    [Case
        (Deposit
            (Role "Lender")
            (Role "Lender")
            (Token "" "")
            (ConstantParam "Amount")
        )
        (Pay
            (Role "Lender")
            (Party (Role "Borrower"))
            (Token "" "")
            (ConstantParam "Amount")
            (When
                [Case
                    (Deposit
                        (Role "Borrower")
                        (Role "Borrower")
                        (Token "" "")
                        (AddValue
                            (ConstantParam "Interest")
                            (ConstantParam "Amount")
                        )
                    )
                    (Pay
                        (Role "Borrower")
                        (Party (Role "Lender"))
                        (Token "" "")
                        (AddValue
                            (ConstantParam "Interest")
                            (ConstantParam "Amount")
                        )
                        Close 
                    )]
                (TimeParam "Payback deadline")
                Close 
            )
        )]
    (TimeParam "Loan deadline")
    Close
~~~

This can easily be toggled back and forth into blocks, which look like this:

![ZCB](https://github.com/Fugu18/marlowe-finance/blob/main/images/ZCB.png)

Which can be sent to Simulation or exported as the following JSON:

~~~
{"when":[{"then":{"token":{"token_name":"","currency_symbol":""},"to":{"party":{"role_token":"Borrower"}},"then":{"when":[{"then":{"token":{"token_name":"","currency_symbol":""},"to":{"party":{"role_token":"Lender"}},"then":"close","pay":{"and":0,"add":0},"from_account":{"role_token":"Borrower"}},"case":{"party":{"role_token":"Borrower"},"of_token":{"token_name":"","currency_symbol":""},"into_account":{"role_token":"Borrower"},"deposits":{"and":0,"add":0}}}],"timeout_continuation":"close","timeout":1735584415483},"pay":0,"from_account":{"role_token":"Lender"}},"case":{"party":{"role_token":"Lender"},"of_token":{"token_name":"","currency_symbol":""},"into_account":{"role_token":"Lender"},"deposits":0}}],"timeout_continuation":"close","timeout":1735582615483}
~~~

with slightly different syntax from the original Marlowe, intended for deployment with JS or TS.


# Marlowe Playground with Examples

### (A) Escrow
Regulates a money exchange between a "Buyer" and a "Seller". If there is a disagreement, a "Mediator" will decide whether the money is refunded or paid to the "Seller".

[Escrow as Marlowe](https://github.com/Fugu18/marlowe-finance/blob/main/marlowe/escrow.marlowe)

### (B) Escrow with Collateral
Regulates a money exchange between a "Buyer" and a "Seller" using a collateral from both parties to incentivize collaboration. If there is a disagreement the collateral is burned.
[Escrow with Collateral as Marlowe](https://github.com/Fugu18/marlowe-finance/blob/main/marlowe/escrow_collateral.marlowe)

### (C) Zero Coupon Bond
A simple loan. The investor pays the issuer the discounted price at the start, and is repaid the full (notional) price at the end.

[Zero Coupon Bond as Marlowe](https://github.com/Fugu18/marlowe-finance/blob/main/marlowe/zcbond.marlowe)

### (D) Coupon Bond Guaranteed
Debt agreement between an "Lender" and an "Borrower". "Lender" will advance the "Principal" amount at the beginning of the contract, and the "Borrower" will pay back "Interest instalment" every 30 slots and the "Principal" amount by the end of 3 instalments. The debt is backed by a collateral provided by the "Guarantor" which will be refunded as long as the "Borrower" pays back on time.

[Coupon Bond Guaranteed as Marlowe](https://github.com/Fugu18/marlowe-finance/blob/main/marlowe/guaranteed_bond.marlowe)

### (E) Dollar Swap
Takes Ada from one party and dollar tokens from another party, and it swaps them atomically.

[Dollar Swap as Marlowe](https://github.com/Fugu18/marlowe-finance/blob/main/marlowe/swap.marlowe)

### (F) Contract for Differences
"Party" and "Counterparty" deposit 100 Ada and after 60 slots is redistributed depending on the change in a given trade price reported by "Oracle". If the price increases, the difference goes to "Counterparty"; if it decreases, the difference goes to "Party", up to a maximum of 100 Ada.

[CFD as Marlowe](https://github.com/Fugu18/marlowe-finance/blob/main/marlowe/cfd.marlowe)

### (G) CFD with Oracle
"Party" and "Counterparty" deposit 100 Ada and after 60 slots these assets are redistributed depending on the change in price of 100 Ada worth of dollars between the start and the end of the contract. If the price increases, the difference goes to "Counterparty"; if it decreases, the difference goes to "Party", up to a maximum of 100 Ada.

[CFD with Oracle as Marlowe](https://github.com/Fugu18/marlowe-finance/blob/main/marlowe/cfd_oracle.marlowe)


## Real World Marlowe

### (1) NFT/FT sale for ADA
A Simple Sale of a Token
The simplest token sale is the exchange of a token for Ada.
This example consists of five transactions:
+ Christopher Marlowe creates the token-sale Marlowe contract.
+ Christopher Marlowe deposits 1 BearGarden token in the contract.
+ Jane Lumley deposits 50 Ada in the contract, causing the contract to pay the token to her and the Ada to Christopher Marlowe.
+ Christopher Marlowe withdraws his 50 Ada from Marlowe's role-payout address.
+ Jane Lumley withdraws her 1 BearGarden from Marlowe' role-payout address.

![Sale4Ada](https://github.com/Fugu18/marlowe-finance/blob/main/images/NFT%20sale%20of%20token%20for%20ada.png)


### (2) NFT/FT sale for Stablecoin
This token sale exchanges a token for either the Djed or iUSD stablecoins.
This example consists of five transactions:
+ Christopher Marlowe creates the token-sale Marlowe contract.
+ Christopher Marlowe deposits 1 BearGarden token in the contract.
+ Jane Lumley deposits 50 Djed in the contract, causing the contract to pay the token to her and the Djed to Christopher Marlowe.
+ Christopher Marlowe withdraws his 50 Djed from Marlowe's role-payout address.
+ Jane Lumley withdraws her 1 BearGarden from Marlowe' role-payout address.

![Sale4Stablecoin](https://github.com/Fugu18/marlowe-finance/blob/main/images/NFT%20sale%20of%20token%20for%20stablecoin.png)


### (3) NFT/FT Sale of a Token with Royalties
This token sale exchanges a token for either the iUSD stablecoins and pays a royalty to the NFT artist. See CIP-27 for more information about NFT royalties in Cardano.
This example consists of six transactions:
+ Christopher Marlowe creates the token-sale Marlowe contract.
+ Christopher Marlowe deposits 1 BearGarden token in the contract.
+ Jane Lumley deposits 50.175 iUSD in the contract, causing the contract to pay the token to her and iUSD to Christopher Marlowe and the artist Elizabeth Cary.
+ Christopher Marlowe withdraws his 50 iUSD from Marlowe's role-payout address.
+ Jane Lumley withdraws her 1 BearGarden from Marlowe's role-payout address.
+ Elizabeth Cary withdraws her 0.175 iUSD royalty from Marlowe's role-payout address.

![SaleRoyalties](https://github.com/Fugu18/marlowe-finance/blob/main/images/NFT%20sale%20of%20token%20with%20royalties.png)


### (4) Swap of tokens
This contract swaps one type of token for another.
This example consists of four transactions:
+ Francis Beaumont creates the token-sale Marlowe contract.
+ Francis Beaumont deposits 500 Globe tokens in the contract.
+ John Webster deposits 300 Swan tokens in the contract, causing it to close and pay the tokens for the benefit of the other parties.
+ Francis Beaumeont withdraws his 300 Swan tokens from Marlowe's role-payout address.
+ John Webster withdraws his 500 Globe tokens from Marlowe's role-payout address.

![Tokenswap](https://github.com/Fugu18/marlowe-finance/blob/main/images/NFT%20swap%20of%20tokens.png)


### (5) Airdrop of token
This mini-airdrop of tokens to five parties illustrates the difficulties of making multiple payments in the same Marlowe transaction: the limit on Plutus execution costs forces the five payments to be split into two transactions.
This example consists of nine transactions:
+ Christopher Marlowe creates the airdrop Marlowe contract.
+ Christopher Marlowe deposits 500 BearGarden token in the contract.
+ After ten minutes, Christopher Marlowe notifies the contact to pay out the first batch of tokens.
+ In a second notification, Christopher Marlowe notifies the contract to pay out the remaining tokens.
+ Francis Beaumont withdraws his 100 BearGarden tokens from the Marlowe payout address.
+ Elizabeth Cary withdraws her 100 BearGarden tokens from the Marlowe payout address.
+ Mary Herbert withdraws her 100 BearGarden tokens from the Marlowe payout address.
+ Jane Lumley withdraws her 100 BearGarden tokens from the Marlowe payout address.
+ John Webster withdraws his 100 BearGarden tokens from the Marlowe payout address.

![Airdrop](https://github.com/Fugu18/marlowe-finance/blob/main/images/Token%20airdrop.png)


### (6) NFT Shared Ownership
Shared Purchase of an NFT, with an Option to Buy Out Other Co-Owners
Three parties contribute equal amounts towards the purchase of a NFT that they jointly own. At any time, one of them may pay the other two the value of the token so that they can have the token all for themselves.

+ Elizabeth Cary deposits 100 Ada into the contract.
+ Jane Lumely deposits 100 Ada into the contract.
+ Mary Herbert deposits 100 Ada into the contract.
+ Christopher Marlowe deposits 1 BearGarden token into the contract, causing it to pay 300 Ada for his benefit.
+ Christopher Marlowe withdraws the 300 Ada from the role-payout address.
+ Later, Mary Herbert deposits 300 Ada into the contract so she can have the token all for herself; this causes 150 Ada each for Elizabeth Cary and Jane Lumley to be paid for their behalves.
+ Elizabeth Cary withdraws 150 Ada from the Marlowe payout address.
+ Jane Lumley withdraws 150 Ada from the Marlowe payout address.
+ Mary Herbert withdraws 1 BearGarden tokens from the Marlowe payout address.

![SharedOwn](https://github.com/Fugu18/marlowe-finance/blob/main/images/NFT%20shared%20ownership.png)


### (7) NFT/FT Loan Collateral
A Bullet Loan with an NFT as Collateral
The party borrows 90 Djed with a BearGarden token as collateral; after they pay back the 90 Djed principal and 10 Djed interest to the counterparty, they receive their BearGarden token back. If they do not pay before the deadline, the counterparty keeps their BearGarden token.

This example consists of seven transactions:

+ Elizabeth Cary creates the token-sale Marlowe contract.
+ Elizabeth Cary deposits 1 BearGarden token in the contract.
+ Mary Herbet deposits 90 Djed in the contract, causing the contract to loan the 90 Djed to Elizabeth Cary.
+ Elizabeth Cary withdraws her 90 Djed from Marlowe's role-payout address.
+ Later, Elizabeth Cary deposits 100 Djed into the contract, which returns her token and pays the 100 Djed to Mary Herbert.
+ Elizabeth Cary withdraws her 1 BearGarden token from Marlowe's role-payout address.
+ Mary Herbet withdraws her 100 Djed from Marlowe's role-payout address.

![LoanCollateral](https://github.com/Fugu18/marlowe-finance/blob/main/images/NFT%20loan%20collateral.png)


### (8) NFT/FT Pawn for stablecoin
Pawning an NFT for iUSD
The party receives 100 iUSD for pawning a BearGarden token as collateral; if they pay back the 100 iUSD, they receive their BearGarden token back. However, at any time before such a redemption, the counterparty may decide to keep the BearGarden token.

This example consists of six transactions:

+ Elizabeth Cary creates the token-sale Marlowe contract.
+ Elizabeth Cary deposits 1 BearGarden token in the contract.
+ Mary Herbet deposits iUSD Djed in the contract, causing the contract to pay the 100 iUSD to the role-payout address for Elizabeth Cary.
+ Elizabeth Cary withdraws her 100 iUSD from Marlowe's role-payout address.
+ Later, Mary Herbert chooses to have the token withdrawn from the contract, depriving Elizabeth Cary of the chance to repay the 100 iUSD and receive her token back.
+ Mary Herbert withdraws her 1 BearGarden token from Marlowe's role-payout address.

![PawnStablecoin](https://github.com/Fugu18/marlowe-finance/blob/main/images/NFT%20pawning%20for%20stablecoin.png)


### (9) Token Sale with Oracle
This token sale uses a price oracle to set the cost of the tokens.
This example consists of six transactions:
+ John Webster creates the token-sale Marlowe contract.
+ John Webster deposits 1,000,000 HOSKY tokens in the contract.
+ The price oracle reports the exchange rate of 1 ADA = 11074197 HOSKY.
+ Elizabeth Cary deposits 90,300 lovelace in the contract, causing the contract to pay the token to her and the Ada to John Webster.
+ John Webster withdraws his lovelace from Marlowe's role-payout address.
+ Elizabeth withdraws her 1,000,000 HOSKY from Marlowe' role-payout address.

![Oracle](https://github.com/Fugu18/marlowe-finance/blob/main/images/NFT%20token%20sale%20with%20oracle.png)


### (10) English Auction
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
