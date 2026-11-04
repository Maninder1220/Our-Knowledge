# Network Engineering Master Curriculum

## Basic to Advanced \| L1 Network Engineer Readiness \| Exam Preparation

**Purpose:** A structured, vendor-neutral learning and practice plan
that builds genuine networking understanding, prepares you for
entry-level Network Engineer / Network Support Engineer (L1) work, and
provides a foundation for exams such as CompTIA Network+ and Cisco CCNA.

**How to use this document:** Follow the phases in order. For every
topic, use the cycle:

1.  **READ** the concept and terminology.
2.  **DRAW** the topology, packet path, or protocol state.
3.  **EXPLAIN** it aloud without reading.
4.  **DO** the configuration or command-line exercise.
5.  **CAPTURE** traffic where relevant.
6.  **BREAK** one component deliberately in a lab.
7.  **TROUBLESHOOT** using evidence.
8.  **DOCUMENT** the symptom, cause, fix, and verification.

Do not mark a topic complete because you have watched a video or
memorised a definition. Mark it complete when you can explain it,
perform a basic task, identify common failure modes, and verify the
result.

------------------------------------------------------------------------

# 1. What an L1 Network Engineer must be able to do

An L1 engineer is usually the first technical point of contact for
network incidents. The role is not to redesign every network or
independently change production routing. It is to gather accurate
evidence, follow approved procedures, restore service within authority,
document actions, and escalate with useful diagnostic information.

## 1.1 Core L1 responsibilities

-   Receive, acknowledge, classify, and update network incidents.
-   Confirm the affected user, device, location, VLAN, subnet,
    application, and time of failure.
-   Determine whether the issue affects one endpoint, multiple
    endpoints, one subnet, one site, or many sites.
-   Check physical link, interface status, Wi-Fi association, IP
    configuration, gateway, DNS, and reachability.
-   Perform approved first-line checks on switches, routers, firewalls,
    access points, VPNs, and network monitoring systems.
-   Use ping, traceroute/tracert, nslookup/dig, ipconfig/ifconfig, `ip`,
    `ss`, `ethtool`, and approved packet captures.
-   Identify common symptoms: link down, duplicate IP, wrong VLAN, DHCP
    failure, DNS failure, gateway unreachable, packet loss, latency, VPN
    disconnected, interface errors.
-   Follow runbooks and change-control procedures.
-   Avoid unauthorised production changes.
-   Record timestamps, source/destination addresses, test results,
    device names, interface names, error messages, and actions taken.
-   Escalate to L2/L3 with evidence and a clear problem statement.
-   Verify service restoration with the affected user or monitoring
    system.

## 1.2 L1 versus L2 versus L3

  -----------------------------------------------------------------------
  Level                   Typical scope           Expected behaviour
  ----------------------- ----------------------- -----------------------
  L1                      Monitoring, triage,     Identify, isolate,
                          basic connectivity      document, restore
                          checks, known fixes,    within runbook,
                          ticket handling         escalate

  L2                      Deeper device, VLAN,    Diagnose configuration
                          routing, firewall,      and network-path
                          wireless, and service   problems; implement
                          troubleshooting         approved changes

  L3 / Engineering        Complex design,         Design, optimise,
                          architecture, advanced  automate, perform
                          routing, security,      complex root-cause
                          vendor defects, major   analysis
                          incidents               
  -----------------------------------------------------------------------

An L1 engineer must understand the underlying concepts even when a
change is escalated. The aim is not to guess or run commands blindly.

------------------------------------------------------------------------

# 2. Learning outcomes and competency standard

By the end of this curriculum, you should be able to:

-   Explain how data moves from an application on one host to an
    application on another host.
-   Distinguish frames, packets, segments, datagrams, ports, MAC
    addresses, and IP addresses.
-   Explain the OSI model and TCP/IP model and use them as
    troubleshooting frameworks.
-   Read IPv4 and IPv6 configuration and calculate subnets.
-   Explain Ethernet switching, MAC learning, ARP, VLANs, trunks, STP,
    and link aggregation.
-   Explain routing tables, default routes, static routes, and dynamic
    routing at a conceptual level.
-   Explain TCP, UDP, DNS, DHCP, HTTP(S), TLS, SSH, NTP, SNMP, and
    common infrastructure services.
-   Use standard tools to check host connectivity, name resolution,
    route selection, listening ports, and packet behaviour.
-   Recognise common firewall, NAT, VPN, wireless, and network-security
    symptoms.
-   Understand monitoring metrics, logs, interface counters, flow
    records, and packet captures.
-   Troubleshoot a basic office LAN incident methodically.
-   Understand the network path in Linux, Docker, Kubernetes, and public
    cloud environments.
-   Prepare for vendor-neutral and vendor-specific entry-level
    networking examinations.

## 2.1 Mastery levels

  -----------------------------------------------------------------------
  Level                               Meaning
  ----------------------------------- -----------------------------------
  0 --- Unfamiliar                    Have not studied the topic

  1 --- Recall                        Can define terms and identify
                                      components

  2 --- Explain                       Can explain how and why it works

  3 --- Perform                       Can complete a guided lab or
                                      command sequence

  4 --- Troubleshoot                  Can diagnose a deliberately
                                      introduced failure

  5 --- Teach/design                  Can explain trade-offs and design a
                                      small solution
  -----------------------------------------------------------------------

For L1 readiness, aim for Level 4 in foundational topics and Level 2--3
in advanced topics. For an exam, also practise timed questions and
scenario-based questions.

------------------------------------------------------------------------

# 3. Phase 0 --- Computer, binary, and communication foundations

## 3.1 Digital information

-   Bit, nibble, byte, word.
-   Binary, decimal, and hexadecimal number systems.
-   Binary place values and conversions.
-   Hexadecimal representation of MAC and IPv6 addresses.
-   Bits per second versus bytes per second.
-   KB, MB, GB versus KiB, MiB, GiB.
-   Data encoding and representation.
-   Client, server, process, service, socket.
-   Operating system, kernel, network interface card (NIC).
-   Physical interface versus logical/virtual interface.

## 3.2 Data communication concepts

-   Sender, receiver, medium, message, protocol.
-   Simplex, half-duplex, full-duplex.
-   Serial and parallel communication (conceptual).
-   Bandwidth, throughput, goodput.
-   Latency, round-trip time (RTT), jitter.
-   Packet loss and retransmission.
-   Congestion and bottlenecks.
-   Error detection: parity, checksum, CRC (conceptual).
-   MTU, frame size, packet fragmentation.
-   MSS and Path MTU Discovery (PMTUD).
-   Encapsulation and decapsulation.

## 3.3 Network categories and topologies

-   PAN, LAN, WLAN, CAN, MAN, WAN, SAN.
-   Internet, intranet, extranet.
-   Client-server and peer-to-peer.
-   Bus, star, ring, mesh, point-to-point, hub-and-spoke.
-   Three-tier campus: access, distribution, core.
-   Collapsed-core architecture.
-   Data-centre leaf-spine architecture.
-   Physical topology versus logical topology.
-   Availability, redundancy, scalability, resilience.

**READ:** Explain the difference between bandwidth, throughput, latency,
jitter, and packet loss.

**DO:** Draw a home network and a small office network. Label endpoints,
access switch, wireless access point, router/firewall, ISP connection,
server, and Internet.

**CHECK:** Explain what changes when the ISP link fails versus when a
single switch port fails.

------------------------------------------------------------------------

# 4. Phase 1 --- Network models, protocols, and packet flow

