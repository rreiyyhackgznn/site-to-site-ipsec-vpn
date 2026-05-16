# Site-to-Site IPsec VPN

A site-to-site IPsec VPN simulation built in Cisco Packet Tracer, establishing
an encrypted tunnel between two corporate networks (MyCoHQ and TheirCo) over
a simulated ISP connection.

## Overview

This project simulates a real-world VPN deployment between two company
headquarters connected through an ISP. The tunnel uses AES-256 encryption
with ISAKMP/IKE phase negotiation, crypto maps, and ACL-based traffic
matching. EtherChannel is also configured on both sites for link aggregation.

## Technologies Used

- **VPN:** Site-to-Site IPsec VPN
- **Encryption:** AES-256 (ESP)
- **Authentication:** Pre-shared Key
- **Key Exchange:** ISAKMP / IKE (Group 2)
- **Traffic Matching:** Extended ACL
- **Link Aggregation:** EtherChannel (LACP, mode active)
- **Redundancy:** Floating static route (AD: 50)

## Network Topology

| Site | Network | Gateway |
|------|---------|---------|
| MyCoHQ | 10.6.48.0/24 | Fa0/1 — Serial1/1 |
| TheirCo | 10.196.31.0/24 | Fa0/1 — Serial1/3 |
| ISP Primary (MyCoHQ) | 103.24.99.0/30 | — |
| ISP Secondary (MyCoHQ) | 103.24.99.100/30 | — |
| ISP Primary (TheirCo) | 205.66.55.0/30 | — |
| ISP Secondary (TheirCo) | 205.66.55.100/30 | — |

## Key Configurations

- **ISAKMP Policy:** AES-256 encryption, pre-shared key, DH Group 2
- **Transform Set:** `esp-aes 256 esp-sha-hmac`, tunnel mode
- **Crypto Map:** Applied on external serial interfaces
- **ACL:** Permits traffic between 10.6.48.1 and 10.196.31.8
- **Floating Static Route:** Redundant ISP path with AD 50
- **EtherChannel:** Port-channel with LACP mode active, IP assigned

## Files

| File | Description |
|------|-------------|
| `IPsec-VPN-project.pkt` | Main Packet Tracer simulation file |

## How to Open

1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
2. Open the `.pkt` file
3. Use Simulation Mode to verify encrypted tunnel traffic between sites
