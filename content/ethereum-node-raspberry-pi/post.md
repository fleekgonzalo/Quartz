---
title: Running an Ethereum node with a Raspberry Pi
draft: false
tags:
  - ethereum
date: YYYY-MM-DD
---
This guide will walk you through the entire process of setting up and operating an ethereum node using a Raspberry Pi 4 model B, though the process is fairly similar for other brands of Single Board Computers.

This project is recommended for learning purposes since theres not a financial incentive for running a node by itself.

The main objectives of this project are:
- Learn what are nodes and how they work
- Learn how to set up and operate an Ethereum node
- Have a private node that can be useful for smart contract development
- Help decentralize the Ethereum network

Reads:
- [Spin up your own Ethereum node | ethereum.org](https://ethereum.org/en/developers/docs/nodes-and-clients/run-a-node/)
- [Nodes and clients | ethereum.org](https://ethereum.org/en/developers/docs/nodes-and-clients/)


## What is a node?

Nodes are the foundation of Ethereum, or any other Layer 1 cryptocurrency such as Bitcoin. A regular personal computer becomes a node when it runs a software client that connects it to the network of nodes and performs some tasks:

- Storing a copy of the blockchain.
- Receiving transactions from an account or from other peer nodes.
- Verifying received transaction signatures and other criteria such as enough existing balance to fulfill the transaction.
- Storing valid transactions in the memory pool.
- Propagating valid transactions.

If the node in question is a validator node, then it also performs the tasks of:

- Preparing new blocks.
- Proposing and validating new blocks.

A validator node can be set up if the node operator stakes 32 ETH. The node operator will be rewarded with staking rewards for every proposed block. However, if the validator misbehaves, it might be slashed, causing the loss of staked funds.

# Why Raspberry Pi?

It is not a good idea to run a node in your main computer. Running a node is fairly resource intensive and will cripple your main computers performance.

Some choose to run a node in a VPS service like AWS. We wont be doing this because:
- It is not self-sovereign, meaning that we are not in control of our own node.
- It contributes to Ethereums centralization, because a lot of nodes are already set up in VPS services. (citation needed)

I have found two good options to run a node, with their own advantages and drawdowns:
- Single Board Computers, like a [Raspberry Pi](https://www.raspberrypi.com/).
- Tiny computers, like an [HP EliteDesk 800 G3 Mini](https://support.hp.com/us-en/document/c05371240).

There are multiple pros and cons between these two options, but it ultimately boils down to SBCs being smaller and more power efficient, while mini computers are more powerful, upgradeable and easier to keep many of them stacked on top of the other.

The [Ethereum on ARM](https://ethereum-on-arm-documentation.readthedocs.io/en/latest/index.html#) project has created system images for many different SBC brands. They also have a complete guide on how to set up and run your node, which you should follow along.

## Hardware

You will need:
- Raspberry Pi 4 model B
- MicroSD Card (16 GB Class 10 minimum)
- 2 TB SSD
- Power supply
- Ethernet cable
- Case with heatsink and fan

For most SBCs storage you will need a 2 TB M.2 NVMe SSD. For the Raspberry Pi however, you will need a USB 3.0 disk or a M.2 SATA SSD with an USB to SATA case.

I ended up going for a WD Blue 2TB M.2 SATA SSD (important to note that the SSD needs to be SATA and not NVMe).

The best case I found is the Argon ONE M.2, which has a SATA to USB adapter, heatsink and fan. Thanks to this case both the SBC and SSD can be inside of a case, instead of the SSD hanging outside the computer. Here is a [video](https://www.youtube.com/watch?v=62FfPT38obo) guide for the Argon ONE M.2 setup.

As for the other required hardware is not very complicated. I would recommend to get the official power supply to not have problems with the voltage.


# Initial setup

1. Go to Ethereum on ARM's documentation and download the Raspberry Pi image.
2. Flash it to your MicroSD using [Etcher](https://etcher.balena.io/).
3. Insert your MicroSD into your Raspberry.
4. Plug the ethernet cable and power supply in.

Before continuing, you will need to change some settings of your router.


## Router

Your creedentials might be written somewhere on your router, if this is not the case you might need to contact your Internet Service Provider or look up default passwords for your router model.

To find the admin panel you need to search "192.168.1.1" in your browser.

Now you need to do the following:
- Find and write down the private IP of your Ethereum node by going into something like "connected devices" and finding "Ethereum on ARM".
- For Nimbus Consensus Client -> Open port 8551 UDP/TCP (internal and external).
- For Erigon Execution Client -> Open port 30303 UDP/TCP (internal and external).


## SSH

The Secure Shell protocol allows us to control a device remotely. Instead of needing to plug a screen and keyboard to our Raspberry whenver we want to use our node we can control it from the comfort of our main computer.

To SSH into your newly set up node, run

> ssh ethereum@your_board_IP

When you do this you will be prompted by a username and password, which are

> User: ethereum

> Password: ethereum

Then you will be forced to change the default password to a new one, do so.


## Installations

You should now be greeted by a screen that reads your computers specifications. Now we need to start setting up some things.

General updates:
> sudo apt upgrade

Argon ONE fan script:
> curl https://download.argon40.com/argon1.sh | bash

Installing the client softwares:
> sudo apt-get -y install geth nethermind erigon besu prysm lighthouse nimbus teku

Now we are ready to set up our Consensus and Execution clients.


## Client Diversity

For the health of the Ethereum network it is important that not all node operators use the same software clients. This is to prevent single points of failure in case theres a bug in one of the clients. If a majority of nodes are using the same client and this client has a bug it could mean a severe security threat for the whole network. This isnt a problem if no single client is being used by a majority of nodes.

Client diversity [dashboard](https://clientdiversity.org/#switch).

At the time of writing, Nimbus and Erigon are minority clients (under 10% of total nodes use them). Those are the clients we will be using.

// Talk about what each client does and the different sync methods.


## Syncing the blockchain

To start downloading the blockchain:
- sudo systemctl start nimbus-beacon
- sudo systemctl start erigon

To see the progress:
- sudo journalctl -u nimbus-beacon -f
- sudo journalctl -u erigon -f
