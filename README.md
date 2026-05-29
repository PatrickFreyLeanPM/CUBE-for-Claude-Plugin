# CUBE for Claude

Reference agents, skills, and data connectors for the [CUBE priorization method](https://patrickfreyleanpm.com/cube-landing/).

> **New here?** Start with [QUICKSTART.md](QUICKSTART.md) — install in 60 seconds. This README is the full reference.

Everything here is available **two ways from one source**: install it as a [Claude Cowork](https://claude.com/product/cowork) or [Claude Code](https://claude.com/product/claude-code) plugin. Same system prompt, same skills — you choose where it runs.

## Getting started in Cowork

- [Install Claude Desktop](https://claude.com/download)
- Get access to Claude Cowork
- Go to **Customize** -> **Personal Plugins** -> **Create Plugin** -> **Add Marketplace**
- Add marketplace `PatrickFreyLeanPM/CUBE-for-Claude-Plugin`
- After the marketplace has been added, go to **Directory** -> **Plugins** -> **Personal** and install the CUBE plugin

After this, you can use the CUBE skills and agents in Claude Cowork.

> [!IMPORTANT]
> **Every output from these plugins is a draft for product manager review.** 

What's in the repo:

- **[Named skills](#skills)** covering customer analysis, business analysis, effort estimation, ROI calculation and release planning.
- **[Named agents](#agents)** — end-to-end workflow agents (Customer Value Analyse, Business Value Analyst, Effort Estimator, ROI Calculator, Release Planenr) with job-style names and a single command to run each one.

## Agents

Each agent is named for the workflow it runs. They're the most common surface — start with the ones that match your work, then tune the underlying skill, the practice profile, and the connectors to how your team does it.

| Agent | What it does | Plugin | Command |
|---|---|---|---|
| **Customer Value Analyst** | Analyzes backlog items from a customer perspective using the Kano model framework, classifying features as Basic (must-have), Performance (linear impact), Delighter (unexpected positive), Unimportant (neutral), or Rejection (harmful) | `cube-prioritization` | `/cube-prioritization:customer-value-analyst` |
| **Business Value Analyst** | Analyzes backlog items from a business perspective using the CUBE methodology, categorizing items as New Business, Up Sell, Retainment, or Operational Efficiency and assigning Fibonacci-inspired numerical scores reflecting business impact | `cube-prioritization` | `/cube-prioritization:business-value-analyst` |
| **Effort Estimator** | Estimates development effort for backlog items using Story Points with Fibonacci-inspired scaling (0, 1, 2, 3, 5, 8, 13, 20, 40, 70, 100+), accounting for raw effort, technical complexity, and uncertainty | `cube-prioritization` | `/cube-prioritization:effort-estimator` |
| **ROI Calculator** | Calculates Return on Investment ratios for backlog items (Business Value ÷ Development Effort) and sorts them by ROI in descending order to guide efficient resource allocation and identify high-value, low-effort quick wins | `cube-prioritization` | `/cube-prioritization:roi-calculator` |
| **Release Planner** | Organizes ROI-prioritized backlog items into incremental releases (V1.0, V1.1, V2.0, etc.) based on team effort capacity and strategic constraints, transforming a prioritized backlog into a realistic, achievable roadmap that balances delivery velocity with technical coherence | `cube-prioritization` | `/cube-prioritization:release-planner` |
| **Full CUBE Analyst** | Orchestrates the complete CUBE workflow by executing all five specialized sub-agents in sequence, transforming raw backlog items into a fully analyzed, prioritized, and release-planned roadmap that integrates customer perspective, business value, development effort, ROI, and release planning | `cube-prioritization` | `/cube-prioritization:full-cube-analyst` |

## Repository Layout

```
cube-prioritization/      # skills and agents for the CUBE prioritization method
.claude-plugin/
  marketplace.json        # plugin registry
```

Each plugin directory has the same shape:

```
<plugin>/
  .claude-plugin/plugin.json
  CLAUDE.md               # template practice profile — filled in by /<plugin>:cold-start-interview
  README.md
  skills/                 # skills — each is a /<plugin>:<skill> slash command
  agents/                 # scheduled agents (if any)
  hooks/                  # pre- and post-tool hooks (if any)
```

## Getting Started

### Claude Cowork

In Cowork:

1. Open the **Cowork** tab.
2. Click **Customize** in the left sidebar.
3. Click **Browse plugins** and install the ones you want, **or** upload a custom plugin file (any plugin directory zipped up).

After install, skills fire automatically when relevant, slash commands are available via `/`, and the scheduled agents run on the cadence set in their frontmatter.

### Claude Code

```bash
# Add the marketplace (use the absolute path to this repo or a GitHub URL)
/plugin marketplace add https://github.com/PatrickFreyLeanPM/CUBE-for-Claude-Plugin

# Install a plugin — pick the ones that match your practice
/plugin install cube-prioritization
/plugin install cube-prioritization@cube-for-claude
```

[![Watch the demo](https://img.youtube.com/vi/pGOw8aDEb94/maxresdefault.jpg)](https://www.youtube.com/watch?v=pGOw8aDEb94)

## Contributing

Everything here is markdown and JSON. Fork, edit, PR.

- **New skill** → add it under `<plugin>/skills/<skill-name>/SKILL.md` with the frontmatter the existing skills use (`name`, `description`, `argument-hint`). Keep the description under 1024 characters — it's the trigger signal. The skill is invokable as `/<plugin>:<skill-name>`. Mark pure-reference skills `user-invocable: false`.
- **New agent** → add `<plugin>/agents/<name>.md` with scheduling frontmatter and the system prompt. Add a matching `managed-agent-cookbooks/<name>/` if you want headless deployment.

## License

Licensed under the [Apache License, Version 2.0](LICENSE).

Copyright 2026 Patrick Frey