IPv4
====

→ Network Layer

*   L3/IP service goal: forward IP datagrams to destination IP subnet/host/interface
*   IP address has role of locator & identifier:

*   Network part (network identifier & locator)
*   Host part (host identifier)

*   Each IP network (often called subnetwork or subnet) has an IP address

*   IP address of a network = Host number is set to all zeros, e.g 128.143.0.0

*   IP routers are devices that forward IP datagrams between IP networks
*   Delivery of an IP datagram proceeds in 2 steps:

*   Use network prefix to deliver IP datagram to the right network
*   Once the network is reached, use the host L3 address to deliver to the right interface

→ IP Protocol

*   Addressing conventions
*   Datagram format
*   Packet handling conventions

→ Routing protocols

*   Path selection

*   RIP, OSPF, BGP

→ ICMP protocol

*   Error reporting
*   Router "signaling"

→ IPv4 Datagram

![](../gitbook/assets/acn-notes-figures/image94.png)

*   IHL : Internet Header Length
*   TOS: Type of service
*   TTL: Time to live

![](../gitbook/assets/acn-notes-figures/image98.png)

![](../gitbook/assets/acn-notes-figures/image102.png)

→ IPv4 addressing

*   IP address: 32-bit identifier for host , router interface
*   Address space: 4.3 billion  IPv4 addresses in theory ( 2^32 )
*   Interface: connection between host/router  and physical link

*   IP addresses associated with each interface

→  IP address notation :  4 numbers from 0 to 255  separated by dots

→ Subnets

*   Device interfaces with same subnet part of IP address
*   Can physically reach each other without intervening router

→ Splitting IP addresses ![](../gitbook/assets/acn-notes-figures/image77.png)

*   Network part: Addressing the network
*   Host part: Addressing the interface to host

![](../gitbook/assets/acn-notes-figures/image10.png)

→ Classless IP addresses

*   CIDR : C lassless I nterDomain Routing (introduced in 1993 until then above fig. used)
*   Idea:  introduction of arbitrary subnet length
*   Address format: a.b.c.d/x, where x corresponds to the number of bits in subnet portion of address

→ Example CIDR

*   How to calculate the network address for interface address 192.168.128.1 with a prefix length of 17 bits?

*   CIDR notation : 192.168.128.1/17
*   Dotted decimal notation: 192.168.128.1/255.255.128.0 ![](../gitbook/assets/acn-notes-figures/image19.png)

→ IPv4 address exhaustion

*   IPv4 addresses are rare a resource nowadays

*   Inefficiency of Classful Internet Routing

*   Class C (256 addresses) too small for small enterprises
*   Class B (65536 addresses) too small for large enterprises or universities
*   Class A (16 million addresses) too large

*   Rise of internet-connected devices

*   Personal computers, mobile phones, Internet-of-things

*   Always-on devices

*   Sharing of IPv4 addresses become less viable

→ Various solutions proposed, the most notable one being private addresses:

*   10.0.0.0/8 - 24-bit block
*   172.16.0.0/12 - 20 bit block
*   192.168.0.0/16 - 16-bit block

→ ICMP  

*   Network control plane protocol above "IP"

*   ICMP messages carried in IP datagrams
*   Can be considered part of the IP layer

*   Communicates error messages and other conditions that require attention
*   Error messages are acted on by either…

*   IP Layer, or
*   TCP or UDP

*   Some ICMP messages cause error notifications to be returned to user processes

![](../gitbook/assets/acn-notes-figures/image51.png)

Two classes of ICMP messages:

*   Query messages

*   Only kind of ICMP messages that generate another ICMP message

*   Error messages

*   Contain IP header and at least first 8 bytes of datagram that caused the ICMP error to be generated
*   Allows receiving ICMP module to associate the message with a particular protocol and process (port number)

→ ICMP Message Types

![](../gitbook/assets/acn-notes-figures/image34.png)

*   ICMP should contain as much data of the dropped message as possible up to a limit of 572 byte for the ICMP message.

→ ICMP

→  Ping

*   Checks if host is reachable, alive
*   Uses ICMP echo request/reply
*   Copy packet data request reply ![](../gitbook/assets/acn-notes-figures/image56.png)

→ Traceroute

