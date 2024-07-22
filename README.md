# Static-Routing-configuration
This repository contains a detailed guide and configuration files for setting up static routing using three routers in a network topology. Static routing is a method of manually setting up routes in a network, which can be particularly useful in small networks or specific scenarios where dynamic routing is not necessary

## Overview

The project demonstrates how to configure static routes on three routers to ensure proper communication between different network segments. This setup can be useful for understanding the basics of static routing and for implementing simple, stable networks where routing paths do not change frequently.

## Network Topology

The network topology for this configuration includes three routers connected in a triangle, with each router having one or more connected networks. The goal is to configure static routes so that all networks can communicate with each other.


## Configuration Steps

1. **Assign IP Addresses**: Assign IP addresses to the interfaces of each router.
2. **Configure Static Routes**: Manually add static routes on each router to enable communication between all networks.
3. **Verify Connectivity**: Test the configuration to ensure that all routers and networks can communicate properly.

### Router 1 Configuration

```sh
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface GigabitEthernet0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown

ip route 192.168.3.0 255.255.255.0 192.168.2.2
ip route 192.168.4.0 255.255.255.0 192.168.1.2
```

### Router 2 Configuration

```sh
interface GigabitEthernet0/0
 ip address 192.168.2.2 255.255.255.0
 no shutdown

interface GigabitEthernet0/1
 ip address 192.168.3.1 255.255.255.0
 no shutdown

ip route 192.168.1.0 255.255.255.0 192.168.2.1
ip route 192.168.4.0 255.255.255.0 192.168.3.2
```

### Router 3 Configuration

```sh
interface GigabitEthernet0/0
 ip address 192.168.3.2 255.255.255.0
 no shutdown

interface GigabitEthernet0/1
 ip address 192.168.4.1 255.255.255.0
 no shutdown

ip route 192.168.1.0 255.255.255.0 192.168.3.1
ip route 192.168.2.0 255.255.255.0 192.168.4.2
```

## Testing the Configuration

1. **Ping Test**: Use the `ping` command from each router to test connectivity to the other routers and networks.
2. **Traceroute Test**: Use the `traceroute` command to ensure that the packets are taking the correct paths as per the static routes configured.

