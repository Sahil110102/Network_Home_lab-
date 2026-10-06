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
