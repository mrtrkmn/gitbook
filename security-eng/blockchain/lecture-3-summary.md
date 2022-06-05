## Bitcoin Blockchain

![](../.github/assets/blockchain-chain.png)

## Account-based Ledger

Transactions            |  World State
:-------------------------:|:-------------------------:
![](../.github/assets/transactions.png)   |  ![](../.github/assets/world-state.png)

- Intuitively: We consider Bitcoin to use an account-based ledger. However, an account-based approach takes a lot of effort to track the balances of every account. 

- In reality, Bitcoin keeps track of the transactions an account has received and does not add up account balances( on the chain)

- By using a transaction-based ledger, Bitcoin enables wallet owners to define conditional transactions using Bitcoin script

* Bitcoin script is a stack-based scripting language used in Bitcoin transactions. 

## Transaction-based Ledger 

![](../.github/assets/transaction-based-ledger.png)

- Transactions (Tx) have a number of inputs and a number of outputs
    - Inputs (Txin): Former outputs, that are being consumed
    - Outputs (Txout): Creation of new coins and transfer of coin ownership
- In transactions where new coins are created, no Txin used (no coins are consumed)

- Each transaction has a unique identifier(TxID). Each output has a unique identifier within a transaction. We refer to them (in this example) as #TX[#txout] . e.g 1[1] which is second Txout of the second transaction

### Transactions Connected by Inputs and Outputs 

![](../.github/assets/transactions_ins_outs.png)

## Transaction-based ledger 

![](../.github/assets/transaction-based-ledger-table.png)

Example: 

0. No input required as coins are created
1. The Tx is used as an Txin. Two Txout are created, one to Bob and one to Alice. (1[0] and 1[1]) The Tx is signed by Alice
2. Uses first Txout of Tx1. Creates two Txout to Carol and Bob, signed by Bob. 
3. Uses second Txout of Tx1. Creates two Txout to David and Alice, signed by Alice. 

### Change Address 

Why does Alice have to send money back to herself ? 

In Bitcoin, either all or none of the coins have to be consumed by another transaction. The address the money is sent back to is called a **change address**. This enables an efficient verification , as one only has to keep a list of **unspent transaction outputs(UTXO)**

### Consolidating funds: 

Instead of having many unspent transaction outputs, a user can create a transaction that uses all UTXO she has and creates a single UTXO with all the coins in it. 

### Joint payments:

Two or more parties can combine their inputs and create one output. Of course, it requires signatures from all involved parties. 

## Anotomy of the Bitcoin Blockchain

![](../.github/assets/anatomy-of-the-bitcoin.png)

- Raw data is on disk 
- Miners and full nodes organize their data in a certain way. (Bitcoin core)
- As of February 2022, the total data size of the Bitcoin blockchain is 388 GB. 

## A newly Created Transactions Way into a Block

![](../.github/assets/transaction-path-to-a-block.png)


## Storing Bitcoins

- **Storing Bitcoins is all about storing and managing secret keys**

- Different approaches for storing and managing secret keys lead to different trade-offs between **availability**, **security**, **convenience**


![](../.github/assets/storing-bitcoins.png)

- Availability: being able to access the keys when one wants to 
- Security: restricting access to the keys
- Convenience: easy use 

## Cryptocurrency Wallets


Cold Storage            |  Hot Storage
:-------------------------:|:-------------------------:
Takes some time to "activate" | Is immediately available
Enhances security at the cost of convenience and availability | Enables convenience at the cost of availability and security
Advantage:  Cold storage does not have to be online to receive coins  | Example: Storage on your pc / mobile 


## Useful Resources

- [mempool.space](https://www.blockchain.com/explorer)
    - A block and mempool explorer for Bitcoin
    - Read [this article](https://bitcoinbriefly.com/how-to-use-mempool-space-block-explorer/) to better understand how to use the tool-
    
- [Jochoe’s Bitcoin mempool](https://jochen-hoenicke.de/queue/#BTC,24h,weight)
    - Another mempool explorer with useful insights

- [Blockchair](https://blockchair.com/bitcoin)
    - Some other blockchain explorer