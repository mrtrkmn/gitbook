# Obfuscation

## General Questions

1. Which kind of attacker does software obfuscation aim to protect against? 1P

 -  Man-in-the-middle (MITM)
    -  attacks communication channels (e.g replays messages)
 -  Remote attacker 
    -  exploits vulnerabilities (e.g buffer-overflows)
 -  Man-at-the-end (MATE)
    - reverse engineers software (e.g steals intellectual property)

2. What are the 2 types of attacker goals when attacking obfuscated programs ? 1P 

    -  Stealing intellectual property (e.g algorithm)
    -  Stealing secret data from software (e.g keys, passwords)

3. Explain in 3-5 sentences how software diversity works

    - The main idea of software diversity is to have different versions of a software to protect intellectual property and secret data, it is not totally accepted and applied. It can be applied
    to as pre-distribution and post-distribution software diversity. Pre-distribution is to have obfuscation
    transformations involve randomly generated code & data. Post-distributino is to have piece of code which
    embeds self modifying code in application.

    - Provides protection against MATE attacks. 


## Strength of Obfuscation

1. Describe each of the 4 factors/dimensions for characterizing the strength of obfuscation (proposed by Collberg) using 1-2 sentences. 2P

    a. **Potency > comprehensibility of code by humans** 

    - Time and skills needed to understand how the code works 
    - Direcly proportional with software complexity and size 

    b. **Stealth > identifiability of obfuscated code** 

     - Time and computation needed to identify the parts of the code which were obfuscated

    c. **Resilience > Resistance against automatic deobfuscation**
        
    - Time and computation needed to deobfuscate the code with a software tool (automated approach)

    -  Plus resources needed to build such a tool 

    d. **Cost > performance and resource overhead of obfuscation** 
    
    -  Time overhead added to program execution after obfuscation 
    -  Size of the obfuscated binary relative to original binarys

2. Explain in 3-5 sentences why it is important for a software developer to be able to predict the strength of the software obfuscation applied to her program. 2P

    - Some algorithms should be secret at some point since it makes the software unique from others, without good  implementation of obfuscation,  the code can be reversed easily. In order to protect, sensitive information and algorithms, the strength of the program should be high. Higher strength means more resilience. 

## Opaqueness 

1. What is the main difference between an opaque predicate and an opaque expression, fromt the point of view of the values they can evalute to? 2P 

    - Opeaque predicates are used to protect intellectual property
    - Opeque expressions are used to protect secret data 



## Dynamic Obfuscation Transformations 

1. Describe in 2-3 sentences each of the phases of dynamic obfuscation (self-modifying code). 2P

    - At compile-time 
        - Transform the program to an initial configuration 
        - Add a runtime code-transformer
    - At runtime
        - Interleave execution of the program with calls to the transdformer T 
        - T changes the code segment content at runtime
        - Ideally a non-repeating series of configurations, in practice they repeat

2. Describe the steps of the Dynamic Decryption and Re-encryption obfuscation transformation.

    - Execute current basic block 
    - At some point in the current basic block decrypt the next basic block
    - Decryption key could be hash of some other basic block 
    - Jump to decrypted basic block 
    - Encrypt the previously executed basic block 
    - Go to step 1


3. For the functions f1, f2 and f3 (represented using their binary representation in memory below), create and illustrate one template that fits all 3 functions and write the corresponding edit scripts. 3P


> f1

|memory offset|	0 |	1| 	2|	3|	4|	5|	6|
|:-----------:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|memory value|	0x15|	0xaf|	0xe3|	0x45|	0xef|	0x54|	0x42|


> f2

|memory offset|	0 |	1| 	2|	3|
|:-----------:|:----:|:----:|:----:|:----:|
|memory value|	0x15|	0xaf|	0xb3|	0x45|

> f3 

|memory offset|	0 |	1| 	2|	3|	4|
|:-----------:|:----:|:----:|:----:|:----:|:----:|
|memory value|	0x98|	0xaf|	0x1a|	0x45|	0xef|

> Solution

``` 
e_1  = [ 0> 0x15 , 2 > 0xe3, 5> 0x54, 6> 0x42  ]
e_2 =  [ 0> 0x15, 2>0xb3 ] 
e_3 = [ 0> 0x98, 2>0x1a, 4 > 0xef ] 
```

