# agent-personas

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
