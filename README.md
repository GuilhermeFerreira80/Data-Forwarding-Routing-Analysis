# Enterprise Network Routing & Design — Atlantic Bay Resort & Spa

Practical networking project developed for the **Data Forwarding / Routing** course in the Informatics Engineering BSc at **ISEC**.

### Overview
Design, topology planning, and implementation of an enterprise multi-site network architecture simulated in **GNS3**. The infrastructure features a centralized core (EAC) interconnecting 7 branch units across 3 geographical zones (North, East, and West sectors), focusing on dynamic routing protocol interoperability, IPv4/IPv6 dual-stack environments, traffic engineering, and link redundancy.

### Architecture & Routing Protocols
- **Core Backbone (Multi-Area OSPF):** Multi-area OSPF deployment (Area 0, Area 1, Area 2, Area 3, Area 5) featuring **OSPF Virtual Links** to bridge non-contiguous areas to the backbone.
- **Branch Units & Heterogeneous Protocols:**
  - **EIGRP:** AS 10 and AS 1 deployments with inbound route filtering using `prefix-lists` and `distribute-lists`.
  - **RIPv2:** Configured across distinct units to evaluate distance-vector routing and VLSM handling.
  - **OSPFv3 (Native IPv6):** Dedicated end-to-end IPv6 routing domain in the Conference Center without transition tunnels.
- **Bidirectional Redistribution:** Full two-way route redistribution across boundary routers (ABRs) with tailored metric transformations to prevent loops.

### Advanced Features & Security
- **Internet Redundancy & Failover:** Primary 1 Gbps ISP uplink running PAT (NAT Overload) with floating static route failover (AD=10) via a secondary operational gateway.
- **Policy-Based Routing (PBR):** Source-based traffic path engineering configured via `route-map` in the Spa & Wellness unit.
- **Device Hardening:** Cryptographic MD5 authentication across all dynamic routing updates, secure line management, and session limiting.
