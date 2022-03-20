## GENERAL

- basic functioning of GNS3:
- The global operation and the interest of BGP:
- The differences between layer 2 and layer 3 in a network:


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
- BGPD service
- OSPFD service
- routing engine service:
    IS-IS (Intermediate system-to-intermediate system)
- Busybox:
    Logiciel qui implémente un grand nombre des commandes standard sous Unix, à l'instar des GNU Core Utilities
    Size of Busybox image ~ 2 MB
    Size of Alpine image ~ 5 MB
    Size of Ubuntu image ~ 188 MB
    `Busybox` is a minimal set of tools typically present in a unix-like operating system. It does not contain a kernel and is not an operating system.
    `Alpine` is a minimal Linux distribution that contains everything necessary to boot a kernel and initiate a session.
    `Ubuntu` is a consumer-focused Linux distribution with many tools, utilities, and applications needed for an end-user focused operating system.
    -->That should explain the size differences.

## PART2

- VXLAN:
    - Virtual eXtensible Local Area Network (VXLAN) is a tunneling protocol that tunnels Ethernet (layer 2) traffic over an IP (layer 3) network.
    - The differences with a VLAN: 
- switch
- bridge
- The differences between broadcast and multicast.
- The expected operation of the topology


## PART3

- BGP-EVPN:
    * BGP (Border Gateway Protocol). BGP-4 is one of the Exterior Gateway Protocols and the de facto standard interdomain routing protocol.
- The principle of road reflection (RR):
    BGP routers connected inside the same AS through BGP belong to an internal BGP session, or IBGP. In order to prevent routing table loops, IBGP does not advertise IBGP-learned routes to other routers in the same session. As such, IBGP requires a full mesh of all peers. For large networks, this quickly becomes unscalable. Introducing route reflectors removes the need for the full-mesh.
- VTEP:
    The VXLAN tunnel endpoint (VTEP) is the device that’s responsible for encapsulating and de-encapsulating layer 2 traffic. This device is the connection between the overlay and the underlay network. The VTEP comes in two forms: Software (host-based), Hardware (gateway)
- VNI:
    The VXLAN Network Identifier (VNI) identifies the VXLAN and has a similar function as the VLAN ID for regular VLANs. We use 24 bits for the VNI, which means we can create 16,777,215 ( ~16 million) VXLANs. That’s a lot, compared to those 4094 VLANs with a 12-bit VLAN ID. We can create plenty of VXLANs, which means a large service provider with even thousands of customers can use as many VXLANs per customer as needed.
- The difference between type 2 and type 3 roads:
    * Type 2 route — MAC/IP route: This is used to advertise the MAC address, ARP entry, and routing information of hosts.
    * Type 3 route — inclusive multicast route: This is used for automatic discovery of VTEPs and dynamic establishment of VXLAN tunnels.
- The expected operation of the topology
---

- VTYSH:
    * (Virtual teletype) is a virtual port and used to get Telnet or SSH access to the device.VTY is solely used for inbound connections to the device. These connections are all virtual with no hardware associated with them.
    * An integrated shell for the FRR routing engine. It amalgamates all the CLI commands defined in each of the daemons and presents them to the user in a single shell. It provides a Cisco-like modal CLI, and many of the commands are similar to Cisco IOS commands. There are different modes to the CLI, and certain commands are only available within a specific mode.