## 4.1 OSI reference model

  --------------------------------------------------------------------------
  Layer             Name              Main purpose         Common examples
  ----------------- ----------------- -------------------- -----------------
  7                 Application       Network services     HTTP, DNS, SMTP,
                                      used by applications SSH

  6                 Presentation      Data representation, Character
                                      encoding, encryption encoding,
                                      concepts             serialization,
                                                           TLS-related
                                                           functions

  5                 Session           Session/dialogue     Session control
                                      management concepts  

  4                 Transport         Process-to-process   TCP, UDP
                                      delivery             

  3                 Network           Logical addressing   IPv4, IPv6, ICMP
                                      and routing          

  2                 Data Link         Local-link delivery  Ethernet, 802.1Q,
                                      and framing          MAC

  1                 Physical          Signals and          Copper, fibre,
                                      transmission media   radio
  --------------------------------------------------------------------------

Important: OSI is a reference model. The Internet protocol suite is
commonly described using the TCP/IP model. The mapping is not perfectly
one-to-one.

## 4.2 TCP/IP model

-   Link / network access layer.
-   Internet layer.
-   Transport layer.
-   Application layer.
-   Mapping TCP/IP functions to OSI layers.
-   Protocol suite and interoperability.
-   End-to-end communication.

## 4.3 Data units and addresses

-   Application data.
-   TCP segment.
-   UDP datagram.
-   IP packet.
-   Ethernet frame.
-   Bits.
-   MAC address: local-link interface identifier.
-   IP address: logical network-layer address.
-   Port number: transport-layer service/process identifier.
-   Socket: communication endpoint abstraction.
-   VLAN ID: Layer 2 broadcast-domain identifier.
-   Subnet/prefix: Layer 3 address range.

## 4.4 Encapsulation and decapsulation

Understand what headers are added at each layer and what each device
examines.

-   Application data is passed to transport.
-   TCP or UDP adds a transport header.
-   IP adds a network header.
-   Ethernet or another link technology adds link framing.
-   The receiving host removes headers in reverse order.
-   A router normally removes the incoming link-layer frame and creates
    a new link-layer frame for the next hop.
-   Source/destination IP addresses normally remain end-to-end, except
    where NAT or other translation is applied.
-   Layer 2 source/destination MAC addresses are hop-by-hop and normally
    change at each routed hop.
-   TTL in IPv4 / Hop Limit in IPv6 is decremented by routers.

## 4.5 Control plane, data plane, and management plane

-   Data plane: forwards packets/frames.
-   Control plane: learns or calculates forwarding information.
-   Management plane: configuration and administration.
-   Routing table versus forwarding table (conceptual distinction).
-   Centralised versus distributed control.

**DO:** Draw the packet path from a laptop to a remote web server. Label
DNS, gateway ARP, Ethernet, IP, TCP, TLS, and HTTP.

**CHECK:** Explain why a switch uses a MAC address while a router uses
an IP routing lookup.

------------------------------------------------------------------------

# 5. Phase 2 --- Physical layer and Ethernet

## 5.1 Physical media and components

-   Copper twisted-pair cabling.
-   UTP and STP concepts.
-   Cat5e, Cat6, Cat6A (capability and distance concepts).
-   Fibre: multimode and single-mode.
-   Fibre connectors and transceivers.
-   SFP, SFP+, QSFP (form-factor awareness).
-   Patch panels and structured cabling.
-   RJ45 connectors.
-   Ethernet speed standards.
-   Link speed and auto-negotiation.
-   Half-duplex and full-duplex.
-   Power over Ethernet (PoE).
-   Wireless radio as a transmission medium.
-   Cable faults, fibre contamination, bad optics, excessive
    attenuation.

## 5.2 Ethernet

-   IEEE 802.3 family.
-   Ethernet frame fields.
-   Preamble and start-frame delimiter (conceptual).
-   Destination MAC and source MAC.
-   EtherType/length.
-   Payload.
-   Frame Check Sequence (FCS).
-   CRC error detection.
-   Unicast, multicast, broadcast.
-   Broadcast domain and collision domain.
-   MTU and jumbo frames.
-   Speed/duplex mismatch.
-   Interface counters: errors, drops, discards, CRC, collisions (where
    applicable).

## 5.3 Common physical troubleshooting

-   Link light off.
-   Interface administratively down.
-   Interface operationally down.
-   Incorrect cable or transceiver.
-   Unsupported optic.
-   Speed mismatch.
-   Duplex mismatch.
-   CRC/input errors.
-   Interface flapping.
-   High utilisation.
-   PoE budget or power issue.
-   Fibre transmit/receive polarity and optical-level issues.

**DO:** Inspect your host's interfaces and counters using `ip -br link`,
`ip -s link`, and `ethtool <interface>` on Linux.

------------------------------------------------------------------------

# 6. Phase 3 --- Layer 2 switching

## 6.1 Switch operation

-   Layer 2 switch versus Layer 3 switch.
-   MAC address learning.
-   MAC address table / CAM table.
-   Source MAC learning.
-   Known unicast forwarding.
-   Unknown unicast flooding.
-   Broadcast forwarding.
-   Filtering.
-   MAC aging.
-   MAC table overflow and MAC flooding (security concept).
-   Store-and-forward versus cut-through switching.
-   Switch port states and administrative configuration.

## 6.2 ARP and neighbour discovery

IPv4: - ARP request and reply. - ARP cache. - Gratuitous ARP. - Proxy
ARP. - Duplicate IP symptoms. - ARP spoofing/poisoning. - Dynamic ARP
Inspection (DAI).

IPv6: - Neighbor Discovery Protocol (NDP). - Neighbor Solicitation and
Advertisement. - Router Solicitation and Advertisement. - Duplicate
Address Detection. - Neighbor cache. - ICMPv6 dependency.

## 6.3 VLANs

-   Purpose of VLANs.
-   VLAN as a separate Layer 2 broadcast domain.
-   VLAN ID and range concepts.
-   Access ports.
-   Trunk ports.
-   IEEE 802.1Q tagging.
-   Native VLAN concepts.
-   Allowed VLAN lists.
-   Voice VLAN (awareness).
-   VLAN database and port membership.
-   Inter-VLAN routing.
-   Switched Virtual Interface (SVI).
-   Router-on-a-stick.
-   VLAN pruning.
-   VLAN hopping and mitigation.
-   VLAN design and IP subnet mapping.

## 6.4 Spanning Tree Protocol

-   Why Layer 2 loops are dangerous.
-   Broadcast storms and MAC table instability.
-   STP purpose.
-   Root bridge election.
-   Bridge ID and priority.
-   Root port.
-   Designated port.
-   Port roles and states.
-   Path cost.
-   BPDU.
-   RSTP.
-   MSTP.
-   PortFast/edge ports.
-   BPDU Guard.
-   Root Guard.
-   Loop Guard.
-   UDLD (vendor/implementation awareness).

## 6.5 Link aggregation

-   Link aggregation purpose.
-   LACP.
-   Static port-channel.
-   Member-link consistency.
-   Load distribution.
-   Redundancy and aggregate bandwidth.
-   Common misconfiguration symptoms.

**DO:** Build two switches with multiple VLANs, a trunk, and redundant
links in a simulator. Observe MAC learning and STP behaviour. Introduce
a trunk mismatch and diagnose it.

------------------------------------------------------------------------

# 7. Phase 4 --- IPv4 addressing and subnetting

This is a must-master phase. Do not move on while subnet calculations
are unclear.

## 7.1 IPv4 fundamentals

-   32-bit address.
-   Dotted-decimal notation.
-   Binary representation.
-   Network bits and host bits.
-   Subnet mask.
-   Prefix notation/CIDR.
-   Network address.
-   Broadcast address.
-   Usable host addresses.
-   Default gateway.
-   Host route, network route, default route.
-   Public and private addressing.
-   Loopback: 127.0.0.0/8.
-   Link-local/APIPA: 169.254.0.0/16.
-   RFC 1918 private ranges:
    -   10.0.0.0/8
    -   172.16.0.0/12
    -   192.168.0.0/16
-   Special-purpose and reserved addresses.
-   Unspecified and limited broadcast addresses.

## 7.2 Subnetting