*   Allows to follow path taken by packet
*   Send UDP/TCP/…. packets with increasing TTL to (unlikely) port
*   ICMP replies: "time exceeded"; last ICMP message: "port unreachable"

      → Possible anomalies due to load balancing

      → Per connection load balancing

*   Hash consistently and use packet headers as random values

*   Packets from same TCP connection yield same hash value
*   No reordering within one TCP connection

![](../gitbook/assets/acn-notes-figures/image84.png)

→ PARIS TRACEROUTE

*   Idea: Vary header fields that are within the first 28 octets

*   TCP:sequence number
*   UDP: checksum field

*   Requires manipulation of payload to ensure correctness of checksum

*   ICMP: combination of ICMP identifier and sequence number

*   Experiment results

*   Certain routers use first four octets after IP header combined with IP fields for load balancing

*   Still fails on per packet load balancing

*   MDA\[4\] tries to cover this problem

There are further interesting traceroute tools, e.g.:

*    yarrp \[5\]

• Stateless

• Highly parallel

*   Scamper \[6\]

*   All-in-one tool
*   IPv4 & IPv6
*   Built-in alias resolution

*   MDA \[4\]

*   Tries to identify all possible paths
*   Crafts specific packets to find new paths
*   Large overhead

*   MDA-Lite \[7\]

*   Optimized MDA implementation
*   Trade off between performance and completeness

→ ARP  ( MAC addresses and IP addresses)

*   MAC (or LAN or physical or Ethernet) address

*   L2 service: transmit frame from one interface to another physically-connected interface (same network) with specified destination address
*   Address length: 48 bit ( for most LANs)

*   Burned into network adapter ROM, or software settable
*   Assumption: two hosts on the same LAN will not use the same Ethernet address

*   IP address: network-layer address

*   L3 service: get datagram to destination IP subnet/ host I/F
*   L3 address: has role of locator & identifier (vs. HIP - Host Identity Protocol; LISP- Locator/ID Separator Protocol)
*   Address length: 32 bit (ipv4) or 128 bit (ipv6)
*   Address separated into:

*   Network part (i.e network identifier & locator)
*   Host part (i.e host identifier)

→ ARP - ADDRESS RESOLUTION

*   Mapping between addresses of different layers

*   IPv4 → MAC
*   MAC → IPv4

*   Mapping from L3 host address to MAC address

*   Needed to identify correct L2 adapter of L3 address

→ Address Resolution Protocol (ARP)

*   Mapping from MAC address to L3 address

*   Reverse Address Resolution Protocol (rarely used)

![](../gitbook/assets/acn-notes-figures/image95.png)

