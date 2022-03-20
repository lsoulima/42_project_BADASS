# STATIC CONFIG

`frr1`

    ip link add br0 type bridge
    ip link set dev br0 up
    ip addr add 10.1.1.1/24 dev eth0
    ip link add name vxlan10 type vxlan id 10 dev eth0 remote 10.1.1.2 local 10.1.1.1 dstport 4789
    ip addr add 20.1.1.1/24 dev vxlan10
    ip link set dev vxlan10 up
    brctl addif br0 eth1
    brctl addif br0 vxlan10

`frr2`

    ip link add br0 type bridge
    ip link set dev br0 up
    ip addr add 10.1.1.2/24 dev eth0
    ip link add name vxlan10 type vxlan id 10 dev eth0 remote 10.1.1.1 local 10.1.1.2 dstport 4789
    ip addr add 20.1.1.2/24 dev vxlan10
    ip link set dev vxlan10 up
    brctl addif br0 eth1
    brctl addif br0 vxlan10

`host1`

    ip a add 30.1.1.1/24 dev eth0

`host2`

    ip a add 30.1.1.2/24 dev eth0


# DYNAMIC CONFIG

`frr1`

    ip link add br0 type bridge
    ip link set dev br0 up
    ip addr add 10.1.1.1/24 dev eth0
    ip link add name vxlan10 type vxlan id 10 dev eth0 group 239.1.1.1 dstport 4789
    ip addr add 20.1.1.1/24 dev vxlan10
    ip link set dev vxlan10 up
    brctl addif br0 eth1
    brctl addif br0 vxlan10

`frr2`

    ip link add br0 type bridge
    ip link set dev br0 up
    ip addr add 10.1.1.2/24 dev eth0
    ip link add name vxlan10 type vxlan id 10 dev eth0 group 239.1.1.1 dstport 4789
    ip addr add 20.1.1.2/24 dev vxlan10
    ip link set dev vxlan10 up
    brctl addif br0 eth1
    brctl addif br0 vxlan10

`host1`

    ip a add 30.1.1.1/24 dev eth0

`host2`

    ip a add 30.1.1.2/24 dev eth0



# EXTRA

**show interfaces**

    ip addr show eth0
    ip link show eth1
    ip -d link show vxlan10

**display mac address table**

    brctl showmacs br0
