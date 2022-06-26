# Bitcoin
`LINKS:` [3Blue1Brown video](https://www.youtube.com/watch?v=bBC-nXj3Ng4)
`TAGS:` 

---
Bitcoin is an online [[currency]] with extremely high volaitility. 

## The ledger system
Bitcoin uses a decentralized leger system to keep track of transactions, balances, and to verify the transactions. 

A copy of the ledger lives on each Bitcoin user's machine. The copies are verified by comparing them to the ledger that has the most *computational work* put into it. 

## Verifying the ledger system
This is how Bitcoin ledgers avoid fraudulent transactions being put onto them. 

We have to use a cryptographic hash [[function]]. A hash function takes a message / file, and outputs a "hash" or "digest" that is unpredictable when the message is changed. 

The hash function is cryptographic because computing it backwards is infeasable. For more detail on why, see [[256 bit security]]. 

This function can prove that a list of transactions is associated with a lot of computational effort. By adding a message to the end of the list of transactions such that the ledger, taken as an input to the hash function, results in the first 30 digits of the hash being zero, basically proves that whoever calculated that message went to a lot of trouble to do so. That would probably need a billion calculations or more. This is called a "proof of work." Every time a transaction is changed, a new proof of work is needed. 

The first step in actually implementing this to verify the ledgers is to divide the ledger into blocks. Each block is one or two transactions, with a proof of work that validates it. Each block also containes the hash of the previous block, so that you can't go back and change an old transaction, or change the order of any blocks without breaking the *block chain*. 

Guessing numbers to find the correct proof of work is called mining. Many people give the task to their machines, because whoever comes up with the correct number for the proof of work gets some amount of bitcoin as a reward. 

Non-miners just listen for blocks to update their copy. If two blocks emerge with conflicting transactions, the one which is longest, meaning that it has the most blocks connected to it, is the one that gets chosen. 

Functionally, this means that in order to get a fraudulent transaction approved, the scammer would have to find the proof of concept first, before all other miners. Then, the scammer would have to keep updating this separate blockchain so that it would keep up with the genuine blockchain, which would have a lot more computing power going into it. Eventually the genuine blockchain would win out, and the fraudulent one would get rejected. 

## Determining complexity of the hash function
In the above example, we proposed that the "proof of work" must make the hash have 30 zeroes at the beginning. Actually, that number is variable. It varies such that no matter how many miners are in the system, the correct proof of work is found every 10 minutes exactly (see [[complexity]]).

Also, the reward given to miners is reduced over time. It used to be 50 BTC, now its around 12. 

## The environmental cost of bitcoin
Bitcoin is produced through computationally-intense algorithms, that are scaled in complexity based on the number of active bitcoin miners in the world, such that a bitcoin is produced every ten minutes, no matter how many people are mining. 

This means that to calculate the energy needed to create a single bitcoin, we can take the sum of the total energy being spent on mining per second, and multiply it by 600 seconds per minute. 

The total bitcoin mining network in 2020 uses around 120 GW per second. That means that in the span of time needed to create a single bitcoin, miners around the world are using up 72,000 GW, or 72 TW. 

We can calculate the return on this investment in GWh/$ based on the price of bitcoin. This price fluctuates a ton, but as of Jan 18 2020, it stands at $36,751.70. 

With these numbers, we find that it takes 0.32 GWh to create $1 worth of bitcoin. To put it in perspective, the average house's electricity needs clock in at 0.9 GWh per month. That's 0.03 GWh per day, so $1 in bitcoin uses as much energy as powering your house for around 11 days. 