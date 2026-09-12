# TechNova Enterprise Network

A medium-sized enterprise network designed and implemented in **Cisco Packet Tracer** to simulate a realistic corporate network environment.

The project focuses on enterprise networking, redundancy, routing, network services, secure device management, Layer 2 security, and troubleshooting.

## Network Architecture

The network follows a hierarchical design:

**ISP → EDGE Router → CORE Router → Distribution Layer → Access Layer**

Dedicated switches are also used for the Server and Management networks.

### Main Devices

* ISP-R1
* EDGE-R1
* CORE-R1
* DIST1
* DIST2
* Access_SW_1
* Access_SW_2
* Access_SW_3
* Access_SW_4
* Server_SW
* MGMT_SW

## VLANs and IP Addressing

| VLAN | Name          | Network       | Purpose            |
| ---: | ------------- | ------------- | ------------------ |
|   10 | HR            | 10.10.10.0/24 | Human Resources    |
|   20 | IT            | 10.10.20.0/24 | IT Department      |
|   30 | FINANCE       | 10.10.30.0/24 | Finance Department |
|   40 | GUEST         | 10.10.40.0/24 | Guest Users        |
|   50 | SERVERS       | 10.10.50.0/24 | Servers            |
|   60 | MANAGEMENT    | 10.10.60.0/24 | Network Management |
|  999 | UNUSED-NATIVE | Reserved      | Native VLAN        |

## Technologies Implemented

### Layer 2

* VLANs
* 802.1Q trunking
* Native VLAN 999
* EtherChannel / LACP
* Rapid-PVST
* STP root optimization
* PortFast
* BPDU Guard
* Root Guard
* Loop Guard

### Layer 3

* Inter-VLAN routing
* HSRP gateway redundancy
* OSPF Area 0
* OSPF default route propagation
* Router loopback interfaces

### Network Services

* DHCP
* DHCP Relay using `ip helper-address`
* DNS
* FTP/File Server
* Web Server
* NAT/PAT

### Secure Management

* SSH
* Centralized TACACS+ authentication
* Local authentication fallback
* Dedicated management VLAN

### Layer 2 Security

* Port Security
* Sticky MAC addresses
* DHCP Snooping
* BPDU Guard
* Root Guard
* Loop Guard

## Routing and Redundancy

OSPF is used as the internal dynamic routing protocol.

The network uses **HSRP** between DIST1 and DIST2 to provide redundant default gateways for the VLANs.

STP root roles are distributed between the two distribution switches to provide load balancing while maintaining Layer 2 redundancy.

EtherChannel/LACP is used on multiple redundant uplinks to increase bandwidth and provide link-level redundancy.

## Internet Connectivity

Internal VLANs access the external network through the EDGE router.

NAT overload/PAT translates private enterprise addresses to the EDGE router's outside interface.

The project also includes a simulated public web server on the ISP network.

## Servers

The server network contains:

* DHCP Server — `10.10.50.10`
* DNS Server — `10.10.50.11`
* File Server — `10.10.50.12`
* AAA/TACACS+ Server — `10.10.60.20`
* Public Web Server — `198.51.100.10`

## Security and Management

Network devices are managed through SSH instead of insecure Telnet.

TACACS+ is used for centralized authentication with local authentication configured as a fallback.

Access ports use security controls such as Port Security and DHCP Snooping, while STP protection mechanisms are applied to help prevent Layer 2 attacks and accidental topology issues.

## Troubleshooting and Validation

During implementation, several issues were encountered and investigated, including:

* HSRP gateway connectivity problems
* OSPF adjacency verification
* EtherChannel negotiation problems
* VLAN and trunk connectivity
* DHCP relay connectivity
* NAT/PAT verification
* STP path selection
* Packet Tracer limitations affecting ACL testing
* Router authentication/password configuration behaving unexpectedly in Packet Tracer

### ACL Limitation

An extended ACL was designed to restrict communication between selected VLANs. However, during testing, the ACL did not behave as expected when applied to the VLAN interfaces in Cisco Packet Tracer.

The configuration and traffic behavior were investigated, but the restriction could not be reliably validated in the Packet Tracer environment.

This is documented as a **lab/Packet Tracer limitation encountered during testing**, rather than being presented as a successfully validated security control.

### Router Authentication Issue

While configuring passwords/authentication on the routers, Packet Tracer exhibited unexpected behavior that affected router access during testing.

The issue was investigated as part of the troubleshooting process. This project therefore does not claim successful end-to-end router TACACS+/password authentication validation where Packet Tracer behavior prevented reliable testing.

## Project Validation

The following areas were successfully tested:

* VLAN connectivity
* Inter-VLAN routing
* HSRP operation
* OSPF neighbor relationships
* OSPF route propagation
* NAT/PAT translations
* DHCP and DHCP relay
* DNS resolution
* Internet connectivity
* SSH access
* TACACS+ authentication on supported devices
* Layer 2 security features
* STP and redundant path behavior

## Project Files

```text
Technova-Enterprise-Network/
├── README.md
├── TechNova_Enterprise_Network.pkt
├── Documentation/
├── Screenshots/
└── Configurations/
```

## Skills Demonstrated

This project demonstrates practical knowledge of:

**VLANs · Trunking · Inter-VLAN Routing · STP · Rapid-PVST · EtherChannel · LACP · HSRP · OSPF · NAT/PAT · DHCP · DNS · SSH · TACACS+ · Port Security · DHCP Snooping · Network Troubleshooting**

## Tools

* Cisco Packet Tracer
* Cisco IOS CLI

## Author

**Ali Haris Khan**

BS Software Engineering
Networking / NOC / Network Engineering

---

*This project was created as a practical networking lab to develop enterprise network design, configuration, troubleshooting, and documentation skills.*