*   Example send datagram from A to B via R (assuming A knows B's IP address)
*   The router manages two ARP tables one for Net 1 and one for Net 2

![](../gitbook/assets/acn-notes-figures/image88.png)

*   A creates IP datagram with source IP addr. A, destination IP addr. B
*   A uses ARP to get R's MAC address of R's interface 10.0.10.1
*   A creates link-layer frame with R's MAC address as destination, frame contains A-to-B IP datagram
*   A's NIC sends frame
*   R's NIC receives frame
*   R extracts IP datagram from Ethernet frame, sees it is destined to B
*   R uses ARP to get B's MAC address
*   R creases frame containing A-to-B IP datagram, send it to B

→ ARP protocol (Same LAN network)

*   A wants to send datagram to R's interface 10.0.10.1, while R's MAC address is not in A's ARP table

*   A broadcasts ARP query packet, containing R's IP address

*   Destination MAC address = FF-FF-FF-FF-FF-FF
*   All hosts on LAN receive ARP query

*   When R receives ARP packet, it replies to A with its (R's) MAC address

*   Frame sent to A's MAC address

*   A caches IP-to-MAC address pair in its ARP table until information times out

*   Soft state: information that times out (goes away) unless refreshed

*   ARP is "plug-and-play"

*   Nodes create their ARP tables without intervention from network administrator

→ ARP PACKET FORMAT

![](../gitbook/assets/acn-notes-figures/image79.png)

→ ARP Details

*   ARP supports different protocols at L2 and L3

*   Any network protocol over any LAN/MAC protocol
*   Type and address length fields specified in ARP PDUs

*   Reserve ARP (RARP)
*   L2 MAC fields (hardware)

*   Hardware type: 6: IEEE82 (with LLC/SNAP)
*   Address length: 6 for a 6 byte long MAC address
*   Sender hardware address (SHA)
*   Target hardware address (THA)

*   L3 network fields (protocol)

*   Protocol type: IP = 0800
*   Address length: 4 for 4 byte long IPv4 address
*   Sender protocol address (SPA)
*   Target protocol address (TPA)

*   Operation Code

*   01: request
*   02: reply
*   03: reverse request
*   04: reverse reply (for RARP)

→ PROXY ARP

*   Proxy ARP: Host or router responds to ARP Request that arrives from one of its connected networks for a host that is on another of its connected networks
*   RFC 925: Multi-LAN Address Resolution

![](../gitbook/assets/acn-notes-figures/image80.png)

– Use cases:

*   Transparent subnet gatewaying

*   Two LANs sharing same IP subnet, connected via router
*   RFC 1027- Using ARP to implement Transparent Subnet Gateways

*   Host joining LAN via dialup link

*   Dialup router employs proxy ARP

*   Host joining LAN via VPN

*   VPN server employs Proxy ARP

*   Host separated via firewall

*   Firewall employs Proxy ARP

→ When should a host send ARP requests ?

*   Before sending each IP packet

*   No, each host/router maintains ARP table ( IP address → MAC address mapping)
*   ARP request is only sent in case there is no entry for this IP address in the ARP table

→ How to deal with hosts that change their addresses ?

*   Expiration timer is associated to each entry in the ARP table

*   ARP table entry is removed upon timer expiration
*   Some implementations send ARP request to revalidate before removing table entry
*   Some implementations remember when ARP table entries were used to avoid removing important entries.

→ What happens if an ARP request is made for a non-existing host?

*   Several ARP requests are made with increasing time intervals between requests
*   Eventually, ARP gives up

→ Gratuitous ARP requests

*   A host sends an ARP request for its own IP address
*   Useful for detecting if an IP address has already been assigned

→ VULNERABILITIES OF ARP

1.  Since ARP does not authenticate requests or replies, ARP requests and replies can be forged
2.  ARP is stateless: ARP replies can be sent without a corresponding ARP request
3.  According to the ARP protocol specification, a node receiving an ARP packet (request or reply) must update its local ARP cache with the information in the sender fields. Updates also happen if the receiving node already has an entry for the IP address of the sender in its ARP cache. (This applies for ARP request packets and for ARP Reply packets )

→ Typical exploitation of these vulnerabilities

*   A forged ARP request or reply can be used to update the ARP cache of a remote system with a forged entry ( ARP Poisoning )
*   This can be used to redirect IP traffic from/to other hosts
*   ARP poisoning & ARP spoofing also can be performed by hosts within a WPA2-protected WLAN

→ Routers vs Switches

*   Both store-and-forward devices

*   routers: L3/network layer devices (examine network layer headers)
*   Switches: L2/link layer devices

*   Switches:

*   Maintain switching tables
*   Implement filtering, learning algorithms
*   May implement spanning tree algorithm
*   Switch L2 frames based on switching table entries & destination MAC address

*   Routers

*   Maintain forwarding tables
*   Implement routing protocols
*   Forward IP packets based on forwarding table entries & destination IP address

→ Forwarding: data plane

*   Directing a data packet to an outgoing link
*   Individual router using a forwarding table

→ Routing: control plane

*   Computing the paths the packets will follow
*   Individual router creates a forwarding table

→ Routing protocols (e.g RIP, OSBF, BGP)

*   Distributed routing protocol entities in routers talking amongst themselves (above IP)

→ Routing in Software Defined Networking (SDN)

*   Router may receive forwarding and/or routing information via SDN control plane
*   Control plane might not necessarily be inside the router

![](../gitbook/assets/acn-notes-figures/image28.png)

→ Routing functions include:

*   Route calculation
*   Execution of routing protocols
*   Maintenance of routing state
*   Maintenance of forwarding table

→ On commercial routers handled by a single general purpose processor, called routing processor.

→ IP forwarding is per-packet processing

*   On high-end commercial routers, IP forwarding is distributed (Most work is done on the interface cards ) ![](../gitbook/assets/acn-notes-figures/image13.png)

→ Two key router functions

*   Run routing algorithms/protocol (RIP, OSPF, BGP)
*   Forwarding datagrams from incoming to outgoing link
