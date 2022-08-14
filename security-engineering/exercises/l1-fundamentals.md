# Lecture 1 

## Fundamentals

1. Is there a difference between privacy and confidentiality ?

- There are some differences between privacy and confidentiality. Privacy an be applied to individuals whereas confidentiality is applied to the information. Confidentiality means that private information between some entities should not be disclosed to public or known by other parties who should not learn. 

> Privacy is associated with protecting personal data from disclosure (upon the request of the user). e.g address, DOB, search queries, shopping patterns, etc.

> Confidentiality protects information  e.g passwords, bank balance


2. How are security and safety different from each other ? How are they similar ?

- Safety and security are fundamentally aim same purpose in different ways. Security is about preventing any unwanted or malicious activities that may happen in the system. Safety is more about reliability of the system, how is it reliable against failures, it is about knowing whether the application/system is safe to use. 

> **Safety**: 
>   - Is the system doing harm to its environment ?
>    - Failures materialize as a consequence of normal and abnormal operations 
>   - Systematic and random errors; the latter modeled with stochastic processes 

> **Security**:
> - Is the environment doint harm to the system ? 
> - Malicious entity uses flaws in system to do harm 



3. Before we signed the contract for the CISO position, we were asked if we could create an online banking system that is 100% secure. Is it realistic ?

- There is no such a system which is 100% secure. We can only say this system is secure against this kind of attack or against some set of situations. It is definitely not realistic to say any system 100% secure. 


> The major distinction between security and safety is the trigger of failures
>   - A stochastic process for safety 
>   - An adversary/hacker for security

> They are similar in that they consider **all possible** failures and their reasons/occurences. 

## Security Principles 

1. Name at least five principles, describe them in one sentence and find examples in which these principles have been violated or ensured. 

- **Least Privilege**
    - Every subject should not have more privileges thann necesseary to complete the job 
    - Example
        - Providing extra permission such as write access to a db for someone who actually only needs read 

- **Complete Mediation**
    - Access to every object must be controlled in an way not circumventable
    - Airports ensure that every subject is checked before entering sensitive areas like planes

- **Secure, fail-safe defaults/implicit deny**
    - Security mechanism should start in a secure state and return to a secure state in case of failures 
    - Firewalls use white-lists rather than black-lists 
    - Clean up after crashes 
    - Doors to buildings lock when closed. 

- **Open Design**
    - The security of a mechanism should not depend on the secrecy of its design or implementation 
    - Most modern cryptographic schemes honor "Kerckhoff's Principle" which encourages open design. The internal structure of schemes like DES, AES, RSA etc are published. Only the key(s) remain secret. 
    - Use established standards for encryption
    - Use established protocols

- **Defense in Depth**
    - A system should employ multiple layers of security mechanisms to hinder any potential attacks. 
    - 2FA with password and mobileTAN. If an attacker manages to guess/retrieve the password,they still need to overcome the next later which implies getting access to a cell phone within a limited amount of time, rendering the attack quite unlikely. 


2. What is the principle of Open Design ? What are the (dis)advantages of implementing the principle ? 

Open design principle is basically using approaches which are publicly proved, supported and updated. The design of the system should not depend on implementation secrecy of the system. 

> **Open Design** 
    > The security of a mechanism should not depend on the secrecy of its design or implementation 
> **Advantages**
    > Encourages security by design = discourages securiy by obscurity 
    > Enables study by security community e.g gray-hat hackers
    > (in some cases ) makes the system more usable 

> **Disadvantages**
    > Prevents strorage of secrets within the system, e.g licence keys
    > Facilitates vulnerability discovery for black-hat hackers, e.g heartbleed


3. The figure below depicts the result of port-scanning a web server using NMAP. What is the principle that this server maintains/violates? Why?

![](../.gitbook/assets/nmap.png)

It validates **minimum exposure security** principle, because it is possible to retrieve information about the system. Provides shadow of the system by listing open/closed ports, some other service names and etc. 

> **Minimum Exposure**
    > Minimize the **attack surface** a system presents to the potential adversary 
    > .... includes aspect like: reduce external interfaces to a minimum 
    > Example: Harden OS by disabling all unneeded functionality. Eg. FTP ports


4. Name two conflicting security principles, i.e abiding by one principle during design tends to violate the other. Motivate with an example. 

> **Defense in Depth**
  > A system should employ multiple layers of security mechanisms to hinder any potential attacks
> **Psychological Acceptability**
  > Security mechanisms should not make the resource more difficult to access than if the security mechanisms were not present. 

> **Example**
    > Multi-factor authentication 
    > More factors = more security layers 
    > E.g password cracked ? Still need TAN
    > Harder/slower to access system > less usable > less acceptable 

5. When the bank hired us to become the bank's new CISO, the bank's current computer system's architecture was shown to us. Additional, we received some explanations

The clients used their ID and password to authenticate. The credentials are sent via the internet to the bank's network. Hereby, state-of-the-art encryption is used and the implementation of the website and the part of the backend responsible for the authentication was audited by external and independent experts.

A firewall is used. The firewall holds a list of suspicious ports. If an external component is trying to communicate with a machine within the internal network via one of the suspicious ports, the connection is blocked. In the past, there have been some problems with accessing the mailing server when working from home. Thus, connections to the mailing are no longer routed via the firewall, but directly to the internal network.

![](../.gitbook/assets/bank_net.png)


To keep the internal network as simple as possible, there is just one internal network connecting the servers and the PCs of the employees.

We were asked to write a small report about the current architecture.

Which principles have been incorporated in the current architecture?

> - Only ID and password need > economy of design, psychological acceptability 
> - Checked by external experts > Open Design 

Which principles have been neglected? What are potential problems resulting from the neglected principles?

> - Only ID and password need > Defense in depth
> - Firewall does not apply to the mailing server > complete mediation, minimum exposure
> - Firewall uses a blacklist > Secure, fail-safe defaults/implicit deny
> - One network > Defense in depth, compartmentalization

> Potential problems
    > Attacker can do harm ony with ID and password, not that hard to get
    > Firewall should be harder to compromise than the mailing server 
    > If we were an attacker we would not attack the firewall, but rather try to find a flaw in the mailing server

