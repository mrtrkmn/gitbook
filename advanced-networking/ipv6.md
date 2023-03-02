IPv6
====

→ Problems with IPv4

*   Address space is too small.
*   IPv4 addresses are not end-to-end associative anymore

→ Motivation:

*   IPv6 designed as successor to IPv4
*   IPv4 and IPv6 are not compatible by design

→ Goals

*   Better scalability

*   Larger address space size

*   Easier development

*   Simplified header, easier implementation
*   Better auto-configuration (SLAAC)
*   Updated stateful configuration (DHCPv6)

*   Easier analysis

*   Better flow associativity

→ Addresses

*   IPv6 routinely allows each interface to be identified by several addresses

*   Usually only one IPv4 address per interface

*   IPv6 addresses use 128 bit vs 32 bits for IPv4

→ Addresses Representation

*   An IPv6 address is represented as 8 groups of 4 hexadecimal digits (16 bits), separated by a colon (:)

*   Example: 2001:0db8:85a3:0000:0000:8a2e:0370:7334

*   Leading zeros in a group may be omitted, but each group must retain at least one hexadecimal digit

*   2001: 0 db8:85a3: 000 0: 000 0:8a2e: 0 370:7334 → 2001:db8:85a3:0:0:8a2e:370:7334

*   One or more consecutive groups of zero value may be replaced with a single empty group using two consecutive colons (::), but the substitution may only be applied once in the address:

*   2001:db8:85a3: 0:0 :8a2e:370:7334 → 2001:db8:85a3::8a2e:370:7334
*   The localhost (loopback) address 0:0:0:0:0:0:0:1 is written as ::1
*   Representations are shortened as much as possible. The longest sequence of consecutive all-zero fields is replaced by a double-colon. ![](../gitbook/assets/acn-notes-figures/image20.png)

![](../gitbook/assets/acn-notes-figures/image12.png)

→ The IPv4 CIDR notation is also used for IPv6

*   address/prefix  → 2001:db8::1/64

*   The design of the IPv6 address space implements a very different design philosophy than in IPv4
*   In IPv6, the address space is deemed large enough for the foreseeable future, and a local area subnet always uses 64 bits for the host portion of the address, designated as the interface identifier, while the most-significant 64 bits are used as the routing prefix.

*   First n bits : Global routing prefix
*   Next 64 - n bits : Subnet ID
*   Last 64 bits : Interface ID

→ ADDRESS TYPES

*   Unicast: From one sender to exactly one receiver
*   Multicast: From one sender to all (multiples or one) members in a group
*   Anycast: From one sender to one member of a group
*   Broadcast: Not used in IPv6

→ Global-Unique IPv6 Addresses

*   Globally unique and globally addressable

→ Local-Unique IPv6 Addresses

*   Locally addressable
*   Highly likely globally unique
*   Part of fc00::/7 subnet

→ Link-Local IPv6 Addresses

*   Addressable on the link
*   Can be globally unique but only have to be unique on the link
*   Part of the fe80::/10 subnet

→ Site-Local IPv6 Addresses

*   Developed at the beginning of IPv6, but dropped since then

→ \*\* MULTICAST ADDRESSES

*   First 8 bits set to 11111111
*   Next 4 bits as flag (permanent or transient address)
*   Next 4 bits as scope:

*   0000 Reserved
*   0001 Interface local
*   0010 Link local
*   1000 Organization local
*   1110 Global
*   1111 Reserved

*   Last 112 bits: Group ID

      → Predefined IPv6 Multicast Addresses

*   All nodes multicast

*   ff01::1 (interface-local)
*   ff02::1 (link-local)
*   In IPv4 224.0.0.1 is used

*   All routers multicast

*   ff01::2 (interface-local)
*   ff02::2 (link-local)
*   In IPv4 224.0.0.2 is used

→ IPV6 HEADER FORMAT

→ Reminder from IPv4

![](../gitbook/assets/acn-notes-figures/image45.png)

![](../gitbook/assets/acn-notes-figures/image87.png)

