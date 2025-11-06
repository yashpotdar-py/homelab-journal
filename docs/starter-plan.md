# Starter Plan

## **Stage 1: Planning & Baseline**

**Goal:** Create structure, stability, and remote accessibility.

1. **Naming Convention**
   * Choose a theme
   * Assign static IPs or DHCP reservations for each device.
2. **Documentation Setup**
   * Use a markdown repo (GitHub or Obsidian) named `homelab-journal`.
   * Structure by: `/services`, `/experiments`, `/automation`, `/security`, `/notes`.
3. **Centralized Management**
   * Install **Tailscale** on all devices (zero-config secure VPN).
   * This enables you to SSH, SCP, or monitor from anywhere safely.

---

## **Stage 2: Core Services**

**Goal:** Make your lab self-sustaining.

| Purpose                 | Service                           | Device         | Notes                    |
| ----------------------- | --------------------------------- | -------------- | ------------------------ |
| DNS + Ad Blocking       | Pi-hole                           | Pi 3           | First essential service  |
| System Monitoring       | Netdata or Glances                | Pi 3           | Track system health      |
| Automation Orchestrator | n8n                               | Pi 4 / Laptop  | Manage all workflows     |
| Data Storage            | Simple NAS via Samba or Syncthing | Laptop or Pi 4 | Keep backups centralized |
| Web UI                  | Dashy / Homer Dashboard           | Pi 4           | Beautiful control panel  |

---

## **Stage 3: Automation Layer (n8n Base)**

**Goal:** Begin the “AI Assistant” foundation.

Start with practical automations:

* Monitor system uptime and send Telegram alerts.
* Auto-post system summaries (like temperatures, logs, or news digests).
* Trigger actions via voice or text (e.g., “Hey `<assistant>`, show me CPU usage” → n8n webhook → data retrieval).

Later expand to:

* Use Ollama local models for AI-driven responses (for now utilise the available online models).
* Integrate with Home Assistant.
* Build a web dashboard powered by n8n + Node-RED + AI logic.

---

## **Stage 4: Security Layer**

**Goal:** Learn & practice security fundamentals safely.

* Harden SSH (keys only, disable root login).
* Add UFW (firewall) rules.
* Run OpenVAS or Nessus for internal vulnerability scans.
* Set up Fail2Ban on SSH & web services.

---

## 🌱 Long-Term Vision

When I expand later:

* Add a dedicated NAS or low-power mini PC.
* Run Proxmox or Docker Swarm for VM/container orchestration.
* Build an internal AI cluster or a trained/fine-tuned local LLM.

---
