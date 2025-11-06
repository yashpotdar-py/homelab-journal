# Soulsborne Network & Naming Standard

> *“Ashes seeketh embers. Systems seeketh order.”*  

---

## Overview

This document will define the naming convention, IP structure, and remote access setup for the Soulsborne-themed Home Lab.  
Each device name reflects its role in the network — symbolic, memorable, and narratively tied to its function.  

---

## Naming Theme: Soulsborne

| Device | Role | Hostname | Rationale | Namespace |
|--------|------|-----------|------------|------------|
| **Router** | DHCP / Firewall / Gateway | `sulyvahn` | The Pontiff controls all network paths and inspects all traffic. | `sulyvahn.lab` |
| **Main Laptop** | Control / Work Node | `maliketh` | The Shadow of Death — my enforcer and main executor of commands. | `maliketh.lab` |
| **Raspberry Pi 4** | Automation / AI Node | `seluvis` | The puppet-master orchestrating automations and n8n workflows. | `seluvis.lab` |
| **Raspberry Pi 3** | Utility / DNS Node | `enia` | The oracle interpreting “the Two Fingers” — the perfect DNS/lookup node. | `enia.lab` |
| **Phone** | Remote Monitoring / SSH | `ranni` | The ethereal, remote shell — extending my will from afar. | `ranni.tailscale.net` |

> **Note:** The `.lab` suffix is for local identification (Pi-hole / AdGuardHome DNS zone).  
> The `.tailscale.net` domain handles secure global connectivity.

---

## Network & Address Plan

| Hostname | Local IP | Tailscale Address | Role | Notes |
|-----------|-----------|------------------|------|-------|
| `sulyvahn.lab` | 192.168.1.1 | — | Router / DHCP / Firewall | Gateway for all local traffic |
| `maliketh.lab` | 192.168.1.10 | `maliketh.tailscale.net` | Control node | SSH + code execution hub |
| `seluvis.lab` | 192.168.1.20 | `seluvis.tailscale.net` | AI / Automation node | Runs n8n, automation tools |
| `enia.lab` | 192.168.1.30 | `enia.tailscale.net` | DNS / Utility node | Pi-hole, monitoring, backups |
| `ranni.tailscale.net` | Dynamic | `ranni.tailscale.net` | Remote terminal | Used for mobile SSH control |

> 💡 **Tip:** Reserve each `.lab` IP via my router’s DHCP reservation table.  
> This ensures consistent local naming and prevents conflicts.

---

## Namespace Logic

```plaintext
[hostname].[domain]
└── [domain] = .lab (local) or .tailscale.net (remote)
```

- `.lab` → Internal access (LAN or VPN)
- `.tailscale.net` → Global access via encrypted mesh network

Example access commands:

```bash
# Local
ssh yash@seluvis.lab
ping enia.lab

# Remote (via Tailscale)
ssh yash@maliketh.tailscale.net
```

---

## Remote Access Layer — Tailscale

**Goal:** Securely connect to every node without exposing ports.

### Installation

```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

### Verification

```bash
tailscale status
ping seluvis.tailscale.net
```

> Each connected device will appear on the [Tailscale Admin Console](https://login.tailscale.com/admin/machines).

---