-   Binary-to-decimal conversion.
-   Decimal-to-binary conversion.
-   Prefix-to-mask conversion.
-   Mask-to-prefix conversion.
-   Network ID calculation.
-   Broadcast calculation.
-   Usable host range.
-   Hosts per subnet.
-   Number of subnets.
-   Block size/increment.
-   Classful addressing as historical context.
-   Classless Inter-Domain Routing (CIDR).
-   Variable Length Subnet Masking (VLSM).
-   Supernetting.
-   Route summarisation.
-   Longest Prefix Match.
-   Address allocation and planning.
-   Subnet overlap detection.

## 7.3 Required subnetting practice

Practise all of these until you can solve them without a calculator:

-   /8, /16, /24.
-   /25, /26, /27, /28, /29, /30.
-   /23, /22, /21, /20.
-   Given an IP/prefix, find network, broadcast, and host range.
-   Given a host requirement, choose the smallest suitable subnet.
-   Allocate multiple departments using VLSM.
-   Summarise contiguous networks.
-   Identify overlapping subnets.
-   Determine whether two hosts are in the same subnet.

**DO:** Create an IP plan for a 200-user office with user, voice,
server, guest, printer, and management segments. Reserve space for
growth and document gateway addresses.

------------------------------------------------------------------------

# 8. Phase 5 --- IPv6

## 8.1 Address structure

-   128-bit address.
-   Hexadecimal notation.
-   Eight hextets.
-   Zero compression.
-   Prefix notation.
-   Network prefix and interface identifier concepts.
-   Global Unicast.
-   Link-local (`fe80::/10`).
-   Unique Local (`fc00::/7`).
-   Multicast (`ff00::/8`).
-   Loopback (`::1`).
-   Unspecified (`::`).
-   Anycast.
-   No broadcast in IPv6.

## 8.2 IPv6 configuration and operation

-   SLAAC.
-   DHCPv6 stateful and stateless concepts.
-   Router Advertisements.
-   Neighbor Discovery.
-   Duplicate Address Detection.
-   ICMPv6.
-   Prefix delegation.
-   Static IPv6 addressing.
-   Default route.
-   IPv6 routing.
-   Dual stack.
-   IPv6-only networks and transition concepts.
-   DNS AAAA records.
-   DNS64/NAT64 awareness.
-   IPv6 firewall policy.
-   Common IPv6 troubleshooting.

**DO:** Inspect IPv6 addresses and routes using `ip -6 addr` and
`ip -6 route`. Test IPv6 only where your network supports it.

------------------------------------------------------------------------

# 9. Phase 6 --- Routing fundamentals

## 9.1 Router operation

-   Router interfaces.
-   Layer 3 forwarding.
-   Connected routes.
-   Local routes.
-   Static routes.
-   Default routes.
-   Dynamic routes.
-   Next-hop address.
-   Exit interface.
-   Routing table.
-   Forwarding table.
-   Administrative distance / route preference (vendor-specific
    terminology).
-   Metric.
-   Longest Prefix Match.
-   Equal-Cost Multi-Path (ECMP).
-   Recursive next-hop resolution.
-   Route summarisation.
-   Route redistribution (advanced awareness).
-   Asymmetric routing.
-   Blackhole routes.
-   Routing loops.
-   TTL and traceroute.

## 9.2 Static routing

-   Configure and interpret static routes.
-   Default route.
-   Host route.
-   Floating static route.
-   IPv4 and IPv6 static routes.
-   Next-hop versus exit-interface route.
-   Route verification.
-   Failure and failover behaviour.

## 9.3 Dynamic routing overview

Understand the categories before studying protocols:

-   Interior Gateway Protocol (IGP).
-   Exterior Gateway Protocol (EGP).
-   Distance vector.
-   Link state.
-   Path vector.
-   Autonomous System (AS).
-   Convergence.
-   Neighbour/adjacency.
-   Routing metrics.
-   Control-plane updates.

## 9.4 OSPF foundations

-   OSPF purpose and operation.
-   Router ID.
-   Hello and dead timers.
-   Neighbor discovery.
-   Neighbor states.
-   Adjacency.
-   DR/BDR concepts on broadcast networks.
-   Link State Advertisements.
-   Link State Database.
-   SPF calculation.
-   Cost.
-   Area concept.
-   Area 0.
-   Basic single-area OSPF.
-   OSPF authentication awareness.
-   Common neighbour failures.

## 9.5 BGP foundations

-   Inter-domain routing.
-   Autonomous System Number.
-   eBGP and iBGP.
-   TCP port 179.
-   BGP neighbour.
-   BGP state machine.
-   Path attributes.
-   AS_PATH.
-   NEXT_HOP.
-   LOCAL_PREF.
-   MED.
-   Communities.
-   Prefix advertisement and filtering.
-   Route selection concepts.
-   Route leaks and hijacks (security awareness).

For L1, understand the purpose and basic symptoms of OSPF/BGP failures.
Detailed route policy engineering is normally an L2/L3 responsibility.

------------------------------------------------------------------------

# 10. Phase 7 --- Transport layer: TCP, UDP, and ports

## 10.1 TCP

-   Connection-oriented transport.
-   TCP segment structure.
-   Source and destination ports.
-   Sequence number.
-   Acknowledgement number.
-   SYN, ACK, FIN, RST, PSH, URG flags.
-   Three-way handshake.
-   Connection termination.
-   Reliable ordered byte stream.
-   Acknowledgements.
-   Retransmissions.
-   Duplicate ACKs.
-   Sliding window.
-   Flow control.
-   Congestion control.
-   Receive window.
-   Window scaling.
-   MSS.
-   MTU relationship.
-   TCP reset.
-   TIME_WAIT.
-   Socket states.
-   TCP keepalive.
-   Common causes of connection timeout and refusal.

## 10.2 UDP

-   Connectionless datagrams.
-   UDP header.
-   Ports.
-   No built-in delivery guarantee.
-   Application-managed reliability.
-   Common use cases.
-   UDP troubleshooting.
-   QUIC awareness.

## 10.3 Common ports and protocols

       Port Protocol/service   Transport commonly used
  --------- ------------------ ------------------------------------------
      20/21 FTP data/control   TCP
         22 SSH                TCP
         23 Telnet             TCP
         25 SMTP               TCP
         53 DNS                UDP and TCP
      67/68 DHCPv4             UDP
         69 TFTP               UDP
         80 HTTP               TCP
        110 POP3               TCP
        123 NTP                UDP
        143 IMAP               TCP
    161/162 SNMP               UDP
        179 BGP                TCP
        389 LDAP               TCP/UDP depending on use
        443 HTTPS              TCP; HTTP/3 uses QUIC over UDP
        445 SMB                TCP
        514 Syslog             Traditionally UDP; TCP/TLS options exist
        587 SMTP submission    TCP
        636 LDAPS              TCP
        993 IMAPS              TCP
        995 POP3S              TCP
       3306 MySQL              TCP
       5432 PostgreSQL         TCP

Do not only memorise port numbers. Know what the service does, how
clients use it, how to test it, and what a blocked or unavailable
service looks like.

------------------------------------------------------------------------

# 11. Phase 8 --- Network services

## 11.1 DNS

-   DNS purpose and hierarchy.
-   Stub resolver.
-   Recursive resolver.
-   Root, TLD, authoritative servers.
-   Recursive versus iterative query.
-   DNS caching.
-   TTL.
-   Forward lookup.
-   Reverse lookup.
-   A, AAAA, CNAME, MX, NS, SOA, TXT, PTR records.
-   DNS zone.
-   Delegation.
-   Split-horizon DNS.
-   Conditional forwarding.
-   DNS propagation misconceptions.
-   DNSSEC.
-   DNS over TLS/HTTPS awareness.
-   Common resolution failures.

## 11.2 DHCP

