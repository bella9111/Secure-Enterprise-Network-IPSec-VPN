# 🛡️ Enterprise Government Agency Network with Site-to-Site IPSec VPN

An enterprise-grade, highly secure multi-site network architecture designed for a government agency digital HQ, featuring advanced segmentation, dynamic addressing, edge translation, and cryptographic tunnels.

## 🚀 Network Topology Overview
The topology spans multiple distinct operational sites connected via a simulated ISP core in a star/mesh hybrid WAN layout:
*   **Local Office** (Citizen Portal & Public Services)
*   **State HQ** (Central Administration & DHCP Core)
*   **Security Operations (SecOps)** (Cyber Ops & Security Core)
*   **National Data Center (NDC)** (Secure Web & DNS hosting)

<img width="1600" height="621" alt="image" src="https://github.com/user-attachments/assets/e6c5cd38-9f3a-4ff6-8928-4295b3253185" />

## 🛠️ Implementation & Technical Milestones

### 1. Advanced IP Design & Segmentation
*   **VLSM Subnetting:** Optimized the `192.168.0.0/22` private space down to tailored subnets matching exact host requirements to prevent IP waste.
*   **VLAN Design & Inter-VLAN Routing:** Enforced logical boundaries using IEEE 802.1Q encapsulation (VLAN 10, 20, 30, 40) executed via **Router-on-a-Stick (RoaS)**.

### 2. Infrastructure & Automated Services
*   **Centralized DHCP & Relay:** Configured central DHCP pools on the `State_HQ` router and mapped `ip helper-address` relays at remote boundaries for automated IP provisioning.
*   **Enterprise Application Services:** Implemented localized split-horizon DNS hosting and hosted responsive government portals over HTTP.

### 3. Edge Security & Traffic Translation (NAT/PAT)
*   **Static NAT:** Hardmapped internal services (`192.168.3.2` / `192.168.3.3`) to public IPs to hide enterprise topology while keeping servers accessible.
*   **PAT (Overload):** Constructed access control lists (ACLs) to bind local office and branch subnets to exterior interface addresses for secure internet egress.

### 4. Cryptographic Site-to-Site VPN (The Security Core)
*   **ISAKMP Policy (Phase 1):** Configured IKE Phase 1 using robust **AES-256 encryption**, **SHA hashing**, and Diffie-Hellman Group 2 pre-shared keys.
*   **IPSec Architecture (Phase 2):** Tied explicit crypto access-lists (`ACL 110`) to custom transform sets (`esp-aes esp-sha-hmac`) deployed via crypto maps to guarantee secure, encrypted transit over untrusted public links between SecOps and the NDC.

### 5. Static Routing Optimization
*   Engineered predictable multi-hop paths across 5 corporate and provider routers using explicit static routing tables matched with fallback gateway routing (`0.0.0.0/0`).

## 🧪 Verification & Proof of Concept
*   **Routing Table Stability:** Validated next-hop paths via `show ip route` across the WAN backbone.
*   **Security State:** Monitored active secure sessions with `show crypto isakmp sa` verifying `QM_IDLE` status.
*   **Data Continuity:** Successfully validated end-to-end multi-hop connectivity using `tracert` and explicit ICMP simulations within Packet Tracer.

## 📂 How to Run the Project
1. Download the `.pkt` file from this repository.
2. Open it using **Cisco Packet Tracer** (v8.0 or higher recommended).
3. Use the desktop browser on any local PC to navigate to `www.gov.agency` to test full connectivity and secure translation.# Secure-Enterprise-Network-IPSec-VPN
A secure multi-site network architecture with dynamic addressing, enterprise NAT, and cryptographic IPSec tunnels.
