# SDN Based Traffic Control using OpenFlow and Mininet
- Nookala Sai Tushar Krishna
- SRN: PES2UG24CS331
- Batch ID: 20

---

# Project Overview

This project demonstrates Software Defined Networking (SDN) using Mininet, Open vSwitch, and the OpenFlow protocol. A virtual network topology consisting of multiple hosts connected through a switch was created and controlled using OpenFlow flow rules.

The project demonstrates:
- Packet forwarding using flow tables
- Traffic filtering using OpenFlow rules
- Host communication control
- Bandwidth testing using iperf
- Centralized network management using SDN

---

# Tools and Technologies

- Mininet
- Open vSwitch
- OpenFlow
- Python
- Ubuntu/Debian Linux

---

# Network Topology

The topology consists of:
- 1 OpenFlow Switch (`s1`)
- 3 Hosts (`h1`, `h2`, `h3`)

---

# Commands Used

## Start Mininet

```bash
sudo mn --topo single,3 --mac --switch ovsk --controller remote
```

## View Flow Table

```bash
sudo ovs-ofctl dump-flows s1
```

## Ping Test

```bash
mininet> h1 ping h2
mininet> h1 ping h3
```

## Bandwidth Test using iperf

### Start iperf server

```bash
mininet> h2 iperf -s
```

### Start iperf client

```bash
mininet> h1 iperf -c 10.0.0.2
```

---

# Flow Table Explanation

The switch flow table contains forwarding rules based on MAC addresses and input ports. Flow entries were added to control packet forwarding between hosts.

A rule was configured to drop packets from host `10.0.0.3`, which prevented communication with other hosts.

The controller dynamically manages traffic by installing appropriate flow rules in the switch.

---

# Results

## Successful Communication

- Host `h1` successfully communicated with `h2`
- Ping results showed `0% packet loss`

## Blocked Communication

- Communication between `h1` and `h3` was blocked
- Ping results showed `100% packet loss`

## Bandwidth Testing

Bandwidth between hosts was tested using `iperf`.

The test successfully measured TCP throughput between hosts connected through the OpenFlow switch.

---

# Screenshots

The repository contains screenshots of:
- OpenFlow flow tables
- Ping test results
- iperf bandwidth testing
- Packet filtering results

---

# Conclusion

The project successfully demonstrates Software Defined Networking concepts such as programmable traffic management, centralized control, and flow-based packet forwarding using OpenFlow and Mininet.

The implementation shows how SDN improves network flexibility, security, and traffic management in modern computer networks.