-   Dynamic versus static configuration.
-   DHCP Discover, Offer, Request, Acknowledge (DORA).
-   Scope/pool.
-   Lease.
-   Reservation.
-   Exclusion.
-   Options: gateway, DNS, domain, lease time.
-   DHCP relay / helper.
-   DHCP server availability.
-   DHCP exhaustion.
-   Rogue DHCP.
-   Duplicate address.
-   DHCP snooping.

## 11.3 Other services

-   NTP and time synchronisation.
-   SSH and secure remote administration.
-   Telnet and why it is insecure.
-   HTTP and HTTPS.
-   SMTP, IMAP, POP3.
-   FTP, FTPS, SFTP distinction.
-   TFTP.
-   LDAP and LDAPS.
-   RADIUS.
-   TACACS+.
-   SNMP.
-   Syslog.
-   SMB.
-   Proxy and reverse proxy.
-   Load balancer.
-   Certificate services and PKI.

## 11.4 HTTP, TLS, and certificates

-   Request and response.
-   Methods: GET, POST, PUT, PATCH, DELETE, HEAD.
-   Status codes: 2xx, 3xx, 4xx, 5xx.
-   Headers.
-   Cookies and sessions (conceptual).
-   HTTPS.
-   TLS handshake.
-   Certificate, subject, SAN, issuer, validity.
-   Certificate chain and trust store.
-   Public/private key concepts.
-   SNI.
-   Certificate expiry and hostname mismatch.
-   TLS version/cipher compatibility (conceptual).

------------------------------------------------------------------------

# 12. Phase 9 --- NAT, ACLs, firewalls, and security

## 12.1 NAT

-   Private versus public addressing.
-   Static NAT.
-   Dynamic NAT.
-   PAT/NAT overload.
-   Source NAT (SNAT).
-   Destination NAT (DNAT).
-   Port forwarding.
-   NAT table/translation state.
-   NAT and connection tracking.
-   Hairpin NAT awareness.
-   NAT troubleshooting.
-   NAT is not a substitute for a firewall.

## 12.2 ACLs and firewall fundamentals

-   Permit/deny rules.
-   Rule order and first-match behaviour (platform-dependent details).
-   Source and destination.
-   Protocol and port.
-   Stateful versus stateless filtering.
-   Inbound/outbound direction.
-   Default deny and explicit allow.
-   Standard and extended ACL concepts.
-   Security zones.
-   DMZ.
-   Host firewall versus network firewall.
-   Firewall logs.
-   Session tables.
-   Rule shadowing and overly broad rules.
-   Change approval and rollback.

## 12.3 Security concepts

-   Confidentiality, integrity, availability.
-   Authentication, authorisation, accounting (AAA).
-   Least privilege.
-   Network segmentation.
-   VLAN and subnet separation.
-   802.1X and NAC.
-   RADIUS and TACACS+.
-   VPN.
-   IPsec: IKE, ESP, tunnel/transport mode concepts.
-   IDS and IPS.
-   DDoS.
-   Spoofing.
-   ARP poisoning.
-   DHCP starvation.
-   MAC flooding.
-   VLAN hopping.
-   DNS poisoning.
-   SYN flood.
-   Rogue access point.
-   Wireless encryption.
-   Secure device management.
-   SSH, SNMPv3, secure management VLAN.
-   Configuration backup and secrets handling.
-   Zero Trust principles.

**L1 boundary:** Never disable a firewall, change a production ACL, or
alter VPN/security policy merely to see whether it fixes an issue.
Follow the approved change process.

------------------------------------------------------------------------

# 13. Phase 10 --- Wireless networking

-   IEEE 802.11 family.
-   2.4 GHz, 5 GHz, 6 GHz bands.
-   Channel and channel width.
-   Frequency and wavelength (basic concepts).
-   RSSI.
-   SNR.
-   Interference.
-   Co-channel and adjacent-channel interference.
-   Access point.
-   Wireless LAN controller.
-   SSID and BSSID.
-   Authentication and association.
-   WPA2 and WPA3.
-   Personal versus Enterprise mode.
-   802.1X and RADIUS.
-   Roaming.
-   Mesh wireless.
-   Guest wireless.
-   Captive portal.
-   RF coverage and channel planning.
-   Hidden node and airtime contention concepts.
-   Wireless client isolation.
-   Common wireless troubleshooting.

**DO:** Investigate a wireless complaint by separating authentication
failure, association failure, DHCP failure, DNS failure, weak signal,
interference, and upstream connectivity failure.

------------------------------------------------------------------------

# 14. Phase 11 --- WAN and remote connectivity

-   Leased lines.
-   Broadband and fibre Internet.
-   Ethernet WAN.
-   MPLS concepts.
-   Layer 2 and Layer 3 VPN concepts.
-   Site-to-site VPN.
-   Remote-access VPN.
-   IPsec.
-   GRE.
-   SD-WAN.
-   WAN failover.
-   Dual ISP.
-   BFD awareness.
-   QoS over WAN.
-   Carrier handoff.
-   Circuit ID and provider escalation.
-   Latency and packet loss across WAN.
-   Cloud VPN and dedicated connectivity.

For L1, be able to identify whether a site outage is local LAN, edge
device, ISP circuit, VPN, DNS, or remote application related.

------------------------------------------------------------------------

# 15. Phase 12 --- Network monitoring and operations

## 15.1 Monitoring and telemetry

-   SNMP polling.
-   SNMP v1/v2c/v3.
-   MIB and OID concepts.
-   SNMP traps and informs.
-   Syslog severity.
-   Interface utilisation.
-   Interface errors/discards.
-   CPU and memory.
-   Device availability.
-   ICMP monitoring.
-   Flow telemetry: NetFlow, IPFIX, sFlow.
-   Streaming telemetry awareness.
-   Packet capture.
-   Network discovery and inventory.
-   Configuration backup.
-   Alert thresholds and alert fatigue.

## 15.2 Understand the data types

  -----------------------------------------------------------------------
  Data type                           What it answers
  ----------------------------------- -----------------------------------
  Metrics                             How much, how often, how fast, how
                                      many errors?

  Logs                                What event occurred and when?

  Flow records                        Which endpoints communicated and
                                      how much traffic?

  Packet capture                      What packets and protocol exchanges
                                      were observed at this capture
                                      point?

  Configuration                       What was the device intended to do?

  Inventory/topology                  Which devices, interfaces, links,
                                      and dependencies exist?
  -----------------------------------------------------------------------

## 15.3 Incident management

-   Incident versus service request versus problem.
-   Severity and priority.
-   Impact and urgency.
-   SLA and response targets.
-   Acknowledgement and updates.
-   Escalation matrix.
-   Major incident process.
-   Change management.
-   Maintenance window.
-   Rollback plan.
-   Root cause analysis (RCA).
-   Known error and knowledge base.
-   Shift handover.
-   Clear ticket writing.

## 15.4 Network monitoring platforms

Understand the purpose of tools such as:

-   Zabbix.
-   LibreNMS.
-   Observium.
-   Nagios.
-   PRTG (commercial).
-   SolarWinds (commercial).
-   ntopng.
-   Prometheus and exporters.
-   Grafana.
-   SigNoz for relevant telemetry correlation.
-   Vendor-native network management systems.

A monitoring dashboard does not replace packet analysis, device
configuration review, or a verified end-to-end test.

------------------------------------------------------------------------

# 16. Phase 13 --- Network troubleshooting methodology

This phase should be practised continuously, not only at the end.

## 16.1 Standard incident workflow

1.  Confirm the exact symptom.
2.  Identify affected users, devices, location, application, and start
    time.
3.  Establish scope: one endpoint, one VLAN, one site, multiple sites,
    or all users.
4.  Ask what changed: cabling, power, configuration, maintenance, ISP,
    DHCP, DNS, endpoint, or application.