![](../gitbook/assets/acn-notes-figures/image104.png)

→ IPv6 Flow Label

*   20 bit Flow Label field to identify specific flows needing special QoS
*   Traditional IPv4 way of specifying flows

*   5 tuple: source and destination IP addresses, source and destination port numbers, and protocol type

*   Some of these fields may be unavailable due to fragmentation, encryption, or locating them past extension headers
*   With flow labels, each source chooses its own flow label value.  Routers use IPv6 source address + flow label to identify distinct flows

→ Extensions

![](../gitbook/assets/acn-notes-figures/image89.png)

![](../gitbook/assets/acn-notes-figures/image76.png)

→ Hop-by-hop Options header

*   TLV coded options processed by every hop along the path
*   Jumbo payload option for packets larger than 65535 bytes
*   Router alert option

→ Routing header

*   Strict or loose source routing
*   Similar to the IPv4 Source route and Record route options

→ Fragment header

*   Only source can fragment packets in IPv6
*   Source must use Path MTU Discovery or send max 1240 bytes payload
*   Fragmentation information:

*   Fragmentation offset shifted (as in IPv4)
*   Fragmentation ID is 32 bits (16 bits in IPv4)

→ ⬇️ Fragmentation extension

![](../gitbook/assets/acn-notes-figures/image96.png)

→ Authentication header(IPSEC)

*   To validate the message sender and ensure integrity of data

→ Encapsulated Security Payload  header (IPSEC)

*   To provide confidentiality and guard against eavesdropping

→ Destination Options header

*   TLV coded options processed by destination only

→ Mobility header

*   Parameters used with Mobile IPv6

→ Host Identity Protocol (HIP)

*   For enabling continuity of communications across IP address changes

→ Shim6 Protocol

*   Multihoming Shim Protocol for IPv6 with failover and load-sharing properties.

→ Auto-configuration

*   Address resolution for ICMPv6

*   ICMP has been revised along with the IPv6 development, with a new version: ICMPv6
*   IPv6 does not use ARP but neighbor detection scheme based on ICMPv6: Neighbor Discovery Protocol

→ Neighbor Discovery Protocol

*   IPv4 ARP Equivalent
*   Resolve IPv6 addresses to MAC addresses
*   Add parts for information about routers

→ Realization

*   Part of ICMPv6
*   Split into  "Neighbor Solicitation"  and "Neighbor Advertisement"

→ Neighbor Solicitation

*   Ask for the MAC address of the interface configured for a given IPv6 address
*   Destination IPv6 address ("Solicited Node Address"):

