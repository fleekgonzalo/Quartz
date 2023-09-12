---
title: Storing your Digital Assets Securely
draft: 
tags: []
date: YYYY-MM-DD
---
When you lose access to your bank account you can simply request a password change, but cryptocurrency is ruled by code and cryptography alone, meaning there is no such thing as customer support.

Learning how keys and wallets work will make your security better and your experience managing your assets much less stressful. We'll cover how cryptocurrency storage works and the best practices to secure your digital assets.

# Introductory Concepts

Lets first define what "storage" means in the context of cryptocurrency.

Because crypto is ruled by cryptography and not human law, the only thing that determines the owner of a cryptocurrency account is the ownership of its private/secret key.

A SK is a string of numbers that alows you to cryptographically sign transactions. This means that whoever knows this number will be able to spend all of the accounts balance, regardless of who the "legitimate" owner of the account is.

Example of a Private Key:
>107435187097287799521563287142577638987497617375775444773171446784043234144519

Private Keys also have the task of deriving Public Keys.

Example of the Public Key pair of the previous Private Key:
>0424c0c77337959e372042125a9907872dccdc7c5e3ca784c846a99f8cbe09c220d2383fa661f3de10d433a8397155a68c20540ae3bcb39368ebf8a3d26187f34a

Generally, when making a cryptocurrency account, you will be given a randomly generated seed/recovery/mnemonic phrase. This phrase is made up of 12 or 24 random words from the english dictionary and derives (gives access to) many private keys (many accounts).

![Key Generation](./key-generation.drawio.png)

Your public key is like your bank account's IBAN number or your Paypal username and it is used to receive funds. Your private key is like your credit card details, which lets you spend the funds in one of your bank accounts. Your seed phrase is like the password to your bank, which gives access to all your accounts.

When talking about storing cryptocurrency, we are actually talking about the safekeeping of the seed phrase and/or private keys.

# Wallets

A wallet is a computer program that handles your private keys and lets you interact with them via a user interface. Under the hood, wallets do things like 

- randomly generate a seed phrase
- derive a set of private keys from your seed phrase
- display your cryptocurrency balances
- use your private key to cryptographically sign transactions
- broadcast transactions with their signature to an RPC node
- etc

When we talk about wallets we are referring to non-custodial wallets. Custodial wallets are the wallets you have within exchange accounts, like Binance or Coinbase. If you have never had to write 12 or 24 words down, you're most likely using a custodial wallet.

Non-custodial wallets can generally be divided in two groups: software wallets and hardware wallets. Software wallets store your private keys in your computer or web browser, while hardware wallets are small independent physical devices that hold your private keys and have the only function of signing transactions without exposing your private keys to the internet.

Lets see an example of how cold wallets work:
- user connects hardware wallet to software wallet
- user uses a software wallet to request a transaction
- hardware wallet receives the unsigned transaction sent by the software wallet
- hardware wallet signs transaction inside the device
- hardware wallet sends back the transaction + signature to the software wallet
- software wallet broadcasts the transaction + signature to an RPC node

Hardware wallets offer more security in exchange for convenience (and the cost of buying the device). Software wallets are more suitable for smaller portfolios, short term holdings and throwaway accounts, while hardware wallets are better for large portfolios and long term positions.

To clarify, there are many people that hold large portfolios in software wallets and are doing perfectly fine, but if you are not very computer savy and/or want to sleep better at night you may want to consider a cold wallet.

*Note: Using cold storage doesn’t mean that you cant lose your funds in any way. If you click a sketchy link and sign a transaction with your hardware wallet that drains you it doesn’t matter what type of wallet youre using, you’re going to lose your funds.*


## Seed Phrase Management

As previously said, your seed phrase derives all of your private keys (aka, all your accounts). Needless to say, it's indispensable to keep a copy of your seed phrase in a secure location in case you lose access to your wallet so you can restore it, and this copy needs to be stored securely.

There are many ways to store your seed phrase.

- You can write down the words in a piece of paper and store it somewhere safe, like a home safe or even a safe deposit box.
- You can also store it digitally inside an encrypted file, like that of a password manager.

You can also make multiple copies, and for example store one home and one in a safe deposit box in case the other is lost. Come up with your own system based on your situation, available tools and risk model.


# Common Attacks

Contrary to popular belief, most attacks to personal cryptocurrency portfolios arent done by a genius hacker in a black hoodie that cracks your wallet password or keylogs your computer. More often than not users lose their funds by falling for scams or practicing bad operational security.

### Phishing Scams

The easiest way to lose your crypto is falling for phishing scams. Look out for things like:

- Wrong URLs of popular crypto apps and websites. 
- Unexpected NFTs appearing in your wallet that say you qualify for an airdrop.
- DMs from people you don't know asking for help or offering to help you.
- Etc.

### The $5 wrench attack

![5 Dollar Wrench Attack](./5-dollar-wrench-attack.png)

Keep a low profile.

- Be pseudonymous online and don't reveal your real identity.
- Dont talk about crypto with people that know your real identity.
- Dont brag about the money you have or have made in crypto.

Any and all of these put you physically at [risk](https://www.mirror.co.uk/news/us-news/mising-crypto-king-found-chopped-30707060).

## Practice

The best way to become confident managing your cryptocurrency is by having on hands experience. You may have studied so much about driving but until you get your hands on the steering wheel you don't know how it truly is.

Here are some practice exercices you can do without using real funds.

**Preparations**:
- Make a new cryptocurrency account.
- Store the seed phrase thats generated by your wallet in a secure place.
- To practice without the risk of losing any real money you can receive some free testnet tokens for the Sepolia testnet using this [faucet](https://sepoliafaucet.com/).

**Actions**:
- Make new accounts inside your wallet. Remember that a seed phrase can generate multiple SK/PK pairs.
- Identify your private key/keys and your public key/keys within your wallet. Copy and paste them into your password manager or textfile and label every item correctly (seed phrase, private key and public key).
- Uninstall and reinstall your wallet and restore your accounts using your seed phrase.
- Uninstall and reinstall your wallet and restore only one account using one of your private keys.
- Uninstall your wallet and restore your accounts using your seed phrase in a different wallet, like Frame or Rabby.
- Make a new wallet and send funds back and forth from the original wallet to the new wallet.

You can repeat these exercises and jump from one to another until you feel comfortable.

# Wallet recommendations

**Hardware Wallets**

For a Bitcoin wallet use Electrum or Wasabi.
For an Ethereum wallet use Rabby or Frame.


**Software Wallets**

The two most popular hardware wallet brands are Ledger and Trezor.

Ledger is infamous for the [data breach](https://www.bleepingcomputer.com/news/security/physical-addresses-of-270k-ledger-owners-leaked-on-hacker-forum/) they were subject to that exposed the house addresses of hundreds of thousands of costumers. Not only this, but recently Ledger revealed that they're able to extract the private keys from the devices secure element through their closed-source firmware.

Trezor devices are completely open source: the hardware, the firmware and Trezor Suite, their software wallet. Unfortunately, their devices are very vulnerable to [physical attacks](https://blog.kraken.com/kraken-identifies-critical-flaw-in-trezor-hardware-wallets). Even so, id rather use a Trezor than a Ledger device.

If you have an old phone you don't use laying around you can also try [AirGap](https://airgap.it/), which effectively turns your phone into a hardware wallet (but rendering it useless for any other purpose since it can't be connected to the internet as stated earlier).

For most people I recommend the Trezor One.



// risk modeling