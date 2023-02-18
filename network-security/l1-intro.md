# L1-Introduction

# Attack Types 

## Passive Attacks (= “observation”)
- Eavesdropping of messages
- Traffic Analysis

## Active attacks (= “observation + manipulation”)
- All passive attacks
- Delay
- Replay
- Deletion
- Modification
- Insertion


## Dolev-Yao attacker model
- The attacker is or owns the network (all routers, switches, connections)
- The attacker can perform any active and passive attack
- The attacker has no control over end systems
- The attacker cannot break cryptographic primitives (encryption, signing, hashing, etc.)

## Security Goals

### Confidentiality
    - German: “Vertraulichkeit”
    - Information must be concealed → Attacker cannot read/understand information
    - Example: Encrypt information with a symmetric cipher
### Data Integrity
    - German: “Datenintegrität”
    - Changes to data must be noticeable → Attacker cannot modify data without being detected
    - Example: Hash value (“fingerprint”) of a file stored on a public server.
    - The fingerprint is stored at some secure location
### Authenticity (of data/of a communication partner)
    - German: “Echtheit”
    - We must know who the originator of data is/who our communication partner is
    - Example: Digital signature over the hash of a file authenticates the hash (and the file)/ a challenge/response protocol authenticates our communication partner
### Controlled Access
    - German: “Zugriffskontrolle”
    - Only authorized entities can access certain services or information
    - Example: Employ an access control system, firewall, etc.
### Accountability
    - German: “Zurechenbarkeit”
    - Identify the entity responsible for a (communication) event/change at a file/...
    - Example: Employ a logging system of some sort
### Availability
    - German: “Verfügbarkeit”
    - Services/data/... must be available and function correctly
    - Example: Important services/data shall be replicated/stored redundandly


### Integrity vs. Authenticity
    - Integrity: "Proves that data item did not change"
    - Authenticity: "Proves that data item was created by user x"
    - Authenticity of data implies integrity

### Authentication vs. Authorization
    - Authentication: "Authenticity of user, i.e., find out identity of user"
    - Authorization: "Find out whether a user is allowed to perform an action"
    - Access control systems enforce controlled access
    - Step 1: Authenticate user
    - Step 2: Authorize user
    - Do not confuse authentication and authorization

## Threats 

    - A threat in a communication network is any possible event or sequence of actions that might exploit a vulnerability, leading to a violation of one or more security goals
    - Vulnerability: A design flaw in a cryptographic protocol, a programming error, etc. which exists in a system
    - Threat: The possibility that somebody abuses a vulnerability
    - Attack: The actual realization of a threat

### Threats - Classification

#### Impersonation:
    - An entity claims to be another entity (also called “masquerade”)
#### Forgery of information:
    - An entity creates new information in the name of another entity
#### Modification or loss of (transmitted) information: 
    - Data is being altered or destroyed
#### Repudiation
    - An entity falsely denies its participation in a communication act
#### Eavesdropping:
    - An entity reads information it is not intended to read
#### Authorization Violation:
    - An entity uses a service or resources it is not intended to use
#### Denial of Service (Sabotage):
    - Any action that aims to reduce the availability and / or correct functioning of services or systems


#### Impersonation + Forgery of Information 
##### Example:
    - Attack: Alice pings Carl and pretends to be Bob
    - Alice@Box$ hping3 –count 1 –spoof $BOB –icmp –icmptype 8 $CARL
    - hping3 “is a network tool able to send custom TCP/IP packets...”
    - CARL gets an ICMP Echo Request which appears to be sent from BOB
    - BOB gets an ICMP Echo Reply which he never requested
    - Alice is an active attacker
    - IP (source) addresses are not secured → IP Spoofing


