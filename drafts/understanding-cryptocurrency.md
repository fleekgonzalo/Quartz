---
title: Understanding Cryptocurrency
draft: true
tags:
  - draft
date: YYYY-MM-DD
---
---

A cryptocurrency is a decentralized network of computers that processes transactions. The key difference that sets cryptocurrency apart from the traditional financial system is that it is a decentralized system. In normal finance transactions are processed by a few institutions such as your bank or credit card provider; in cryptocurrency however, your transactions are processed by a decentralized network of computuers.

![how-blockchain-works](../../public/images/how-blockchain-works.png)


## Bitcoin

The concept of cryptocurrency was born with Bitcoin, the first and still biggest by market capitalization. Bitcoin was created by an anonymous individual or group known as Satoshi Nakamoto after the 2008 financial crisis, driven by a distrust for banks and the objective to create a trustless, decentralized currency.

Here are some of the key innovations that came together to create Bitcoin and cryptocurrency as we know it:

- **Blockchain**
- **Consensus mechanism**
- **Public-key cryptography**


### Blockchain

A blockchain is a database made up of blocks that gets expanded with every new appended block.

Blocks are where the transactions are stored. You just need to know that each block:

- Has a list of transactions.
- Is chained to the previous block.

![Blockchain](../../public/images/blockchain.png)


### Consensus mechanism

You will often hear the words "Proof of Work" used interchangeably with "consensus mechanism", but they are not the same. The Proof of Work algorithm is just one of the different components that make up the consensus mechanism.

Proof of Work makes the network reliable and protects it from spam attacks, because to append new blocks you need to spend a great amount of computational resources to solve a cryptographic puzzle.

The people who use specialized computers that run algorithms to get the correct answer to this puzzle are called miners. Miners pick unconfirmed transactions and add them to a pending block. Then they solve this cryptographic problem and append the block to the blockchain, thus confirming the block and the requested transactions within it. As a reward for spending computational resources to secure the network and adding a new block to the blockchain, miners get rewarded with Bitcoin.


### Public-key cryptography

Public-key cryptography, also known as asymmetric cryptography, involves the use of two keys: a public key, which is used to receive funds and can be shared openly, and a private key, which is used to cryptographically sign transactona and needs to be kept secret.

Example of a Private Key:
> 29820647850784916136546797983647695173650021403252862671776771698786006629542

Example of the Public Key pair of the previous Private Key:
> 048c7285878426edda759f3c7ce42a7a76ec96a9ea29007cc1236372a18dc97989ed26cbdc3463e75fab2eb029a061c0c3fa9fba55d47b7f885381c0ffafc9846f

These keys are mathematically related strings of numbers and we can use our private key to derive a public key, but not the other way around.

![One Way Key](../../public/images/one-way-key.png)

Your public key is like your bank account's IBAN number or your Paypal username and it is used to receive funds. Your private key is like your Paypal accounts password or your credit card details, which you require to spend your money.

Just like banks don't make users do overly technical things like updating the accounting books every time they transact, in cryptocurrency users dont need to do things like signing transactions and sending them manually.

The creation, use and management of keys are handled by a wallet computer program. Wallets  generate a wordlist called the seed/recovery/mnemonic phrase, which is made up of 12 or 24 randomly selected words from the english dictionary. This seed phrase derives a set of private key public key pairs.

![Hierarchical Deterministic Generation](../../public/images/hierarchical-deterministic-generation.png)
*Red: NEVER SHARE - Green: Safe to Share*

Under the hood, when you want to transact using a wallet it prepares the transaction by placing the senders public key, the amount to send, and the receivers public key. Then it runs the prepared transaction through a signing algorithm alongside your private key which generates a signature for that specific transaction. This signature proves that the transaction has been signed by the true owner of the private key pair to the public key that wants to spend funds without the need to share our private key.

// nodes and miners
// explain everything as consequenc of the other?
