# Crypto-Kickstarter
This is a smart contract system used to run a simple kickstarter campaign over a blockchain. The difference between a "crypto kickstarter" and an ICO is vast. The Crypto Kickstarter is used to primarily validate real-world addresses so that a hardware product can be delivered to said address, and any additional blockchain features received by the donator are considered not to be a part of the purchase. It represents a legal obligation for a hardware product to be delivered to the end user. In this context, "address" is not an ethereum address, but a traditional real-world address (street name, city, zip code, etc).

It is possible to expand this repo to develop a more "proof-of-individual" kickstarter, limiting hardware deliveries based on a zip code, name, or particular address. This would ensure that a small number of investors do not receive an unfair amount of blockchain features (i.e. vybuds or maybe even tokens), which would effectively corrupt a blockchain system that would otherwise have proof-of-individual potential.

The repo consists of two main elements: The smart contract, and the web page (an example one, anyway).
## Smart Contract
The smart contract collects ETH and distribute OBLs in increments of 0.1 ETH. This "increment" system allows us to produce a number of vybuds that is whole and not fractional, and deliver it to the user's given address. For example:
* 	A donation of 0.10 ETH returns 20 OBL and 1 Vybuds (1 Karma)
* 	A donation of 0.19 ETH returns 20 OBL and 1 Vybuds (1 Karma)
* 	A donation of 0.20 ETH returns 40 OBL and 2 Vybuds (2 Karma)

OBLs are tokens used on the [Project Oblio experiment smart contracts](https://github.com/project-oblio/decentralized-neuroscience-smart-contracts). Karma are just a record to be used in a sort-of proof-of-individual system, if we can ever develop one (we think we can). Karma can be used to [create fractional voting power](https://medium.com/@FEhrsam/blockchain-governance-programming-our-future-c3bfe30f2d74) based on how trusted an identity is. To be clear, karma is not at all synonymous with "number of vybuds owned", except in the case of this initial kickstarter.

Some things to consider:
* Making donator's addresses public is useful if we want to prevent someone from hoarding a large number of vybuds, and using them to attack the network early on with fake data. The maximum number of vybuds that a single person can order in our kickstarter has not yet been determined.
* A donator who wanted to remain anonymous could donate ETH, provide a fake address, and receive only OBL. In this case, Vybuds would validate said address in a centralized way and choose not to deliver to it. So, the investor only games the system by collecting a bunch of OBL, but not vybuds. A future blog post will describe why this wouldn't be advantegous for the investor. 
* This is different from an ICO because a separate log is kept on a per-vybuds basis. The number of vybuds can be limited, effectively preventing one person from hoarding too much of a particular kind of wealth ("Karma"; Vybuds hardware). 
* Thus, there are really two tokens being born here: Karma (more of a score than a token), and OBL. 

## HTML page
A simple HTML page is included which validates address data and creates a JSON structure for input into a myetherwallet.com transaction as the "additional data" field. It ensures that the address data put into the form will be accepted by the smart contract. 

## Proof-of-address ???
Yea... Nothing is ever 100% secure, but it would be really hard for someone to "fake-generate" multiple valid addresses and receive multiple vybuds packages there. Not all security can be as secure as encryption, this is meant to make things difficult AND public in the event someone does try to abuse the setup.
