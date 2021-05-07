---
title: Blockchain Concepts and Terms
date: Last Modified 
permalink: /blockchain-concepts-terms/index.html
eleventyNavigation:
  key: blockchain-concepts-terms
  order: 2
  title: Blockchain Concepts and Terms
  parent: crypto
---
{% image "bitcoin-concepts-terms.jpg" "bitcoin gold nuggets" %}

This is an old post I recovered from my notes when I was still writing actively last 2017. I realized then that a lot of people getting involved with cryptocurrencies usually start out with Bitcoin but have no idea on how Bitcoin or blockchain works. In this post I'll try to explain a bunch of concepts and terms that you might hear when dealing with Bitcoin or blockchains in general.

---

Reaching another record high, Bitcoin is gaining more and more attention. Most probably crypto traders, miners and enthusiasts alike will notice that more and more people are talking about Bitcoin and cryptocurrency in general. Whenever Bitcoin reaches a new all-time-high, a bunch of new users are pulled in by the hype and try to put in as much money as they can in crypto. This usually clogs up the system which results to people asking why their transactions fees are way too high and why it's taking a long time for their transaction to push through (aka why is my transaction not yet confirmed).

If you haven't read the bitcoin [white paper](https://bitcoin.org/bitcoin.pdf), I highly suggest that you do. If you don't have the time, I'll try to simplify some of the concepts behind transaction fees and confirmation times. However, before that, we must familiarize ourselves with some basic terms in Bitcoin and the blockchain technology.

### Transactions

Let's start with a very basic concept of transaction.  The wiki defines a [transaction](https://en.bitcoin.it/wiki/Transaction) as "a transfer of Bitcoin value that is broadcast to the network and collected into blocks". To put it simply, you can consider your buy/sell/withdraw/send bitcoins as a transaction. Whenever you buy Bitcoins from Coinbase or send your Bitcoins as payments, those activities are all considered as transactions because you gain or lose Bitcoin and that gain or loss is then recorded in a block. A transaction also contains inputs and outputs but more on that later.

### Blocks

As mentioned earlier, transactions are all collected into blocks. So what is a block? A block is a container of transactions. This is where all transactions are permanently recorded. You can think of a block as a ledger where you note down whom you paid and who paid you. Whenever you make a transaction (buy or sell), it will be saved in a block and later on stored in the blockchain.

### Blockchain

We already know what a transaction and block is. Now it's time for us to discuss what a blockchain is. A blockchain is literally just a chain of blocks. What makes the blockchain technology great is the fact that since all transactions are recorded in a block and a block is later on added to the blockchain, all historical transactions starting from the genesis block (the very first block mined) up until the latest transaction are visible to everyone. There are more technical aspects behind the blockchain but we won't discuss it for now. Just understand that a blockchain is a collection of blocks where ALL transactions in the Bitcoin network is stored. From the first transaction of Satoshi Nakamoto to Hal Finney, the 10,000 BTC worth of pizza bought way back, up until the recent Bitcoin purchased are all stored in the blockchain.

### Miners

I mentioned above that a blockchain is a collection of linked blocks where all our transaction are saved. However, have you thought how blocks are created and who maintains the blockchain? Nodes, most specifically mining nodes or what we commonly call Miners are responsible for all of these. All miners have a copy of the entire blockchain in their nodes. So as not to complicate things, you can think of a node as a computer used by a miner. It's the responsibility of the miners to secure the Bitcoin network. They do this by constantly validating blocks added in the network and making sure that those blocks are valid. They are also responsible for creating blocks that will be added in the blockchain. Whenever there are set of transactions done in the Bitcoin network, miners compete with each other to find what is known as a hash so that they get rewarded. Currently a miner who successfully solves a block is rewarded 12.5 Bitcoins. This cycle of finding a block and adding them to the blockchain usually takes on average 10 minutes. This means there are roughly 6 blocks added to the blockchain every hour.

---

In a later post which also came from my old notes, I'll be discussing why we sometimes get high transaction fees and long confirmation times with Bitcoin.