5.  Check physical/interface status.
6.  Verify IP address, mask/prefix, gateway, DNS, and DHCP lease.
7.  Test local loopback and local interface as appropriate.
8.  Test default gateway.
9.  Test a known reachable IP.
10. Test DNS resolution.
11. Test destination port/application.
12. Trace the route where useful.
13. Capture packets if authorised and needed.
14. Review monitoring, logs, and interface counters.
15. Compare results from a working endpoint and a failing endpoint.
16. Apply only an approved known fix.
17. Verify service restoration.
18. Record evidence and close or escalate.

## 16.2 Understand what each test proves

  -----------------------------------------------------------------------
  Test                    What it can establish   What it does not prove
  ----------------------- ----------------------- -----------------------
  Link status             Interface/link appears  End-to-end connectivity
                          operational             

  `ipconfig` / `ip addr`  Local IP configuration  Correct upstream
                                                  routing

  Ping gateway            ICMP response from      All application ports
                          gateway                 work

  Ping public IP          ICMP reachability to    DNS works or all
                          that target             Internet traffic works

  DNS query               Resolver returned a     Application server is
                          response                healthy

  TCP port test           A TCP connection        Application logic is
                          attempt/result          healthy

  Traceroute              Some information about  Every hop must respond
                          forwarding path         or path is necessarily
                                                  broken

  Packet capture          Packets observed at     What happened outside
                          capture point           that capture point

  Interface counters      Local interface         Root cause without
                          error/drop information  correlation
  -----------------------------------------------------------------------

## 16.3 Common incident scenarios

For every scenario, practise: symptom, scope, hypothesis, test,
evidence, fix/escalation, verification.

1.  User has no network access.
2.  User receives a 169.254.x.x address.
3.  User has an IP but cannot reach the default gateway.
4.  Gateway is reachable but Internet is unavailable.
5.  IP works but hostname does not.
6.  DNS resolves but the website does not open.
7.  One application port is blocked.
8.  One VLAN cannot reach another VLAN.
9.  One switch port is down.
10. Interface has CRC errors.
11. Link is flapping.
12. Users experience intermittent packet loss.
13. Network is slow during peak hours.
14. Wi-Fi connects but no IP is assigned.
15. Wi-Fi authentication fails.
16. VPN is connected but internal resources are unreachable.
17. A branch office is down.
18. DHCP scope is exhausted.
19. Duplicate IP address is reported.
20. A server is reachable from one subnet but not another.
21. OSPF neighbour is down.
22. BGP peer is down.
23. A firewall rule appears to block a service.
24. A route exists but return traffic fails.
25. MTU/PMTUD issue affects only some applications.

## 16.4 Troubleshooting concepts to master

-   Symptom versus root cause.
-   Correlation versus causation.
-   Fault isolation.
-   Baseline and comparison.
-   Hypothesis-driven testing.
-   Change correlation.
-   One-variable-at-a-time testing.
-   Evidence preservation.
-   Packet loss localisation.
-   Asymmetric routing.
-   Stateful firewall behaviour.
-   Return path.
-   MTU black hole.
-   DNS caching.
-   Time synchronisation.
-   Escalation with evidence.

------------------------------------------------------------------------

# 17. Phase 14 --- Essential commands and tools

Learn the equivalent commands on Windows and Linux. Exact options can
differ by operating-system version.

## 17.1 Windows

  Command                               Purpose
  ------------------------------------- ---------------------------------
  `ipconfig /all`                       Full IP configuration
  `ipconfig /release`                   Release DHCP lease
  `ipconfig /renew`                     Request DHCP lease
  `ipconfig /flushdns`                  Clear DNS resolver cache
  `ping <destination>`                  ICMP reachability
  `tracert <destination>`               Route path investigation
  `pathping <destination>`              Path and loss investigation
  `nslookup <name>`                     DNS query
  `arp -a`                              ARP cache
  `route print`                         Routing table
  `netstat -ano`                        Connections and listening ports
  `Test-NetConnection host -Port 443`   TCP connectivity test
  `Get-NetIPConfiguration`              PowerShell IP information
  `Get-NetRoute`                        PowerShell route information

## 17.2 Linux

  Command                      Purpose
  ---------------------------- -----------------------------------
  `ip -br link`                Interface summary
  `ip -br addr`                IP address summary
  `ip route`                   IPv4 routes
  `ip -6 route`                IPv6 routes
  `ip rule`                    Policy routing
  `ip neigh`                   Neighbour/ARP cache
  `ping`                       ICMP test
  `traceroute` / `tracepath`   Path investigation
  `mtr`                        Continuous path diagnostics
  `dig`                        DNS investigation
  `getent hosts`               System name resolution
  `ss -tulpen`                 Socket inspection
  `curl -v`                    Application/TLS/HTTP diagnostics
  `nc -vz host port`           TCP port test
  `tcpdump`                    Packet capture
  `ethtool`                    NIC properties/statistics
  `ip -s link`                 Interface statistics
  `nmcli`                      NetworkManager
  `bridge link`                Bridge information
  `nft list ruleset`           Firewall rules
  `conntrack -L`               Connection tracking, if installed
  `tc -s qdisc`                Traffic-control statistics

## 17.3 Cisco IOS/IOS XE awareness

Learn to recognise and interpret commands in a lab or read-only
production session:

``` text
show version
show inventory
show interfaces status
show interfaces
show ip interface brief
show ipv6 interface brief
show mac address-table
show vlan brief
show interfaces trunk
show spanning-tree
show etherchannel summary
show ip arp
show ip route
show ip protocols
show ip ospf neighbor
show ip bgp summary
show access-lists
show logging
show running-config
```

Command syntax differs across vendors and operating systems. Do not
assume Cisco IOS commands work on Juniper, Arista, Linux, or a cloud
platform.

## 17.4 Packet analysis

Learn Wireshark:

-   Capture versus display filters.
-   Ethernet II.
-   ARP.
-   IPv4/IPv6.
-   ICMP.
-   TCP handshake.
-   TCP retransmissions.
-   DNS queries and replies.
-   DHCP DORA.
-   HTTP.
-   TLS handshake metadata.
-   VLAN tags.
-   TCP stream following.
-   Capture interface selection.
-   Packet timestamps.
-   Checksum/offload caveats.

Useful display filters:

``` text
arp
icmp
icmpv6
dns
dhcp
tcp
udp
ip.addr == 192.168.1.10
tcp.port == 443
tcp.flags.syn == 1 && tcp.flags.ack == 0
tcp.analysis.retransmission
```

------------------------------------------------------------------------

# 18. Phase 15 --- Linux networking

This is an extension for engineers who work with Linux servers and
infrastructure.

-   NIC and virtual NIC.
-   Interface naming.
-   IP addressing.
-   Static and DHCP configuration.
-   Routing tables.
-   Policy routing.
-   ARP/NDP.
-   Linux bridge.
-   VLAN subinterfaces.
-   Bonding/teaming.
-   Network namespaces.
-   veth pairs.
-   TUN/TAP concepts.
-   Netfilter.
-   nftables.
-   iptables compatibility.
-   Conntrack.
-   NAT and masquerading.
-   Traffic control (`tc`).
-   NetworkManager and `nmcli`.
-   systemd-resolved and resolver configuration.
-   Socket inspection.
-   Kernel network counters.
-   MTU.
-   Firewall zones (firewalld awareness).
-   Network troubleshooting on RHEL-family and Ubuntu systems.

## 18.1 Linux practical lab

``` bash
# Interface status
ip -br link

# Addresses
ip -br addr

# Routes
ip route

# Policy rules
ip rule

# Neighbours
ip neigh

# Listening ports
ss -tulpen

# DNS
dig example.com
getent hosts example.com

# Interface counters
ip -s link

# NIC information
sudo ethtool <interface>

# Firewall
sudo nft list ruleset

# Packet capture
sudo tcpdump -ni any

# NetworkManager connections
nmcli connection show
```

