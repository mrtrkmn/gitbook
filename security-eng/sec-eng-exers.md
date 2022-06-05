### Security Principles Q

1. Name at least five principles, describe them in one sentence and find examples in which these principles have been violated or ensured.

2. What is the principle of Open Design? What are the (dis)advantages of implementing this principle?

3. The figure below depicts the result of port-scanning a web server using NMAP. What is the principle that this server maintains/violates? Why?



4. Name two conflicting security principles, i.e., abiding by one principle during design tends to violate the other. Motivate with an example.

When the bank hired us to become the bank's new CISO, the bank's current computer system's architecture was shown to us. Additional, we received some explanations

	The clients used their ID and password to authenticate. The credentials are sent via the internet to the bank's network. Hereby, state-of-the-art encryption is used and the implementation of the website and the part of the backend responsible for the authentication was audited by external and independent experts.

	A firewall is used. The firewall holds a list of suspicious ports. If an external component is trying to communicate with a machine within the internal network via one of the suspicious ports, the connection is blocked. In the past, there have been some problems with accessing the mailing server when working from home. Thus, connections to the mailing are no longer routed via the firewall, but directly to the internal network.

	To keep the internal network as simple as possible, there is just one internal network connecting the servers and the PCs of the employees.

We were asked to write a small report about the current architecture.

Which principles have been incorporated in the current architecture?

Which principles have been neglected? What are potential problems resulting from the neglected principles?

![](../.github/assets/sec-ex-1-img.png)



## Security Principles ANS



1. 
	a.  Least Privilege
		- Every subject should not have more privileges than necessary to complete its job
		
		- Example;
			- Providing extra permission such as write access to db for someone who actually only needs read access

	b.  Complete Mediation
		- Access to every object must be controlled in an way not circumventable.
		> Airports ensure that every subject is checked before entering sensitive areas like planes

	c. Secure, fail-safe defaults/implicit deny
		- Secuirty mechanisms should start in a secure state and return to a secure state in case of failures.
		> Firewalls use white-lists rather than black-lists
		> Clean up after crashes
		> Doors to buildings lock when closed.

	d. Open Design
		- The security of a mechanism should not depend on the secrecy of its design or implementation
		> Most moden cryptographic schemes honor "Kerckhoff's Principle" which encourages open design. The internal structure of schemes like DES, AES, RSA etc are published. Only the key(s) remain secret.
		> Use established standards for encryption
		> Use established protocols

	e.  Defense in Depth
		- A system should employ multiple layers of security mechanisms to hinder any potential attacks
		> 2FA with password and mobileTAN. If an attacker manages to guess/retieve the passsword, they still need to overcome the next later which implies getting access to a cell phone within a limited amount of time, rendering the attack quite unlikely.

	
2. Open design principle is basically using approaches which are publicly proved, supported and updated. The design of the system should not depend on implementation secrecy of the system. 
Advantages, when open design is preffered, vulnerabilities, problems or unforeseen errors can be reported from the community. There is a huge power of community, where anyone at any time can check any flaws or other content. 

3. It violates minimum exposure security principle, because it is possible to retrieve information about the system. Provides shadow of the system by listing open/closed ports, some other service names and etc. 

4. Economy of design and Defense in depth, they are defending two seperate points, at some cases they may contradict.



5. 

	Complete mediation, fail-safe defaults/implicit deny, compartmentalization security principles are incorporated.

	Minimum exposure, least common mechanism security principles are neglected. 

	Potential problems could be gaining more information about the bank, since there are some "suspicious" ports are blocked others might be accessible. They share access resources with third parties, it may create further problems when third party security principles are not in place. 
