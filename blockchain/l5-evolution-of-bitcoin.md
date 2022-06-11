# L5- Evolution of the Bitcoin Network 

As any other software, blockchains also require updates. 

These updates affect two parts of the network: 

- The **software relying on full nodes** (wallets, etc)
- The **blockchain network** (the full node implementations)

Considering wallets and other software, updates have well-known issues. 

1. Incompatibility between old and new software components 
    -> Old and new software components have to check the version available at runtime

2. Incompatibility between historic data and current data schema expected by the software components
    -> Database schema changes and data migration

> Therefore, the Bitcoin network inherits these standard problems. 

Additionally, the immutable blockchain data structure and the decentralized P2P-network lead to evolutionary issues. > Process for protocol update. 


## Process of Bitcoin Protocol Update 


![](../.gitbook/assets/bitcoin_protocol_update.png)

## Design 

- Proposals can target different layer: 
    - Consensus Layer (how to validate states and history)
    - Peer Services Layer (propagation of messages)
    - API/RPC Layer (high-level calls accesible by apps)
    - Applications Layer (high-level structures)

- All proposals in Bitcoin are referred to as **Bitcoin improvement proposals (BIP)**

- A Github-repository maintained by the core-developers contains all BIPs.

- A BIP contained in the repository is not automatically accepted. Furthermore, the miner community decides whether an BIP is implemented. (See signaling)

- A final BIP contains a detailed description as well as **a reference implementation** Developers of other clients should be able to also adopt the BIP. 

![](../.gitbook/assets/possible-bip-paths.png)


The terms hard fork and soft fork describe changes within the **consensus layer**

- **Hard fork:** Structures, that are invalid under old rules become valid under new rules. 

- **Soft fork:** Some structures, that were valid under the old rules aare no longer valid under the new rules. 

- Other changes applying to other layers are not classified as a hard fork or a soft fork. E.g if a new RPC/API call is introduced, the consensus layer is not affected. 

**Examples**

The Bitcoin core client specifies a maximum block size of 1 MB. 

- An update enabling block size up to 8 MB is considered a **hard fork** 

- An update restricting block sizes up to 0.5MB is considered as **soft fork**

## Signaling 

- The following diagram shows that a soft fork that is not accepted by the majority of miners leads to two chains.

![](../.gitbook/assets/signaling.png)

- The disadvantage of a chain split is that both chains compete for users. 
    - A split could be the goal of the designer or not 
- To find out whether a chain split would occur, a signaling phase is used. 

Signaling is the process that is used for voting on proposals. 
Miners are the only network participants who can cast their votes. They gain the right to vote only when they mine a new block. To signal their vote, they include special values in the header of the blocks they mine. 

**How does it work ? **

- The version-field in the block header contains 32 bit. 
- Each author of proposal (reference implementation) selects a bit in this version-field, a start time and an end time. 
- If miners update, their node software uses the bit to signal the support of this miner for this proposal between start time and end time. 

- **Option A** : The overall support for this proposal is higher than a certain threshold (usually 1916 out of 2016 blocks -> 95 % ) in one difficulty period. The proposal is **accepted (locked in)** and the rules apply after further 2016 blocks to allow the remaining miners to update as well. 

- **Option B:** The overall support for this proposal is lower than the threshold until the end time. The proposal is **rejected**

- As of the signaling, miners can vote up to 29 different proposals at the same time. Bits are reused after the end time. 

## Results 

- If the signaling lead to acceptance, the proposal is automatically implemented. 
- Upon a rejection, the community can split (seperate the development and go into different directions) 

> This is called "Chain Split"

Obviously, both communities want to keep the history.

Two main problems arise with the creation of a second chain: 

1. If the community behind the hard fork has less than 50% of the computational power, the new chain will not work as the new software will switch back to old chain, as the old chain will probably have the higher weight. 
2. One transaction can be executed on both chains > Replay attacks. 

To prevent both problems, the new community has to make the new chain/software incompatible with the old chain. This is done via the creation and adaption of new parameters, such that the old chain is not accepted by the new software and the other way around. Another possibility is to define a second "genesis" block which has to be contained in the longest chain. If the second block contains new rules (rejected by the old software) the chains are split indefinitely and can not merge together. 

- There have been numerous successful Bitcoin soft forks like Pay to Script Hash (P2SH)

- We are not aware of a successful Bitcoin hard fork. 

- Some chain splits were executed with varying success, e.g 
    - Bitcoin Cash (8MB blocks instead of 1MB blocks)
    - Bitcoin Gold (changes in the PoW-algorithm for ASIC resistance)


## SegWit and Taproot 

- **Segregated Witness**(SegWit) and **Taproot** are two major upgrades that occurred on the Bitcoin network. 

- Both are **soft forks**

**SegWit**

- Aimed to increase the transaction throughput by reducing the weight of transactions in a block 
- Removed the signature data from the transaction and appended it to the end of the block. 
- Increased the number of transactions that can fit into a block 

**Taproot**

- Introduced a new signature scheme, the Schnorr signature. 
- Schnorr signatures provide a more efficient and secure way to authorize transactions. 
- Improved privacy and efficiency of the network. 