------------------------------------------------------------------------

# 19. Phase 16 --- Cloud, virtualisation, Docker, and Kubernetes networking

These are advanced extensions. Learn them after you understand
conventional switching, routing, IP addressing, and packet flow.

## 19.1 Virtual networking

-   Virtual NIC.
-   Virtual switch.
-   Hypervisor networking.
-   Bridged networking.
-   NAT networking.
-   Host-only networking.
-   Overlay network.
-   Virtual firewall.
-   Virtual router.
-   VLAN trunk to hypervisor.
-   VM-to-VM and VM-to-host communication.

## 19.2 Cloud networking concepts

Learn the common design patterns across AWS, Azure, and GCP:

-   VPC/VNet.
-   Subnet.
-   CIDR planning.
-   Route tables.
-   Internet gateway or Internet connectivity equivalent.
-   NAT gateway.
-   Firewall/security groups.
-   Network ACLs.
-   Peering.
-   Private service access/endpoints.
-   Private DNS.
-   Load balancers.
-   Availability zones and regions.
-   Site-to-site VPN.
-   Dedicated connectivity.
-   Hybrid routing.
-   Transit networking.
-   Cloud flow logs.
-   Cloud network security.
-   Shared services network.
-   Hub-and-spoke architecture.

## 19.3 Docker networking

-   Network namespaces.
-   Bridge driver.
-   Host driver.
-   None driver.
-   Overlay driver.
-   Port publishing.
-   DNAT/SNAT.
-   Container DNS.
-   Container-to-container traffic.
-   Container-to-host traffic.
-   Container egress.
-   Bridge and veth interfaces.
-   Firewall interactions.
-   MTU and overlay concerns.

## 19.4 Kubernetes networking

-   Kubernetes network model.
-   Node IP, Pod IP, Service IP.
-   Pod CIDR and Service CIDR.
-   CNI.
-   kube-proxy.
-   Cluster DNS.
-   Pod-to-pod.
-   Pod-to-service.
-   Pod-to-node.
-   Node-to-pod.
-   Ingress and Gateway API.
-   NodePort and LoadBalancer.
-   EndpointSlices.
-   NetworkPolicy.
-   Egress.
-   CNI routing and overlay models.
-   MTU.
-   Service datapath.
-   eBPF awareness.
-   Calico architecture.
-   Calico IPAM.
-   Calico BGP and VXLAN modes.
-   Calico Felix and Typha.
-   BGP peering and route advertisement.
-   NetworkPolicy troubleshooting.

**L1 target:** Understand the basic packet path and identify which
team/component owns a failure. Advanced CNI or BGP changes should be
escalated unless explicitly authorised.

------------------------------------------------------------------------

# 20. Phase 17 --- Advanced topics to study after L1 foundations

These are important for long-term progression, but they should not delay
readiness for an L1 role.

## 20.1 Enterprise routing and switching

-   Advanced OSPF.
-   Multi-area OSPF.
-   OSPF summarisation and redistribution.
-   Advanced BGP policy.
-   Route maps and prefix lists.
-   Route reflectors.
-   BGP communities.
-   IS-IS.
-   EIGRP (vendor-specific relevance).
-   VRF.
-   HSRP, VRRP, GLBP.
-   ECMP.
-   BFD.
-   Multicast: IGMP, PIM.
-   QoS: classification, marking, queuing, shaping, policing.
-   MPLS.
-   L3VPN concepts.
-   SD-WAN.

## 20.2 Data-centre networking

-   Leaf-spine.
-   Underlay and overlay.
-   VXLAN.
-   VTEP.
-   VNI.
-   EVPN.
-   BGP EVPN.
-   Anycast gateway.
-   East-west and north-south traffic.
-   Data-centre interconnect.
-   High-speed Ethernet.
-   Storage networking fundamentals.

## 20.3 Network automation

-   Python fundamentals.
-   JSON and YAML.
-   REST APIs.
-   HTTP methods and status codes.
-   Authentication and API tokens.
-   SSH automation.
-   Ansible.
-   NETCONF.
-   RESTCONF.
-   YANG.
-   gNMI.
-   OpenConfig.
-   Git.
-   Configuration templates.
-   Automated backups.
-   Configuration validation.
-   Drift detection.
-   CI/CD for network changes.
-   Infrastructure as Code.

## 20.4 Network architecture and design

-   Requirements gathering.
-   HLD and LLD.
-   IP address plan.
-   VLAN and subnet design.
-   Routing design.
-   Security-zone design.
-   Redundancy and failure domains.
-   Capacity planning.
-   QoS requirements.
-   Monitoring design.
-   Change and rollback plans.
-   Disaster recovery.
-   Documentation standards.

------------------------------------------------------------------------

# 21. Practical lab progression

Use a simulator first, then Linux-based labs, then more realistic
multi-vendor emulation.

  -----------------------------------------------------------------------
  Lab ID                  Assignment              Required outcome
  ----------------------- ----------------------- -----------------------
  LAB-01                  Connect two hosts       Understand Ethernet and
                                                  local communication

  LAB-02                  Configure IPv4          Correct address,
                                                  prefix, gateway

  LAB-03                  Subnet calculation      Calculate network and
                                                  broadcast

  LAB-04                  Connect two subnets     Understand router
                                                  forwarding

  LAB-05                  Build VLANs             Separate broadcast
                                                  domains

  LAB-06                  Configure trunks        Carry multiple VLANs

  LAB-07                  Configure STP           Prevent Layer 2 loops

  LAB-08                  Configure DHCP          Observe DORA

  LAB-09                  Configure DNS           Resolve names

  LAB-10                  Configure inter-VLAN    Permit controlled
                          routing                 routed communication

  LAB-11                  Configure static routes Reach remote networks

  LAB-12                  Configure OSPF          Learn dynamic routing

  LAB-13                  Inspect TCP handshake   Understand connection
                                                  establishment

  LAB-14                  Capture DNS/DHCP        Decode protocols in
                                                  Wireshark

  LAB-15                  Configure NAT           Understand address
                                                  translation

  LAB-16                  Apply ACL/firewall      Restrict traffic and
                          rules                   verify

  LAB-17                  Configure wireless      Separate Wi-Fi
                                                  association and IP
                                                  issues

  LAB-18                  Build a VPN lab         Understand tunnel
                                                  connectivity

  LAB-19                  Monitor interfaces      Detect errors and
                                                  utilisation

  LAB-20                  Troubleshoot 10         Build L1 incident
                          injected faults         confidence

  LAB-21                  Linux namespaces and    Understand kernel
                          veth                    networking

  LAB-22                  Linux bridge and VLAN   Build virtual Layer 2
                                                  network

  LAB-23                  FRRouting OSPF/BGP      Practise open routing
                                                  protocols

  LAB-24                  Docker bridge           Trace container
                                                  connectivity

  LAB-25                  Kubernetes Pod          Trace CNI traffic
                          networking              

  LAB-26                  Cloud VPC/VNet lab      Understand cloud
                                                  routing/security

  LAB-27                  Network monitoring      Observe network health
                          dashboard               

  LAB-28                  Automate a read-only    Collect and report
                          audit                   device state
  -----------------------------------------------------------------------

## Suggested tools

-   Cisco Packet Tracer: introductory switching and routing labs.
-   GNS3 or EVE-NG: multi-device network simulation/emulation.
-   Containerlab: container-based network labs.
-   FRRouting: routing protocols on Linux.
-   Wireshark: graphical packet analysis.
-   tcpdump: command-line packet analysis.
-   Linux network namespaces: kernel networking fundamentals.
-   VirtualBox: Linux host and server labs.
-   Your existing kubeadm/Calico cluster: container networking.

Use vendor images only where you have the appropriate rights and
licences.

------------------------------------------------------------------------

# 22. L1 troubleshooting casebook

