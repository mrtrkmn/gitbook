## Network Types

- Transit AS(red): 
    - Forwards traffic from one AS to another AS 

- Stub AS (yellow): 
    - AS, which is conected to only one other AS 

- Multi-homed AS (blue): 
    - AS, which is connected to multiple ASes, but does not forward traffic on their behalf

![](https://imgur.com/a/oBei9ZG)


## Routing Protocols

- Inter-Domain Protocols (Inter AS routing)
    - Exchange routing information between ASes
    - Called Exterior Gateway Protocols (EGP)
    - In practice, only one protocol is used: BGP

- Intra-Domain Protocols (Intra AS routing)
    - Exchange routing information within an AS
    - Called Interior Gateway Protocols (IGP)
    - In practice, two protocols are used: OSPF and IS-IS, RIP is not used anymore

--> EGP: Which AS to transfer the packet to 

--> IGP: Which intra-AS route to use 

### Routing Information Base (RIB)

- Contains all the routes that the router knows about
- Routes are stored in a table, which is indexed by the destination network
- Each route has a metric, which is used to determine the best route to a destination network
- The metric is computed based on the protocol used to learn the route

### Forwarding Information Base (FIB)

- Contains the best route to each destination network
- The FIB is computed from the RIB
- The FIB is used to forward packets

![](../../gitbook/assets/routuing.png)


### Inter-AS and intra-AS routing

- Inter-AS routing 
    - only for destinations outside of own AS
    - Used to determine gateway router
    - BGP is used to exchange routing information between ASes

- Intra-AS routing 
    - only for destinations inside of own AS
    - Used to determine next hop router
    - OSPF and IS-IS are used to exchange routing information within an AS

### BGP

- Border Gateway Protocol
- Inter-AS routing protocol
- Used to exchange routing information between ASes
- BGP is a path-vector protocol
- BGP router exhange information derived from their routing table entries

--> Internal BGP (iBGP): 
    - Used to exchange routing information within an AS
    - Uses the AS number as the routing domain

--> External BGP (eBGP):
    - Used to exchange routing information between ASes
    - Uses the AS number of the neighbor as the routing domain

![](../../gitbook/assets/bgp.png)

ISP B has a more specific route to Organization 1. 

BGP uses different message types, transmitted between BGP peers, to exchange routing information.

- OPEN message: 
    - Used to establish a BGP session

- UPDATE message:
    - Announce a new route or un-reachability of an old one 

- NOTIFICATION message: 
    - Send error codes

- TEARDOWN message: 
    - Used to close a BGP session

- UPDATE messages:
    - AS path - list of ASes
    - Next hop - IP address of the next hop router
    - Origin - where the route was learned
    - Destination prefix - destination network

### Hot Potato Routing

- Large ASes connect at different sites 
- The longer a packet is transferred inside an AS, the more expensive it is
- Choosing the "nearest" connection site minimizes the cost


In this method, packets are forwarded to the next hop that is closest to the destination, rather than taking the most direct path. This helps to reduce the overall cost of transmitting the data, as it minimizes the amount of hops that the data must take, as well as reducing the amount of time that the data spends in transit.


### BGP Peering 

- Public Peering 
    - Exchanging traffic with other ASes at an Internet exchange point (IXP)
    - Peering is done on a voluntary basis
    - Peer with as many ASes as possible
    - Reduce the traffic you send to your upstream provider

- Private Peering
    - Exchange a large amount of traffic with a single AS 
    - Attractive setup for upstream providers
    - Peering is done on a contractual basis
    - Interconnection of, within, and inbetween data centers 

## Routing Basic Principles

Routing: Prefer routes that incur financial gain: 

1. Route via a customer (financial gain)
2. Route via a peer (no financial gain or loss)
3. Route via a provider (financial loss)

### Route Announcement 

- Announce routes that incur financial gain if others use them (others=customers)
- Announce routes that reduce costs if others use them (Others=peers)
- Do not announce routes that incur financial loss (as long as alternatives exist)

### Stub ASes

- Stub ASes have exactly one BGP relationship (with their provider)

![](../../gitbook/assets/stubas.png)

* Rules:
    - Provider AS announces routes for reaching the whole internet to customer AS 
    - Customer AS announces routes for reaching its prefixes to provider AS 
    - The more traffic the customer sends to the provider or receives from the provider, the more money the provider makes 

In the given figure C is losing money A is earning. 

### Multi-homed ASes

- Multi-homes ASes have multiple providers 

![](../../gitbook/assets/multihomed.png)

* Rules

    - Several provider ASes announce routes for reaching the whole internet to customer AS 
    - Customer AS annouces routes for reaching its prefixes to several provider ASes. 
    - The more traffic the customer exchanges with the providers, the more money the providers make
    - Customer chooses the cheapest/best quality providers 
        - In case customer (by mistake) announces other prefixes, providers would exchange traffic over the customer network: No benefit for the customer but financial loss

    - Customer may use AS path prepending  by adding his AS number several time to path in BGP announcement, to discourage the use of expensive providers for incoming traffic. 
    

    ### Path Prepending 

    **Trying to influence other peoples routing decisions**

    Example: 

    - The destination AS has one router in Munich, and one router in London 
    - The destination datacenter is also in Munich 
    - The source AS can choose to hand over the packet in London or Munich 
    - It is cheaper for the destination AS if the source chooses the Munich router 
    - The destination AS includes its own ASN multiple times in the BGP updates it sends in London
    - The AS-path to Munich is shorter than the AS-path to London
    - This may (or may not) convince a source AS to hand over traffic in Munich

Path Prepending is a technique used in BGP (Border Gateway Protocol) routing to influence the selection of paths in the global routing table. It allows a network administrator to increase the preference of a specific path for a certain destination, making it more likely to be selected as the best path by other BGP routers.

In path prepending, the same autonomous system number (ASN) is added multiple times to the AS-Path attribute of a BGP route. This makes the route appear to be less desirable, causing other BGP routers to prefer alternative paths with a shorter AS-Path. By manipulating the AS-Path attribute, the network administrator can control the path that traffic takes through the network, allowing them to optimize the use of network resources and improve the reliability and performance of their network.

**Business Routing Example**

A tells C routes to all reachable prefixes. 

- The more traffic comes from C, the more money A makes

![](../../gitbook/assets/routing-ex-1.png)


**Business Routing Example 2**

A and B tell C routes to all reachable prefixes.

- The more traffic flows from C to A, the more money A makes
- The more traffic flows from C to B, the more money B makes
- C will pick the one with the cheaper offer/ better quality

![](../../gitbook/assets/routing-ex-2.png)

**Business Routing Example 3**

C tells A its own prefixes , C tells B its own prefixes
 - C wants to be reachable from outside

C does not tell A routes learned from/via B 

C does not tell B routes learned from/via A 

 - C does not want to pay for traffic <- A <- C <- B <- ...


![](../../gitbook/assets/routing-ex-2.png)


**Business Routing Example 4**

What should A announce here 

- C tells A about its own prefixes
- A tells D about its route to C's prefixes: pays money to D, but gains money from C

![](../../gitbook/assets/routing-ex-3.png)

**Business Routing Example 5**

What should A announce to E

- A tells peering partner E about its own prefixes and route to C's prefixes
- no cost on link to E, but gains money from C

![](../../gitbook/assets/routing-ex-4.png)


**Business Routing Example 6**

Which rouite to prefix p does C receive, which should C select?

- A tells C abouts route to prefix p (C loses money)
- F tells C about route to prefix p (no cost involved)
- C prefers route via F

![](../../gitbook/assets/routing-ex-5.png)


**Business Routing Example 7**

Which route to prefix p does C receive, which should C select?

- A tells C about route to prefix p (C loses money)
- F tells C about route to prefix p (no cost involved)
- G tells C about route to prefix p (C gains money)
- C prefers route via G

![](../../gitbook/assets/routing-ex-6.png)


**Business Routing Example 8**

What shold C announce here ? 

- C announces to F and H: its own prefixes and G's prefixes 
- C does not annouce to H: routes to prefixes it learned from F 
  - Otherwise: H could send traffic towards F but would not pay anything. F would not pay either. C's network would be loaded with additional traffic. 

- C does not announce to F: routes to prefixes it learned from H
    - Same reason as above

![](../../gitbook/assets/routing-ex-7.png)

### Valley Free Routing

- Valley free routing is a technique to avoid the problem of routing loops in the Internet

1. upstream: sequence of Customer -> Provider links (possibly length = 0 )
2. then possibly one peering link
3. the downstream: sequence of Provider -> Customer links (possibly length = 0 )

![](../../gitbook/assets/routing-valley.png)



Valley-Free Routing is a routing technique used in computer networks to avoid routing loops. It ensures that packets are not sent in circles by ensuring that they always follow a path that either increases or stays the same in some metric, such as hop count, instead of decreasing and then increasing again.

In a valley-free routing scheme, each node maintains information about the metric value of its neighboring nodes. When forwarding a packet, the node selects the next hop based on the metric values, choosing the neighbor with the lowest value. This ensures that the metric value of the packet always increases or stays the same, and prevents the packet from forming a loop.

Valley-Free Routing is used in various routing protocols, such as OSPF (Open Shortest Path First) and IS-IS (Intermediate System to Intermediate System), to prevent routing loops and ensure stable and efficient routing in large computer networks.


### Siblings 

Not everything is provider/customer or peering 

Sibling = mutual transit agreement 

- Provide connectivity to the rest of the Internet for each other 
- No financial relationship
- very extensive peering agreements

Examples:

- Two small ASes close to each other that cannot/do not want to afford additional Internet services
- Merging of two companies:
    - Merging two ASes into one = difficult 
    - Keep both ASes and exhangeing everything for free = easier
- Example AT&T has five different ASNs 

### Tiers 


Providers can be categorized into Tiers

- Tier-1/Default-Free-Zone: only peerings, no providers 
- Tier-2: only peerings and one or more Tier-1 provider 
- Tier-3: at least one Tier-2 as a provider

- Tier-n: at least one Tier-(n-1) as a provider
    - defined recursively
    - n =< 4: Rare in western Europe, north America, east Asia

- Tier 1.5: almost a Tier 1, but pays money for some links. 

### BGP Technical Summary

1. Receive BGP Update
2. Apply import policies
    - Filter routes
    - Tweak attributes
3. Best route selection based on attribute values
    - Policy: Local preference settings and other attributes 
    - Install forwarding tables entries for best routes
    - Possibly transfer to Route Reflector RR as alternative to logical full mesh of iBGP sessions
4. Apply export policies
    - Filter routes
    - Tweak attributes

5. Send BGP Update



- **Import Policy: Which routes to use**
    
    • Select path that incurs most money
    
    • Special/political considerations (e.g. Iranian AS does not want traffic to cross Israeli AS, other kinds of censorship)

- **Export Policy: Which routes to propagate to other ASes**


    • Not all known routes are advertised
    • Export only, ...
    1. ... if it incurs revenue
    2. ... if it reduces cost
    3. ... it it is inevitable

- **Policy routing: Money, Money, Money, ...**

    • Route import and export driven by business considerations

    • But not driven by technical considerations

        • Example: Slower route via peer may be preferred over faster route via provider



### k-Core Algorithm

![](../../gitbook/assets/routing-k-core.png)


The k-core algorithm is a graph theory algorithm used for finding and analyzing the structure of complex networks. It is used to identify dense subgraphs or subnetworks within a larger network that are more tightly connected than other parts of the network.

The steps to perform the k-core algorithm are as follows:

1. Initialize the coreness value (k-value) of each node in the network to zero.

2. Starting from the nodes with the highest degree (number of connections), increment the k-value of each node until all nodes have a k-value of at least k.

3. Repeat the following steps until no more nodes can be removed:

    a. Find all nodes with a k-value less than k.

    b. Remove these nodes and their connections from the network.

    c. Update the k-values of the remaining nodes.

4. The nodes that remain in the network after the above steps form the k-core of the network, where k is the largest value for which a k-core exists.


The k-core algorithm provides valuable insights into the structure and organization of complex networks, and can be used for a variety of applications, such as community detection, network visualization, and identifying influential nodes in a network.