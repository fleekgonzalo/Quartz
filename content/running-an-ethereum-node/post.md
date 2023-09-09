---
title: "Running an Ethereum Node: A Comprehensive Guide"
draft: false
tags:
  - ethereum
---
This guide will walk you through the entire process of choosing hardware, setting up and operating your node.

This project is recommended for developers or aspiring developers since theres not a financial incentive for running a node, unless you have 32 Eth (although there are some workarounds we will go into later on).

The main objectives of this project are:

- Learn how to set up and operate an Ethereum node
- Have a private node that can be useful for smart contract development
- Help decentralize the Ethereum network

Reads:
- [Spin up your own Ethereum node | ethereum.org](https://ethereum.org/en/developers/docs/nodes-and-clients/run-a-node/)
- [Nodes and clients | ethereum.org](https://ethereum.org/en/developers/docs/nodes-and-clients/)

# Choosing the Hardware

It is not a good idea to run a node in your main computer. Running a node is fairly resource intensive and will cripple your main computers performance.

Some choose to run a node in a VPS service like AWS. We wont be doing this because:
- It is not self-sovereign, meaning that we are not in control of our own node.
- It contributes to Ethereums centralization, because a lot of nodes are already set up in VPS services. (citation needed)

I have found two good options to run a node, with their own advantages and drawdowns:
- Single Board Computers, like a [Raspberry Pi](https://www.raspberrypi.com/).
- Tiny computers, like an [HP EliteDesk 800 G3 Mini](https://support.hp.com/us-en/document/c05371240).

There are multiple pros and cons between these two options, but it ultimately boils down to SBCs being smaller and more power efficient, while mini computers are more powerful, upgradeable and easier to keep many of them stacked on top of the other.

For what is worth, I think the best option for developers is to get a tiny computer. In case you decide going for a SBC, [Ethereum on ARM](https://ethereum-on-arm-documentation.readthedocs.io/en/latest/index.html) is a project that will guide you through the setup for most SBC brands and models.