For each case, write a ticket using the following template:

``` text
Incident ID:
Date/time:
Affected user/site:
Affected device:
Source IP:
Destination IP/name:
Source VLAN/subnet:
Destination VLAN/subnet:
Application/service:
Exact symptom:
Scope/number of affected users:
Recent changes:
Tests performed:
Results:
Relevant logs/packet evidence:
Likely fault domain:
Action taken:
Escalation team:
Current status:
Verification:
```

## Case 1 --- No IP address

**Symptom:** User cannot access the network. Host has `169.254.x.x`.

Investigate: - Is the NIC enabled? - Is the cable/link working? - Is the
correct SSID connected? - Is the VLAN correct? - Is DHCP available? - Is
the DHCP scope exhausted? - Is DHCP relay functioning? - Is the DHCP
request reaching the server?

## Case 2 --- Gateway unreachable

**Symptom:** Host has a valid IP but cannot ping its default gateway.

Investigate: - Correct prefix/mask? - Correct gateway? - Same subnet? -
VLAN membership? - Access/trunk configuration? - ARP/neighbor
resolution? - Switch port status? - Gateway interface status? -
Firewall/ICMP policy?

## Case 3 --- IP works, domain fails

**Symptom:** An IP-based test succeeds but hostname resolution fails.

Investigate: - Configured DNS server. - Resolver reachability. - DNS
query and response. - A versus AAAA records. - DNS timeout or
SERVFAIL. - Search suffix. - Local cache. - Split DNS or VPN DNS
configuration.

## Case 4 --- DNS works, application fails

Investigate: - Resolved destination IP. - Correct TCP/UDP port. - Route
and return route. - Firewall policy. - Service listening state. - TLS
certificate. - Proxy settings. - Application/server health.

## Case 5 --- Intermittent network

Investigate: - Interface flaps. - CRC and input errors. - Duplex/speed
negotiation. - Congestion. - Wireless interference. - Packet loss at
multiple points. - Routing changes. - Device CPU. - ISP circuit
events. - Time correlation with monitoring and logs.

## Case 6 --- One VLAN affected

Investigate: - VLAN exists. - Access port membership. - Trunk allowed
VLANs. - Native VLAN consistency. - SVI status. - Gateway address. -
DHCP scope and relay. - ACL and firewall policy. - STP state.

## Case 7 --- VPN connected, application inaccessible

Investigate: - VPN assigned address. - Routes installed. - Split
tunnel/full tunnel. - DNS servers and suffixes. - Security policy. -
Destination reachability. - Return route. - Overlapping client/local
subnet. - MTU and fragmentation. - Authentication and session logs.

------------------------------------------------------------------------

# 23. Exam preparation strategy

A strong foundation can support multiple exams, but each examination has
its own blueprint. Do not assume one syllabus automatically covers every
vendor's implementation details.

## 23.1 Recommended exam sequence

### CompTIA Network+ N10-009

Use for broad vendor-neutral knowledge:

-   Networking concepts.
-   Network implementation.
-   Network operations.
-   Network security.
-   Network troubleshooting.

### Cisco CCNA 200-301

Use for a structured associate-level networking foundation:

-   Network fundamentals.
-   Network access.
-   IP connectivity.
-   IP services.
-   Security fundamentals.
-   Automation and programmability.

**Exam-version reminder:** Cisco has announced CCNA 200-301 v2.0 from
February 3, 2027, replacing v1.1. Always use the official blueprint
applicable to your booking date.

### Later: CCNP Enterprise

After you can confidently design and troubleshoot a small enterprise
network:

-   ENCOR core.
-   An appropriate concentration exam, such as ENARSI.

## 23.2 Exam preparation checklist

-   [ ] Read the official exam blueprint.
-   [ ] Map each blueprint objective to a chapter in this curriculum.
-   [ ] Explain every objective in your own words.
-   [ ] Complete the associated practical lab.
-   [ ] Practise subnetting daily until fluent.
-   [ ] Memorise important ports after understanding the services.
-   [ ] Practise reading routing tables.
-   [ ] Interpret packet captures.
-   [ ] Practise scenario-based questions.
-   [ ] Complete timed mock examinations.
-   [ ] Review every incorrect answer.
-   [ ] Maintain an error notebook.
-   [ ] Revisit weak areas.
-   [ ] Take the exam only when practice performance is consistent.

Do not use exam dumps. Use official objectives, legitimate practice
questions, labs, and protocol documentation.

------------------------------------------------------------------------

# 24. Suggested 24-week learning plan

This is a suggested schedule, not a guarantee of job readiness. Your
progress depends on study time and how much hands-on practice you
complete.

  -----------------------------------------------------------------------
  Weeks                   Focus                   Deliverable
  ----------------------- ----------------------- -----------------------
  1--2                    Computer, binary,       Explain packet journey
                          network basics,         
                          OSI/TCP-IP              

  3--4                    Ethernet, physical      Basic switched LAN lab
                          layer, switching, ARP   

  5--6                    IPv4 and subnetting     Accurate subnet
                                                  calculations

  7                       IPv6                    Dual-stack fundamentals
                                                  lab

  8--9                    Routing and routing     Multi-subnet lab
                          tables                  

  10                      TCP, UDP and ports      Handshake packet
                                                  capture

  11--12                  DNS, DHCP, HTTP, TLS    Service troubleshooting
                          and services            lab

  13                      VLAN, trunk, STP and    Switched office LAN
                          LACP revision           

  14                      NAT, ACL, firewall and  Controlled filtering
                          security                lab

  15                      Wireless and WAN        Wireless/WAN fault
                          fundamentals            analysis

  16                      OSPF and BGP            Routing protocol lab
                          fundamentals            

  17                      Monitoring and incident Monitoring and ticket
                          handling                exercise

  18                      L1 troubleshooting      10 case studies
                          scenarios               

  19--20                  Linux networking and    Linux network lab
                          packet analysis         

  21                      Docker and Kubernetes   Pod/container
                          networking              packet-path lab

  22                      Cloud networking        Small cloud VPC/VNet
                                                  design

  23                      Automation and advanced Read-only network audit
                          revision                

  24                      Exam preparation and    Final assessment
                          mock assessments        portfolio
  -----------------------------------------------------------------------

### Weekly study routine

A practical weekly allocation:

-   40% theory and protocol understanding.
-   35% practical labs.
-   15% troubleshooting scenarios.
-   10% revision and self-assessment.

For each topic, create a one-page summary containing: 1. Definition. 2.
Why it exists. 3. How it works. 4. Important fields/headers/states. 5.
Real-world use. 6. Common failures. 7. Troubleshooting commands. 8.
Verification. 9. Interview questions.

------------------------------------------------------------------------

# 25. Professional documentation you should learn to maintain

Network engineering is also documentation and operational discipline.

Learn to create and maintain:

-   Physical network topology.
-   Logical network topology.
-   IP address management (IPAM) sheet.
-   VLAN inventory.
-   Subnet allocation sheet.
-   Router/switch inventory.
-   Interface inventory.
-   Circuit/provider inventory.
-   Firewall rule inventory.
-   Network dependency map.
-   Monitoring and alert matrix.
-   Troubleshooting runbooks.
-   Incident records.
-   Change requests.
-   Rollback plans.
-   Configuration backups.
-   HLD and LLD.
-   Root cause analysis.
-   Shift handover notes.

A useful network record should identify the device, interface, VLAN,
subnet, gateway, peer, location, purpose, owner, and relevant
dependencies.

Never put passwords, private keys, or secrets in plain-text network
documentation.

------------------------------------------------------------------------

