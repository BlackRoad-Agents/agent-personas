<!-- BlackRoad SEO Enhanced -->

# agent personas

> Part of **[BlackRoad OS](https://blackroad.io)** — Sovereign Computing for Everyone

[![BlackRoad OS](https://img.shields.io/badge/BlackRoad-OS-ff1d6c?style=for-the-badge)](https://blackroad.io)
[![BlackRoad Agents](https://img.shields.io/badge/Org-BlackRoad-Agents-2979ff?style=for-the-badge)](https://github.com/BlackRoad-Agents)
[![License](https://img.shields.io/badge/License-Proprietary-f5a623?style=for-the-badge)](LICENSE)

**agent personas** is part of the **BlackRoad OS** ecosystem — a sovereign, distributed operating system built on edge computing, local AI, and mesh networking by **BlackRoad OS, Inc.**

## About BlackRoad OS

BlackRoad OS is a sovereign computing platform that runs AI locally on your own hardware. No cloud dependencies. No API keys. No surveillance. Built by [BlackRoad OS, Inc.](https://github.com/BlackRoad-OS-Inc), a Delaware C-Corp founded in 2025.

### Key Features
- **Local AI** — Run LLMs on Raspberry Pi, Hailo-8, and commodity hardware
- **Mesh Networking** — WireGuard VPN, NATS pub/sub, peer-to-peer communication
- **Edge Computing** — 52 TOPS of AI acceleration across a Pi fleet
- **Self-Hosted Everything** — Git, DNS, storage, CI/CD, chat — all sovereign
- **Zero Cloud Dependencies** — Your data stays on your hardware

### The BlackRoad Ecosystem
| Organization | Focus |
|---|---|
| [BlackRoad OS](https://github.com/BlackRoad-OS) | Core platform and applications |
| [BlackRoad OS, Inc.](https://github.com/BlackRoad-OS-Inc) | Corporate and enterprise |
| [BlackRoad AI](https://github.com/BlackRoad-AI) | Artificial intelligence and ML |
| [BlackRoad Hardware](https://github.com/BlackRoad-Hardware) | Edge hardware and IoT |
| [BlackRoad Security](https://github.com/BlackRoad-Security) | Cybersecurity and auditing |
| [BlackRoad Quantum](https://github.com/BlackRoad-Quantum) | Quantum computing research |
| [BlackRoad Agents](https://github.com/BlackRoad-Agents) | Autonomous AI agents |
| [BlackRoad Network](https://github.com/BlackRoad-Network) | Mesh and distributed networking |
| [BlackRoad Education](https://github.com/BlackRoad-Education) | Learning and tutoring platforms |
| [BlackRoad Labs](https://github.com/BlackRoad-Labs) | Research and experiments |
| [BlackRoad Cloud](https://github.com/BlackRoad-Cloud) | Self-hosted cloud infrastructure |
| [BlackRoad Forge](https://github.com/BlackRoad-Forge) | Developer tools and utilities |

### Links
- **Website**: [blackroad.io](https://blackroad.io)
- **Documentation**: [docs.blackroad.io](https://docs.blackroad.io)
- **Chat**: [chat.blackroad.io](https://chat.blackroad.io)
- **Search**: [search.blackroad.io](https://search.blackroad.io)

---


Core agent persona definitions for BlackRoad OS. Contains the identity, system prompts, and configuration for all 12 agents in the fleet.

## What This Is

A structured JSON registry of every agent persona in the BlackRoad OS system. Each persona defines the agent's name, role, personality, assigned model, and system prompt text used when invoking the agent through Ollama or any LLM backend.

## Personas

| ID | Name | Role | Group |
|----|------|------|-------|
| road | Road | Fleet Commander | core |
| coder | Coder | Software Engineer | core |
| scholar | Scholar | Researcher and Analyst | core |
| alice | Alice | Gateway and Network Ops | fleet |
| cecilia | Cecilia | AI Inference and Storage | fleet |
| octavia | Octavia | DevOps and Git Ops | fleet |
| lucidia | Lucidia | Web Hosting and CI/CD | fleet |
| aria | Aria | Monitoring and Orchestration | fleet |
| pascal | Pascal | Mathematics and Logic | specialist |
| writer | Writer | Content Creation | specialist |
| tutor | Tutor | Education and Onboarding | specialist |
| cipher | Cipher | Security and Cryptography | specialist |

## Usage

```python
import json

with open("personas.json") as f:
    data = json.load(f)

# Get a specific persona
road = next(p for p in data["personas"] if p["id"] == "road")
print(road["persona"])  # System prompt text

# List all fleet agents
fleet = [p for p in data["personas"] if p["group"] == "fleet"]
```

```bash
# Use with Ollama
PERSONA=$(jq -r '.personas[] | select(.id=="coder") | .persona' personas.json)
ollama run codellama --system "$PERSONA" "Write a Python HTTP server"
```

## Structure

Each persona object contains:

- `id` — Unique identifier used for routing and dispatch
- `name` — Display name
- `emoji` — Associated emoji keyword (for terminal/UI display)
- `color` — Brand hex color
- `role` — One-line role description
- `group` — Category: core, fleet, or specialist
- `model` — Default Ollama model
- `persona` — Full system prompt text

Part of BlackRoad-Agents. Remember the Road. Pave Tomorrow. Incorporated 2025.
