### Properties of Cryptographic Hash Functions

1. Preimage Resistance  
  
    - h is a function 
    - for essentially all pre-specified outputs y, it is computationally infeasible to find an x such that h(x) = y 
    - h is also called **one way function**

2. 2nd Preimage Resistance 
    
    - Given x it is computationally infeasible to find any second input x' with x != x' such that h(x) = h(x')

3. Collision Resistance

    - A hash function h is said to be collision resistant if it is infeasible to find two values, x and y such that x != y, yet h(x) = h(y)

- 2nd Preimage Resistance is subset of Collision Resistance

- Output of hash functions can be revealed with brute force if a salt is not used while hashing input. 

### Merkle Trees

- A Merkle Tree is a data structure using cryptographic hashes, basically a binary tree with hash pointers
- It is used as efficient and secure way to verify large data structures
- It especially provides an efficient way to 
    - proof that a certain data block is contained in a Merkle Tree (Proof of Membership)
    - proof that  a certain data block is not contained in a sorted Merkle Tree (Proof of Non Membership)

![](../.github/assets/merkle-tree.png)

#### Proof of Membership 

- We want to ensure that a certain data block is contained in the Merkle Tree without hashing the complete tree

- Only the hashes of corresponding nodes and leaves have to be checked/validated (without disclosing other content)

- E.g we want to evaluate whether "Data #3" is contained in the Merkle Tree or not

- This enables verification in log(n) time.

![](../.github/assets/merkle-tree-pom.png)