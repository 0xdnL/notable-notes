---
tags: [iproute, linux, macos, network]
title: ip
created: '2019-09-03T11:51:54.855Z'
modified: '2024-01-11T12:40:58.307Z'
---

# ip

> edits and displays the configuration of network interfaces, routing, and tunnels

## install

```sh
apt install iproute2
yum install iproute

brew install iproute2mac # python wrapper  a very similar but limited API
```

## usage

```sh
ip [OPTS] OBJECT {CMD|HELP}

ip help                         # display a list of commands and arguments for each subcommand
ip addr help                    # display address commands and arguments
ip link help                    # display link commands and arguments
ip neigh help                   # display neighbour commands and arguments
```

## option

```sh
-s, -stats, -statistics       # output more information. -s -s => more verbose
-f, -family                   # inet, inet6, bridge, ipx, dnet, link
-4                            # shortcut for -family inet.
-6                            # shortcut for -family inet6.
-B                            # shortcut for -family bridge.
-0                            # shortcut for -family link.
-o, -oneline                  # output each record on a single line, replacing line feeds with the '\' character
```

## address                   

> display IP Addresses and property information (abbreviation of address)

```sh
ip addr                         # display all addresses and property information

ip addr show en0                # show info to interface en0

ip -4 addr show eth0 | grep -oP "(?<=inet ).*(?=/)"

ip addr show dev em1            # display information only for device em1
ip -brief -color address show
ip -br -c a s

# modifying address andlink properties
ip addr add 192.168.1.1/24 dev em1        # Add address 192.168.1.1 with netmask 24 to device em1
ip addr del 192.168.1.1/24 dev em1        # Remove address 192.168.1.1/24 from device em1
```

## addrlabel                 

> label configuration for protocol address selection.

```sh
```

## l2tp                      

> tunnel ethernet over IP (L2TPv3)

```sh
```

## link                      

> Manage and display the state of all network interfaces

```sh
ip link                         # Show information for all interfaces
ip link show dev em1            # display information only for device em1
ip -s link                      # display interface statistics

ip link set                     # Alter the status of the interface
ip link set em1 up              # Bring em1 online
ip link set em1 down            # Bring em1 offline
ip link set em1 mtu 9000        # Set the MTU on em1 to 9000
ip link set em1 promisc on      # Enable promiscuous mode for em1
```

## maddress                  

> manage and display multicast IP addresses

```sh
ip maddr                        # display multicast information for all devices
ip maddr show dev em1           # display multicast information for device em1

ip maddr add                              # add a static link-layer multicast address
ip maddr add 33:33:00:00:00:01 dev em1    # add mutlicast address 33:33:00:00:00:01 to em1
ip maddr del 33:33:00:00:00:01 dev em1    # delete multicast address: 33:33:00:00:00:01 from em1
```

## monitor                   

> watch for netlink messages.

```sh
```

## mroute                    

> multicast routing cache entry.

```sh
```

## mrule                     

> rule in multicast routing policy database.

```sh
```

## neighbour                 

> manage ARP or NDISC cache entries.

```sh
neigh                           # Show neighbour objects; also known as the ARP table for IPv4
ip neigh                        # display neighbour objects
ip neigh show                   # arp cache
ip neigh show dev em1           # Show the ARP cache for device em1


# manage arp table
neigh add                                                 # Add an entry to the ARP Table
ip neigh add 192.168.1.1 lladdr 1:2:3:4:5:6 dev em1       # Add address 192.168.1.1 with MAC 1:2:3:4:5:6 to em1

neigh del                                                 # Invalidate an entry
ip neigh del 192.168.1.1 dev em1                          # Invalidate the entry for 192.168.1.1 on em1

neigh replace                                             # Replace, or adds if not defined, an entry to the ARP table
ip neigh replace 192.168.1.1 lladdr 1:2:3:4:5:6 dev em1   # Replace the entry for address 192.168.1.1 to use MAC 1:2:3:4:5:6 on em1
```

## netns                     

> manage network namespaces.

```sh
ip netns list                         # shows the list of current named network namespaces

ip netns add vpn                      # creates a network namespace and names it vpn

ip netns exec vpn ip link set lo up   # bring up the loopback interface in the vpn network namespace.

ip netns add foo
ip netns add bar
ip netns set foo 12
ip netns set bar 13
ip -n foo netns set foo 22
ip -n foo netns set bar 23
ip -n bar netns set foo 32
ip -n bar netns set bar 33
ip netns list-id target-nsid 12 # Shows the list of nsids from the network namespace foo.
ip netns list-id target-nsid 12 nsid 13 # Get nsid of bar from the network namespace foo (result is 23).
```

[[docker]], [[nsenter]], [man7.org/linux/man-pages/man8/ip-netns](https://man7.org/linux/man-pages/man8/ip-netns.8.html)

## ntable                    

> manage the neighbor cache's operation.

```sh
```

## route                     

> display and alter the routing table

```sh
ip route                        # List all of the route entries in the kernel
ip ro                           # show IP-pakets route via default bridge
ip route show cache table all


# adjust and view routes
route add                                         # Add an entry to the routing table
ip route add default via 192.168.1.1 dev em1      # Add a default route (for all addresses) via the local gateway 192.168.1.1 that can be reached on device em1
ip route add 192.168.1.0/24 via 192.168.1.1       # Add a route to 192.168.1.0/24 via the gateway at 192.168.1.1
ip route add 192.168.1.0/24 dev em1               # Add a route to 192.168.1.0/24 that can be reached on device em1

route delete                                      # Delete a routing table entry
ip route delete 192.168.1.0/24 via 192.168.1.1    # Delete the route for 192.168.1.0/24 via the gateway at 192.168.1.1

route replace                                     # Replace, or add if not defined, a route
ip route replace 192.168.1.0/24 dev em1           # Replace the defined route for 192.168.1.0/24 to use device em1

route get                                         # display the route an address will take
ip route get 192.168.1.5                          # display the route taken for IP 192.168.1.5
```

## rule                      

> rule in routing policy database.

```sh
```

## tcp_metrics, tcpmetrics   

> manage TCP Metrics.

```sh
```

## tunnel                    

> tunnel over IP.

```sh
```

## tuntap                    

> manage TUN/TAP devices.

```sh
```

## xfrm                      

> manage IPSec policies.

```sh
```

## see also

- [[wg]]
- [[netstat]]
- [[arp]]
- [[ipv4]], [[ipcalc]]
- [[net-tools]]
- [[iproute]]
- [[net-tools vs iproute]]
- [[ethtool]]
- [[iptables]]
- [[firewall-cmd]]
- [computerhope.com/unix/ip.htm](https://www.computerhope.com/unix/ip.htm)
- [man7.org/../man8/ip.8.html](http://man7.org/linux/man-pages/man8/ip.8.html)
