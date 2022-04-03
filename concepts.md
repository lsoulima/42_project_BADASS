## GENERAL

- basic functioning of GNS3:
    `Graphical Network Simulator` is used to emulate, configure, test and troubleshoot virtual and real networks. GNS3 allows you to run a small topology consisting of only a few devices on your laptop, to those that have many devices hosted on multiple servers or even hosted in the cloud.
- The global operation and the interest of BGP:
    The `BGP` allows you to create loop-free interdomain routing between different autonomous systems (ASs).
    An `AS` is a set of routers under a single technical administration.
    Routers in an AS can use multiple Interior Gateway Protocols (IGPs) to exchange routing information inside the AS.
    The routers can use an exterior gateway protocol to route packets outside the AS.
[see more...](https://www.cisco.com/c/en/us/support/docs/ip/border-gateway-protocol-bgp/26634-bgp-toc.html)
- The differences between layer 2 and layer 3 in a network:
    A Layer 2 switch only works with MAC addresses and doesn't interact with any higher layer addresses, such as an IP.
    A Layer 3 switch, on the other hand, can also do static routing and dynamic routing, which includes IP and virtual local area network (VLAN) communications.
[see more...](https://www.aussiebroadband.com.au/blog/difference-layer-3-layer-2-networks/)
## PART1

- packet routing software:
    - ZEBRA:
        * An IP routing manager. It provides kernel routing table updates, interface lookups, and redistribution of routes between different routing protocols.
        * Zebra is a multi–server routing software which provides TCP/IP based routing protocols. Zebra turns your machine into a full powered router.
    - QUAGGA:
        * Software suites that can be used to implement different routing protocols.
        * Quagga is a routing software suite, providing implementations of OSPFv2, OSPFv3, RIP v1 and v2, RIPng and BGP-4 for Unix platforms, particularly FreeBSD, Linux, Solaris and NetBSD. Quagga is a fork of GNU Zebra
    - FRR:
        A routing software suite, which has been derived from Quagga and is distributed under GNU GPL2 license. Like Quagga, it provides implementations of all major routing protocols such as OSPF, Routing Information Protocol (RIP), Border Gateway Protocol (BGP), and Intermediate system-to-intermediate system (IS-IS) for Unix-like platforms.
- `BGPD` and `OSPFD` services:
    A routing components that work with the Quagga routing engine. [ref](https://linux.die.net/man/8/bgpd)
- routing engine service: !!
- Busybox:
    Logiciel qui implémente un grand nombre des commandes standard sous Unix, à l'instar des GNU Core Utilities.
    
    Size of Busybox image ~ 2 MB
    Size of Alpine image ~ 5 MB
    Size of Ubuntu image ~ 188 MB
    `Busybox` is a minimal set of tools typically present in a unix-like operating system. It does not contain a kernel and is not an operating system.
    `Alpine` is a minimal Linux distribution that contains everything necessary to boot a kernel and initiate a session.
    `Ubuntu` is a consumer-focused Linux distribution with many tools, utilities, and applications needed for an end-user focused operating system.
    -->That should explain the size differences.

## PART2
[see more...](https://www.ciscolive.com/c/dam/r/ciscolive/apjc/docs/2018/pdf/BRKDCN-3040.pdf)
- VXLAN vs VLAN: !!
    * Benefits: segmentation, Flexibilty, Security
    * VXLAN: (Virtual eXtensible Local Area Network)  is a tunneling protocol that tunnels Ethernet (layer 2) traffic over an IP (layer 3) network.
    VxLAN creates virtual layer-2 segments, called VNI's. VNI's run over the top of a layer-3 network. VxLAN switches use a special interface called a VTEP. This bridges VNIs to the layer-3 network. When traffic comes in, the VTEP encapsulates the traffic, and sends it to a destination VTEP where it is decapsulated.
    * VLAN: Reduce Overhead by limiting the size of each brodcast domain
-  Switch:
    A device that connects multiple devices together. Switches allow devices to share and transfer data, enabling communication between devices on the network. Switches work by processing packets of data and routing them to the intended destination(s).
- bridge:
    A bridge operates at the data link layer. A bridge is a repeater, with add on the functionality of filtering content by reading the MAC addresses of source and destination. It is also used for interconnecting two LANs working on the same protocol. It has a single input and single output port, thus making it a 2 port device.
- The differences between broadcast and multicast:
    Broadcast and multicast are two types of transmission. The main difference between broadcast and multicast is that, in broadcast, the message or packets go to all the connected devices on the network while in multicast, the packets go to a required set of devices on the network.
[devices](https://www.geeksforgeeks.org/network-devices-hub-repeater-bridge-switch-router-gateways/)
- The expected operation of the topology !!


## PART3

- BGP-EVPN: !!
    * BGP (Border Gateway Protocol). BGP-4 is one of the Exterior Gateway Protocols and the de facto standard interdomain routing protocol.
- The principle of road reflection (RR):
    BGP routers connected inside the same AS through BGP belong to an internal BGP session, or IBGP. In order to prevent routing table loops, IBGP does not advertise IBGP-learned routes to other routers in the same session. As such, IBGP requires a full mesh of all peers. For large networks, this quickly becomes unscalable. Introducing route reflectors removes the need for the full-mesh.
[see more...](https://www.cbtnuggets.com/blog/technology/networking/networking-basics-what-are-bgp-route-reflectors-for-ipv6)
- VTEP:
    Switches and routers that participate in VxLAN has a special interface called VTEP. The CTEP provides the connection between the overlay and the underlay. Each VTEP has an IP address in the underlay network, it also has one or more VNIs.
    The VXLAN tunnel endpoint (VTEP) is the device that’s responsible for encapsulating and de-encapsulating layer 2 traffic. This device is the connection between the overlay and the underlay network. The VTEP comes in two forms: Software (host-based), Hardware (gateway)
- VNI:
    The VXLAN Network Identifier (VNI) identifies the VXLAN and has a similar function as the VLAN ID for regular VLANs. We use 24 bits for the VNI, which means we can create 16,777,215 ( ~16 million) VXLANs. That’s a lot, compared to those 4094 VLANs with a 12-bit VLAN ID. We can create plenty of VXLANs, which means a large service provider with even thousands of customers can use as many VXLANs per customer as needed.
- The difference between type 2 and type 3 roads:
    * Type 2 route — MAC/IP route: This is used to advertise the MAC address, ARP entry, and routing information of hosts.
    * Type 3 route — inclusive multicast route: This is used for automatic discovery of VTEPs and dynamic establishment of VXLAN tunnels.
[see more...](https://support.huawei.com/enterprise/en/doc/EDOC1100023542?section=j01f&topicName=type-3-route)
- The expected operation of the topology

---

- VTYSH:
    * (Virtual teletype) is a virtual port and used to get Telnet or SSH access to the device.VTY is solely used for inbound connections to the device. These connections are all virtual with no hardware associated with them.
    * An integrated shell for the FRR routing engine. It amalgamates all the CLI commands defined in each of the daemons and presents them to the user in a single shell. It provides a Cisco-like modal CLI, and many of the commands are similar to Cisco IOS commands. There are different modes to the CLI, and certain commands are only available within a specific mode.

- RIB & FIB: [see more...](https://writemem.co.uk/what-is-a-rib-and-a-fib/)
    The elements that we’ve discussed so far are all linked together, there is a flow from one database to another.
    The best paths from EIGRP’s RIB and the best paths from BGP’s RIB are passed into the routing table RIB. Where competing paths exist from multiple routing protocols then Administrative Distance (AD) as a tiebreaker – lower is better.The winning paths are then passed to the FIB to be used for forwarding packets on to the next-hop router. The same process has also happened on the next router and the next one, until the packet reaches its destination.

- Why we'll need loopback interfaces?
    * we'll use the loopback IP as the rdv point in the multicast topology...
    * the VTEP gets IP address from the loopback
    (make sure all loopback interfaces are added into OSPF, and are in sparse mode.)