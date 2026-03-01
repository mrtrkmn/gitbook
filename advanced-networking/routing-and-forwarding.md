# Routing and Forwarding

What is the interface of a routing protocol?

• Routing protocols know all possible routes to a destination network

• Routing Information Base (RIB)

• Routing protocols choose which route is the “best” route (FIB)

• Forwarding Information Base (FIB),  also known as routing table

• Routing protocols do not concern themselves with forwarding individual packets

*   Routing : Routing protocols are used to create a RIB, RIB is used to create a FIB (routing table)
*   Updates to RIB/FIB itself happen less frequently → less time critical
*   Forwarding : actually looking at the packets and relaying packets according to the routing table
*   Forwarding lookups need to be performed for every packet in every router → highly time critical

[\[a\]](#cmnt_ref1) To determine the lower 24 bits of an IPv6 address by hand, you can follow these steps:

Take the last 4 hexadecimal characters of the IPv6 address, which represent the last 32 bits of the address.

Convert the hexadecimal value to binary.

Extract the last 24 bits of the binary representation.

Here's an example:

Given the IPv6 address: 2001:0db8:85a3:0000:0000:8a2e:0370:7334

Last 4 hexadecimal characters: 7334

In binary: 0111001100110100

Last 24 bits: 100110100110100

Note that this method only works for the lower 24 bits of the last block of an IPv6 address. To determine the lower 24 bits of a different portion of the address, you would need to follow a similar process, converting the relevant hexadecimal characters to binary and extracting the desired bits.