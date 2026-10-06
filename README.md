# Network Configuration & Security Lab

A multi-network Linux networking and security lab implemented using the
CORE network emulator.

## Overview

This project simulates an enterprise network consisting of internal
networks, a DMZ, external networks and an Internet backbone.

The project focuses on:

- Static routing
- Network segmentation
- DHCP
- Stateful firewall configuration
- Service-specific access control
- Network connectivity testing

## Network Architecture

The topology contains two organisations:

- Talos
- Delos

The Talos network contains internal subnets and a DMZ containing
public-facing services. R3 acts as the Talos gateway and firewall,
while Minerva provides routing and DHCP functionality for the Delos
client network.

## Key Implementations

### 1. Static Routing

Configured static routes across the network using Linux `ip route`
commands.

Routing decisions were based on the propagation delays specified by
the topology.

The configuration provides connectivity between:

- Internal networks
- SSH server
- DMZ services
- Global DNS
- Delos clients
- External networks

Connectivity was validated using:

```bash
ping <destination>
traceroute <destination>