# 26. Glossary --- terminology you must recognise

  Term     Meaning
  -------- -------------------------------------------
  NIC      Network Interface Card
  MAC      Media Access Control address
  IP       Internet Protocol
  ARP      Address Resolution Protocol
  NDP      IPv6 Neighbor Discovery Protocol
  VLAN     Virtual LAN
  SVI      Switched Virtual Interface
  STP      Spanning Tree Protocol
  RSTP     Rapid Spanning Tree Protocol
  LACP     Link Aggregation Control Protocol
  MTU      Maximum Transmission Unit
  MSS      Maximum Segment Size
  CIDR     Classless Inter-Domain Routing
  VLSM     Variable Length Subnet Masking
  NAT      Network Address Translation
  PAT      Port Address Translation
  ACL      Access Control List
  DNS      Domain Name System
  DHCP     Dynamic Host Configuration Protocol
  TCP      Transmission Control Protocol
  UDP      User Datagram Protocol
  ICMP     Internet Control Message Protocol
  OSPF     Open Shortest Path First
  BGP      Border Gateway Protocol
  IGP      Interior Gateway Protocol
  AS       Autonomous System
  VPN      Virtual Private Network
  IPsec    Internet Protocol Security
  QoS      Quality of Service
  SNMP     Simple Network Management Protocol
  Syslog   Network/system event logging protocol
  NTP      Network Time Protocol
  IDS      Intrusion Detection System
  IPS      Intrusion Prevention System
  NAC      Network Access Control
  AAA      Authentication, Authorization, Accounting
  PoE      Power over Ethernet
  SFP      Small Form-factor Pluggable
  WAN      Wide Area Network
  LAN      Local Area Network
  WLAN     Wireless Local Area Network
  MPLS     Multiprotocol Label Switching
  SD-WAN   Software-Defined WAN
  VRF      Virtual Routing and Forwarding
  VXLAN    Virtual Extensible LAN
  EVPN     Ethernet VPN
  CNI      Container Network Interface
  ECMP     Equal-Cost Multi-Path
  RTT      Round-Trip Time
  RSSI     Received Signal Strength Indicator
  SNR      Signal-to-Noise Ratio
  PMTUD    Path MTU Discovery
  RCA      Root Cause Analysis
  SLA      Service Level Agreement

------------------------------------------------------------------------

# 27. Self-assessment: Are you ready for an L1 Network Engineer role?

You should be able to answer these questions without searching for
definitions.

## Fundamentals

1.  What is the difference between a frame, packet, segment, and
    datagram?
2.  Explain the seven OSI layers.
3.  What is the difference between bandwidth and throughput?
4.  What is the difference between latency and jitter?
5.  What is a MAC address?
6.  What is an IP address?
7.  What is a default gateway?

## Switching

8.  How does a switch learn MAC addresses?
9.  What happens when a switch does not know the destination MAC?
10. What is a VLAN?
11. What is the difference between an access port and a trunk port?
12. Why is STP necessary?
13. What is ARP?

## IP and routing

14. What does `/24` mean?
15. What is the network address of `192.168.10.25/27`?
16. How do you calculate usable host addresses?
17. What is the difference between public and private IP?
18. How does a router choose a route?
19. What is longest-prefix matching?
20. What is a default route?
21. What is the purpose of OSPF and BGP?

## Transport and services

22. Explain the TCP three-way handshake.
23. What is the difference between TCP and UDP?
24. Why does DNS use both UDP and TCP?
25. Explain DHCP DORA.
26. What is the difference between HTTP and HTTPS?
27. What is a TLS certificate?
28. What is the difference between connection timeout and connection
    refused?

## Troubleshooting

29. A user has a `169.254.x.x` address. What do you investigate?
30. A user can ping `8.8.8.8` but cannot open a domain. What do you
    investigate?
31. A user can ping the gateway but cannot reach an application. What
    next?
32. What does a traceroute tell you?
33. How do you check listening ports on Linux?
34. How do you identify packet retransmissions?
35. What does an interface CRC error indicate?
36. How do you investigate intermittent packet loss?
37. Why might a VPN show connected while an internal application remains
    inaccessible?

## Operations

38. What information belongs in an L1 incident ticket?
39. When should you escalate an incident?
40. Why should you avoid unapproved changes?
41. What is the difference between a metric, log, flow record, and
    packet capture?
42. How do you verify that a network incident is actually resolved?

**Readiness target:** Be able to answer at least 90% correctly, explain
your reasoning, and complete practical troubleshooting for the
foundational scenarios. This is a personal target, not an official
employer or examination pass standard.

------------------------------------------------------------------------

# 28. Official standards and learning references

Use these to verify technical facts and learn protocol behaviour beyond
vendor summaries.

## Standards and RFCs

-   RFC Editor: https://www.rfc-editor.org/
-   RFC 791 --- Internet Protocol: https://www.rfc-editor.org/rfc/rfc791
-   RFC 1122 --- Internet host requirements:
    https://www.rfc-editor.org/rfc/rfc1122
-   RFC 8200 --- IPv6: https://www.rfc-editor.org/rfc/rfc8200
-   RFC 9293 --- TCP: https://www.rfc-editor.org/rfc/rfc9293
-   RFC 826 --- ARP: https://www.rfc-editor.org/rfc/rfc826
-   RFC 1034 --- DNS concepts and facilities:
    https://www.rfc-editor.org/rfc/rfc1034
-   RFC 1035 --- DNS implementation and specification:
    https://www.rfc-editor.org/rfc/rfc1035
-   RFC 2131 --- DHCP: https://www.rfc-editor.org/rfc/rfc2131
-   RFC 2328 --- OSPFv2: https://www.rfc-editor.org/rfc/rfc2328
-   RFC 4271 --- BGP-4: https://www.rfc-editor.org/rfc/rfc4271

## Certification blueprints

-   CompTIA Network+: https://www.comptia.org/certifications/network/
-   Cisco CCNA exam topics:
    https://learningnetwork.cisco.com/s/ccna-exam-topics
-   Cisco CCNP Enterprise:
    https://www.cisco.com/site/us/en/learn/training-certifications/certifications/enterprise/ccnp-enterprise/index.html
-   Juniper certification:
    https://www.juniper.net/us/en/training/certification.html

## Practical tools

-   Wireshark: https://www.wireshark.org/docs/
-   tcpdump: https://www.tcpdump.org/
-   Cisco Networking Academy: https://www.netacad.com/
-   GNS3: https://www.gns3.com/
-   EVE-NG: https://www.eve-ng.net/
-   Containerlab: https://containerlab.dev/
-   FRRouting: https://docs.frrouting.org/
-   Linux IP documentation:
    https://www.kernel.org/doc/html/latest/networking/

## Cloud and container networking

-   AWS networking: https://docs.aws.amazon.com/vpc/
-   Azure virtual network:
    https://learn.microsoft.com/azure/virtual-network/
-   Google Cloud VPC: https://cloud.google.com/vpc/docs
-   Kubernetes networking:
    https://kubernetes.io/docs/concepts/cluster-administration/networking/
-   Calico documentation: https://docs.tigera.io/

------------------------------------------------------------------------

# 29. Final learning principles

1.  Understand the reason a protocol exists before memorising its
    operation.
2.  Learn the packet structure and protocol fields wherever relevant.
3.  Draw network topologies by hand.
4.  Practise subnetting until calculations are fluent.
5.  Use packet captures to validate your mental model.
6.  Learn commands by understanding the evidence they provide.
7.  Troubleshoot from scope and evidence, not assumptions.
8.  Compare working and failing systems.
9.  Do not make unapproved production changes.
10. Maintain an error notebook and revisit recurring mistakes.
11. Learn vendor-neutral principles before vendor-specific syntax.
12. Follow the current official blueprint for the exam you intend to
    take.
13. Build a lab portfolio that demonstrates your ability to explain,
    configure, test, and troubleshoot.

**The final objective:** Become an engineer who can observe a network,
understand the traffic, isolate a failure, communicate evidence clearly,
and restore service safely. That is a much stronger foundation than
memorising commands or passing a multiple-choice examination.
