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

2. DHCP
Configured Minerva as a DHCP server for the Delos client subnet.
The configuration provides clients with:
- Dynamic IP addresses
- Subnet mask
- Default gateway
- DNS configuration
- Lease information
Client machines were configured to obtain their network settings
dynamically.
3. Stateful Firewall
Implemented firewall rules on R3 using Linux iptables.
The firewall follows a default-deny approach and explicitly permits
required traffic.
Implemented controls include:
- DNS access to the DNS server
- HTTP access to the web server
- SMTP access to the mail server
- Internal-to-DMZ communication
- Internal-to-external communication
- Stateful return traffic
- Restricted SSH access to R3
- ICMP monitoring
- Logging of dropped traffic
Example:
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

Connection-state tracking was used to allow established and related
traffic.
Testing
The network was tested using:
- ping
- traceroute
- dig
- telnet
- tcpdump
- Wireshark
Testing covered routing reachability, DHCP address assignment and
firewall access-control behaviour.
Technologies
- Linux
- TCP/IP
- IPv4
- Static Routing
- DHCP
- iptables
- DNS
- HTTP
- SMTP
- CORE Network Emulator
- tcpdump
- Wireshark
Skills Demonstrated
- Network configuration
- Network troubleshooting
- Firewall configuration
- Access control
- Network security
- Packet analysis
- Linux administration
- TCP/IP networking


The firewall portion is particularly worth highlighting because your report actually implements default `INPUT`, `OUTPUT`, and `FORWARD` drops and then explicitly allows required traffic. :chatgpt-content-reference{index="6"}

---

# 4. Make the project more impressive before putting it on GitHub

I'd make **one improvement** to turn this from a university assignment into a genuine portfolio project.

Add a section called:

### Security Testing

Show examples such as:

| Test | Expected Result |
|---|---|
| Internet → DMZ DNS | Allowed |
| Internet → DMZ HTTP | Allowed |
| Internet → DMZ SMTP | Allowed |
| Internet → DMZ SSH | Blocked |
| Internal → DMZ services | Allowed |
| Internal → External | Allowed |
| External → Internal unsolicited traffic | Blocked |
| Non-client → R3 SSH | Blocked |
| Client subnet → R3 SSH | Allowed |
| Unauthorised traffic | Dropped |

This demonstrates that you understand **why** the firewall rules exist rather than simply copying `iptables` commands.

Your assignment specification specifically requires service-specific DMZ access, stateful inspection, restricted SSH, ICMP handling and dropping all other traffic. :chatgpt-content-reference{index="7"}

---

## 5. One thing I'd change on your resume

Because you're aiming toward cybersecurity, don't call it:

> **FIT9137 Assignment 3**

That's an academic label and doesn't sell your skills.

Use:

> **Network Configuration & Stateful Firewall Lab**

Then put:

> *Monash University — FIT9137*

This makes it look like a **technical project**, while still being honest about where it came from.

### Your final resume entry

**Network Configuration & Stateful Firewall Lab | Monash University**  
*Linux • TCP/IP • iptables • DHCP • Static Routing • CORE • Wireshark*

- Built and configured a multi-subnet enterprise network with internal, DMZ and external networks using the CORE network emulator.
- Implemented loop-free **static routing** across multiple Linux routers using propagation-delay-based path selection.
- Configured **DHCP** to dynamically provision client network settings.
- Developed a **stateful iptables firewall** using default-deny policies and least-privilege rules for DNS, HTTP, SMTP, SSH and ICMP traffic.
- Tested network reachability and security controls using **ping, traceroute, dig, telnet and packet-analysis tools**.

That is a **very relevant project for a junior cybersecurity/networking resume**.

If you give me the **actual `.imn` CORE configuration file** as well, I can take this one step further and help you structure the **complete GitHub repository with the actual configuration files, README, firewall rules, routing files, screenshots/evidence, and a polished project description** rather than just putting the PDF online.
```bash
ping <destination>
traceroute <destination>
