Secure Mesh Networking with Tailscale (WireGuard VPN)

## Overview
This project demonstrates how I used Tailscale (a WireGuard‑based mesh VPN) to securely connect two isolated VMs across separate NAT networks. I tested peer‑to‑peer connectivity, enabled MagicDNS, configured remote desktop access, implemented zero‑trust ACLs, and set up an exit node.

## Network Architecture
- **Ubuntu VM** — remote host  
- **Kali VM** — client machine  
- **Tailscale Tailnet** — secure overlay network connecting both VMs


## Tools Used
- Tailscale  
- WireGuard  
- Ubuntu Linux  
- Kali Linux  
- Remmina (RDP client)  

## Skills Demonstrated
- VPN configuration and authentication  
- NAT traversal analysis (STUN, hole‑punching, DERP relays)  
- Zero‑trust access control using ACLs  
- Remote desktop configuration  
- Identity‑based networking  
- Secure routing and exit node setup  

## Methodology

### 1. Tailnet Setup
- Created a Tailscale account using identity provider authentication.  
- Installed Tailscale on both Ubuntu and Kali.  
- Authenticated both devices into the same Tailnet.  
- Verified connectivity in the Tailscale Admin Console.

### 2. Connectivity Testing
- Retrieved Tailscale IPs using `tailscale ip -4`.  
- Successfully pinged Ubuntu from Kali using both IP and MagicDNS hostname.  
- Confirmed encrypted peer‑to‑peer tunnel establishment.

### 3. Remote Desktop Access
- Installed and enabled XRDP on Ubuntu.  
- Connected from Kali using Remmina over the Tailscale network.  
- Demonstrated full remote desktop control across NAT boundaries.

### 4. Zero‑Trust ACL Implementation
- Modified Tailnet ACLs to restrict traffic to **port 3389 only**.  
- Verified that ping was blocked while RDP remained functional.  
- Demonstrated micro‑segmentation and least‑privilege access.

### 5. Exit Node Configuration
- Enabled IP forwarding on Ubuntu.  
- Advertised Ubuntu as an exit node.  
- Activated exit node routing from Kali.  
- Verified public IP change using ifconfig.me.

## Key Findings
- Tailscale uses STUN and NAT hole‑punching to establish direct connections.  
- DERP relays are used only when NAT traversal fails.  
- MagicDNS simplifies host discovery without manual IP management.  
- ACLs enforce identity‑based zero‑trust policies.  
- Exit nodes allow secure internet routing through trusted devices.

## Screenshots
<img width="1210" height="465" alt="image" src="https://github.com/user-attachments/assets/81ffdd7a-6bf6-4f6c-b79c-a4568043509e" />


## What I Learned
This lab deepened my understanding of modern VPNs, NAT traversal, and zero‑trust networking. It reflects real-world scenarios such as remote access, secure tunneling, and identity‑based access control used in enterprise environments.
