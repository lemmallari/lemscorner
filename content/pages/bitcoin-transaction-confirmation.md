---
title: BTC Transaction Fees and Confirmation Times
date: Last Modified 
permalink: /bitcoin-transaction-confirmation/index.html
eleventyNavigation:
  key: bitcoin-transaction-confirmation
  order: 3
  title: BTC Transaction Fees and Confirmation Times
  parent: crypto
---
{% image "bitcoin-concepts-terms.jpg" "bitcoin gold nuggets" %}

This is another post I recovered from my notes. As crypto is becoming adopted by more and more people, there will be times when these systems experience some issues which can cause the average user to panic. One known issue is that sometimes you don't receive your coins after withdrawing them from an exchange or sending it from one wallet to another. Another known issue is the high transaction fees (very visible in both Ethereum and Bitcoin) from time to time. In this post I'll try to explain why these two common issues regularly happen.

---
### Transaction Fees

For new Bitcoin users, the concept of transaction fees are not immediately noticeable. However, if you look closely, whenever you perform any transaction using your Bitcoin this transaction fee is always present. So what are transaction fees and what are they used for?

To answer that, we need to back track a bit and go back to our previous discussion about blocks and transactions. As we already know, blocks store all transactions made in the Bitcoin network permanently. We also learned that miners solve for hashes in blocks in order for a block to be added into the blockchain. So where does transactions fees come in? We must first understand the building blocks of a transaction before we continue.

### Inputs and Outputs

I mentioned in my previous post that a transaction contains an input and an output. A single transaction can contain multiple inputs and multiple outputs.  To keep it simple,  an input tells you where your Bitcoins came from. On the other hand, an output tells you where your Bitcoins will be sent. Let's have an example to have a better idea of how inputs and outputs work in a transaction. (This example does not include transaction fees yet!)

Let's say you have 10 Bitcoins and you wanted to purchase a car worth 9 Bitcoins. For simplicity's sake, let's just say that your 10 Bitcoins came from a single transaction. Now you bought the car and sent your 10 Bitcoins to the car dealer. You will then get your 1 Bitcoin back and 9 Bitcoins will now be sent to the car dealer. In this example, your transaction of sending your 10 Bitcoin to the dealer will contain 1 input (which is your 10 Bitcoins) and 2 outputs (1 output is the 1 Bitcoin returned to you as your change and the other output is the 9 Bitcoins you sent to the car dealer).

::: callout
Note: Inputs and Outputs are much more complicated than this. This is merely an over simplification.
:::

### Transaction Size

Now that we know about inputs and outputs, we also need to know what a transaction size is in order to understand how transaction fees are calculated.

A transaction can be composed of a single or multiple input and a single or multiple output. Each input and output has its own size in bytes. We can calculate for the transaction size by adding up all the sizes of inputs and outputs plus other information included in the transaction. For example a single transaction can contain 40 inputs and 16 outputs. With other information in place, the resulting size of that transaction is 7761 bytes or 7.58 kilobytes. The other information included in a transaction other than the inputs and outputs are constant in all transactions. This means that the number of inputs and outputs greatly affects your transaction size.

### Bitcoin Block Size and the Mempool

Before finally going back to transaction fees, we must first understand Bitcoin's block size and how it affects everything. In our example above, a single transaction with 40 inputs and 16 outputs totaled to about 7.58 kilobytes. Bitcoin's blocksize, disregarding SegWit's "advantage", is just 1 megabyte. Since we already know that a block is comprised of multiple transactions, this means that only a handful of transactions can be included in a block whenever it is mined by miners. Basing from my previous post, we have an idea that a block is mined roughly every 10 minutes. So if we have a lot of transactions amounting to more than 1 megabyte, where do these transactions end up while they are waiting to be included in the next block to be mined? 

That's where the Mempool comes in. You can think of the mempool as the "waiting lounge" of transactions that have yet to be included in a block. Each mining node has their own set of mempools which miners use to store transactions that they will process in the next block that they will mine. Whenever a transaction is included in a block, it is removed from the mempool. There are times when activity in the Bitcoin network gets so high that the mempool gets clogged up. This results to thousands of transactions being "stuck" in the mempool for hours since only a handful of transactions can only be included in a block every 10 minutes. There are even times when a transaction gets cancelled because it was left in the mempool for far too long (2 to 14 days). 

### Back to Transaction Fees

So where does the transaction fee fit in to all these? As mentioned above, Bitcoin's blocksize is only 1 megabyte. This greatly limits the number of transactions that can be included within a block. Technically, transactions should be on a first come first serve basis or what we call FIFO (First in, First Out). However due to the limited block size and high number of transactions on busy days, most transactions end up waiting in the mempool.

A fee market was later on introduced to Bitcoin. This allowed users to set a higher fee than normal so that miners will prioritize their transactions over other transactions. This also incentivizes miners to prioritize transactions with higher fees. Transaction fees are measured by sats (satoshis*) per byte. This means that the larger your transaction size is, the more expensive your transaction fee would be. Take note this is based on transaction size (inputs + outputs + other info) and not transaction amount. Because of this fee market setup, the growing demand for the usage of Bitcoin and the limited block size, network fees sky rocketed and confirmation times became longer.

### Confirmation and Confirmation Times

We already know that a block contains transactions. Once a block is added to the blockchain, all transactions in it will be irreversible and will be forever part of the blockchain. To secure a transaction against double spending, all transactions require a minimum number of confirmations before being considered as "Confirmed". So what are confirmations?

Once a transaction gets included in a block, it automatically gets one confirmation. This means that your transaction is 1 level deep in the blockchain. When a new block gets added, your confirmation number increases by 1. For majority of small transactions, 6 confirmations are required before considering a transaction as confirmed. This means that once your transaction is included in a block, you must wait for 5 more blocks to be mined before your transaction gets confirmed. On average, a small transaction should not take more than 1 hour to be confirmed. 

Unfortunately, due to the fee market, transactions with higher fees gets prioritized by the miners. This leaves transactions with lower fees stuck in the mempool while waiting to be included in the next block. This means that there are times when your transaction may take hours or even days before it gets confirmed in the network. This does not mean your funds are lost forever, they are just stuck in limbo waiting to be processed by miners.

### Summary

Due to the fee market and the limited block size of Bitcoin, users experience high transaction fees and long confirmation times. So the next time you want to send your coins from your personal wallet to an exchange, don't be surprised if the fee is too high or if it takes hours or days before your transaction gets confirmed. It will eventually get there, you just need to be patient.

### Other Notes

If you want to check the average transaction fee (sats per byte), you can check this [site](https://bitinfocharts.com/comparison/bitcoin-transactionfees.html).
If you want to check how many transactions are in limbo, you can check it [here](https://jochen-hoenicke.de/queue/#BTC,24h,weight).

The higher the number in these sites, the higher the transaction fee and the longer confirmation time will be needed for your transaction to get confirmed.
