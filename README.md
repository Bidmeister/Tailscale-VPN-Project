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
<img width="1178" height="441" alt="image" src="https://github.com/user-attachments/assets/65a27c27-79f7-4b1f-bfd4-66bb1f3e8ae0" />

<img width="901" height="643" alt="image" src="https://github.com/user-attachments/assets/b99788f1-2c81-45b5-ae1c-ac5f3a927dd4" />

<img width="772" height="610" alt="image" src="https://github.com/user-attachments/assets/7daff56a-acd9-4074-80d2-c79596f3ff82" />

<img width="671" height="450" alt="image" src="https://github.com/user-attachments/assets/96654ad8-7cd7-4701-affa-fb3e29ad7a24" />

<img width="1000" height="953" alt="image" src="https://github.com/user-attachments/assets/8fcb09a2-dc1f-4dc1-a316-c55249731b87" />




## What I Learned
This lab deepened my understanding of modern VPNs, NAT traversal, and zero‑trust networking. It reflects real-world scenarios such as remote access, secure tunneling, and identity‑based access control used in enterprise environments.