*   ff02::1:ff XX:XXXX
*   Insert lowest 24 bits of the given IPv6 address at the end of the destination IPv6 address [\[a\]](#cmnt1)

*   Destination MAC address:

*   33-33- XX-XX-XX-XX
*   Insert lowest 32 bits of the "Solicited Node Address"

To determine the lower 24 bits of an IPv6 address by hand, you can follow these steps:

1.  Take the last 4 hexadecimal characters of the IPv6 address, which represent the last 32 bits of the address.
2.  Convert the hexadecimal value to binary.
3.  Extract the last 24 bits of the binary representation.

Here's an example:

Given the IPv6 address: 2001:0db8:85a3:0000:0000:8a2e:0370:7334

1.  Last 4 hexadecimal characters: 7334
2.  In binary: 011 1001100110100
3.  Last 24 bits: 100110100110100

Note that this method only works for the lower 24 bits of the last block of an IPv6 address. To determine the lower 24 bits of a different portion of the address, you would need to follow a similar process, converting the relevant hexadecimal characters to binary and extracting the desired bits.

→ NEIGHBOR ADVERTISEMENT

*   Answer a Neighbor Solicitation
*   Use MAC and IPv6 addresses of the destination host

![](../gitbook/assets/acn-notes-figures/image93.png)

![](../gitbook/assets/acn-notes-figures/image26.png)

Router Solicitation (RS)

*   Prompt all routers on this segment to send a Router Advertisement
*   Normally sent when interface comes up  
    Router Advertisement (RA)

*   Sent to the all-nodes multicast address in fixed intervals by all routers
*   Contains Information about the network segment:

*   Autoconfiguration methods (SLAAC, DHCPv6)
*   Prefix Information
*   Route Information
*   MTU on link
*   Link-Layer address of the router

Address resolution and ICMPv6

*   ICMP has been revised along with the development IPv6, with a new version: ICMPv6 (RFC4443)
*   IPv6 does not use ARP but a neighbor detection scheme based on ICMPv6: Neighbor Discovery Protocol (RFC4861)
*   ICMPv6 support additional services:

*   Secure Neighbor Discovery (SEND)  is an extension of NDP with extra security
*   Multicast Listener Discovery (MLD) is used by IPv6 routers for discovering multicast listeners on a directly attached link
*   Multicast Router Discovery (MRD) allows discovery of multicast routers

*   Everybody can claim to be a router

*   Use RA Guard to filter unauthorized RAs (RFC 6105)
*   Secure Neighbor Discovery (SEND)  is an extension of NDP with extra security (RFC 3971)

Stateless auto-configuration / Serverless

• Automatic configuration of link-local addresses on system startup

![](../gitbook/assets/acn-notes-figures/image101.png)

Use case

• Automatic configuration of link-local address

→ Procedure

1.  Create EUI-64 Address

1.  Always in subnet fe80/64
2.  First 24 bit of interface identifier: First 24 bit of MAC address (flip second bit of the first octet)
3.  "Middle" 16 bit: Always ff:fe
4.  Last 24 bit: Last 24 bit of MAC address

2.  Perform duplicate address detection
3.  Configure Address to interface

→ StateLess Address AutoConfiguration

*   Use link-local address and interface ID
*   Hosts join all-nodes multicast address (ff02::1)
*   Hosts do DAD with all nodes based on multicast address
*   Hosts communicate to routers using all-routers multicast address (ff02::2)
*   ICMPv6  router solicitation sent by host to request additional information
*   ICMPv6  router advertisement  sent by router to inform host about prefixes for site and global addresses

*   SLAAC uses a modified MAC address, which makes it possible to trace a device

*   RFC 4941 "Privacy Extensions"
*   Use random 64 bit number for the host part
*   Change the number regularly

→ Stateful configuration (managed)

• Flag in router advertisement tells whether to rely on auto-configuration or to use conventional managed configuration → DHCPv6

→ DHCPv6

*   SLAAC and router advertisements can configure an IPv6 host and provide connectivity.

*   Why do we need DHCPv6 ?

*   Can be used to provide prefix information
*   Can be used to provide fixed addresses to device identifiers
*   Can be used to provide DNS information
*   Has to be used to provide boot information for Netboot

→ IPv4 to IPv6 Transition

– Because of the large number of systems and actors on the Internet, the transition from IPv4 to IPv6 cannot happen suddenly.

Three transition strategies have been devised by IETF:

*   Dual Stack

*   All hosts have dual IPv4 and IPv6 stack of protocols until all of the internet runs IPv6
*   Avoids the complexities of tunneling, such as security, increased latency, management overhead

        → Approach

*   Assign each end-user one public IPv4 address and one public IPv6 subnet
*   End device chooses to use IPv4 or IPv6
*   Both networks are directly accessible

        → Problem

*   IPv4 addresses might already be exhausted
*   Supporting IPv4 and IPv6 inside the ISP network at the same time is expensive and complex

        → Solutions

*   No solution for address exhaustion in full Dual Stack (see DS Lite)
*   ISPs can transparently tunnel IPv4 in IPv6 (or the other way round), and only setup one network, which provides IPv4 and IPv6

*   Dual Stack Lite

→ Approach

*   Same as full Dual Stack, but private instead of public IPv4 address
*   Deployment of a Carrier-Grade-NAT

→ Problems

*   Peer-to-peer communication almost impossible
*   Mostly affects VoIP and gaming

→ Tunneling

*   Encapsulation of IPv6 packets in IPv4
*   Some automatic tunneling techniques: 6to4, Teredo, ISATAP

     → Approach

*   Encapsulate IPv6 packets in IPv4 packets
*   Implementable in a variety of forms

     → Implementations

*   Any general purpose VPN service, with an IPv6 overlay and IPv4 underlay network (IPsec, OpenVPN, Cisco Anyconnect …)

*   Teredo: Tunneling IPv6 over UDP through Network Address Translations (NATs)

*   Developed by Microsoft
*   Components: Client, Server, Relay
*   Client: Has only IPv4 and is possibly behind a NAT
*   Server: Help client to set itself up, and establish the tunnel
*   Relay:  Forward traffic from and to client
*   IPv4 client and server addresses are embedded in IPv6 address
*   Teredo prefix: 2001::/32
*   Based on NAT UDP hole punching

→  IPv4 to IPv6 Transition

*   Local router encapsulates IPv6 to IPv4
*   IPv4 packet gets transmitted to the "nearest" relay
*   Source IPv4 address is embedded in the IPv6 address
*   6to4 prefix: 2002::/16, append public IPv4 address to get /48 IPv6 subnet
*   Address IPv4 packets to 192.88.99.1 (IPv4 Anycast)
*   Deploy dual stack 6to4 relays and 6to4 routers as NAT router.

![](../gitbook/assets/acn-notes-figures/image72.png)

→ Header translation

*   Stateless IP/ICMP Translation (SIIT)
*   Defines a class of IPv6 addresses called IPv4-translated addresses
*   Use the ::ffff:0:0:0/96 subnet and may be written as ::ffff:0:a.b.c.d
*   Allows IPv6-only hosts to communicate with IPv4-only hosts

→ EXCURSION

*   The privacy extension prevents tracking of clients by randomization of the interface ID

![](../gitbook/assets/acn-notes-figures/image68.png)

*   In general, most end devices implement the privacy extension

*   90% of IPv6 addresses seen by a large CDN are only seen once in long-running analyses \[7\]
*   But how about Customer Premises Equipment (CPE)?

*    e.g., private networks use a single, fixed router (the CPE) as gateway to the Internet

        →  In 2020, an approach to discover the IPv6 periphery was presented \[8\]

*   →  A measurement revealed 64.8M router addresses
*   →  30M addresses were found using EUI-64

→ Is client tracking impossible?

*   To prevent tracking based on the assigned prefix, providers often rotate their assignments
*   But behavioral analysis of providers and CPE’s using EUI-64 can be used to track prefixes \[9\]
*   While clients can not be tracked, CPEs using EUI-64 identifiers can be actively found.

![](../gitbook/assets/acn-notes-figures/image43.png)

*   In theory, testing all targets in a /48 is infeasible
*   How can we reduce the search space and effectively track EUI-64 identifier?

*   Customers receive at least /64 prefixes and often larger
*   Providers often use only parts of their owned prefixes
*   Prefixes are often assigned at nibbles (e.g., /56, /60, /64)

![](../gitbook/assets/acn-notes-figures/image58.png)

Excursion Waste Bits

Excursion: Bit Magic in programming

*   We have fixed pointers of size 32 bits
*   We only reference 4 million items
*   → log2 (4000000) ≈ 22 bits
*   → 10 bits can be used to encode information to save memory

→ Application: Encode information into Addresses

*   Example: A company with several branches in Germany wants to encode the postal code of each branch into addresses.
*   Germany has 5 digits postal codes (00000-99999)
*   log2 (99999) ≈ 17 bits

→ SUMMARY

IPv6 offers:

*   128 bit address space → 340 trillion addresses
*   Revised and simplified header format
*   New options and extensions
*   Increased security measures

IPv6 uses hexadecimal colon notation with abbreviation methods

IPv6 has three address types:  unicast, anycast and multicast

ICMPv4, ARP, RARP and  IGMP replaced with  ICMPv6

IPv4 and IPv6 transition strategies are based on dual-stack and tunneling

IPv6 adoption:

*   IPv6 is supported by all major operating systems and all major router vendors
*   Still some work to be done for complete adoption