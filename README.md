<p align="center">
  <img
    src="https://raw.githubusercontent.com/AgentMindCloud/grok-install-brand/main/plates/plate_09_grok-install-brand.png"
    alt="grok-install-ecosystem — the GrokInstall family in one view"
    width="100%"
  >
</p>

# GrokInstall Ecosystem

**One YAML file. One command. Your Grok agent is live on X.**

The GrokInstall ecosystem is the open standard for installable, safety-scanned, Grok-native agents on X — plus the tooling, templates, documentation, and marketplace that makes the standard real. Twelve repos, Apache 2.0, built in public.

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-a13d24?style=for-the-badge&labelColor=ede3cf)](LICENSE)
[![Ecosystem](https://img.shields.io/badge/Repos-12-a13d24?style=for-the-badge&labelColor=ede3cf)](#the-twelve-repos)
[![Live](https://img.shields.io/badge/Marketplace-grokagents.dev-a13d24?style=for-the-badge&labelColor=ede3cf)](https://grokagents.dev)
[![Built for Grok on X](https://img.shields.io/badge/Built%20for-Grok%20on%20X-a13d24?style=for-the-badge&labelColor=ede3cf)](https://x.com/JanSol0s)

---

## Start here

If you're new to the ecosystem, pick the entry point that matches what you want to do:

| You want to... | Start with |
|---|---|
| Install a Grok agent in one command | [grok-install-cli](https://github.com/AgentMindCloud/grok-install-cli) |
| Understand the YAML spec | [grok-install](https://github.com/AgentMindCloud/grok-install) |
| Browse ready-made agents | [awesome-grok-agents](https://github.com/AgentMindCloud/awesome-grok-agents) or [grokagents.dev](https://grokagents.dev) |
| Read the full documentation | [grok-docs](https://github.com/AgentMindCloud/grok-docs) · [live site](https://agentmindcloud.github.io/grok-docs/) |
| Ship a Grok 4.20 codebase safely to X | [grok-build-bridge](https://github.com/AgentMindCloud/grok-build-bridge) |
| Write agents in VS Code with full IntelliSense | [vscode-grok-yaml](https://github.com/AgentMindCloud/vscode-grok-yaml) |
| Auto-validate agents in CI | [grok-install-action](https://github.com/AgentMindCloud/grok-install-action) |

---

## The twelve repos

| # | Repo | Role |
|---|---|---|
| 01 | [grok-install](https://github.com/AgentMindCloud/grok-install) | The open standard — one YAML file, one command, your agent is live on X |
| 02 | [grok-yaml-standards](https://github.com/AgentMindCloud/grok-yaml-standards) | Twelve magic YAML standards extending grok-install.yaml |
| 03 | [grok-docs](https://github.com/AgentMindCloud/grok-docs) | Official documentation site (MkDocs Material) |
| 04 | [grok-install-cli](https://github.com/AgentMindCloud/grok-install-cli) | Official Python CLI and runtime — `pip install grok-install` |
| 05 | [grok-install-action](https://github.com/AgentMindCloud/grok-install-action) | GitHub Action: auto-validate, safety-scan, certify on every push |
| 06 | [vscode-grok-yaml](https://github.com/AgentMindCloud/vscode-grok-yaml) | VS Code extension: IntelliSense, validation, safety scanning |
| 07 | [awesome-grok-agents](https://github.com/AgentMindCloud/awesome-grok-agents) | Ten production-ready agent templates, all certified |
| 08 | [grok-agents-marketplace](https://github.com/AgentMindCloud/grok-agents-marketplace) | Community marketplace — [grokagents.dev](https://grokagents.dev) |
| 09 | [grok-install-brand](https://github.com/AgentMindCloud/grok-install-brand) | Brand HQ: plates, banners, icons, README template |
| 10 | [x-platform-toolkit](https://github.com/AgentMindCloud/x-platform-toolkit) | Twenty open-source X tools filling platform gaps |
| 11 | [grok-build-bridge](https://github.com/AgentMindCloud/grok-build-bridge) | Grok 4.20 codebase → production-ready X agent, safely |
| 12 | [grok-agent-orchestra](https://github.com/AgentMindCloud/grok-agent-orchestra) | Multi-agent orchestration with the Lucas safety veto |

---

## How the pieces fit

```
                        grok-install
                    (the YAML standard)
                            │
              ┌─────────────┼─────────────┐
              │             │             │
    grok-yaml-standards  grok-docs   grok-install-cli
    (12 extensions)    (docs site)    (Python runtime)
                                          │
                    ┌─────────────────────┼─────────────────────┐
                    │                     │                     │
          vscode-grok-yaml      grok-install-action    awesome-grok-agents
          (IDE extension)       (CI validation)       (template gallery)
                                          │
                                          ▼
                            grok-agents-marketplace
                               (grokagents.dev)
                                          │
                    ┌─────────────────────┴─────────────────────┐
                    │                                           │
            grok-build-bridge                          grok-agent-orchestra
          (Grok code → X, safely)                      (multi-agent + Lucas)

                            x-platform-toolkit
                         (20 open X tools, sibling)

                            grok-install-brand
                         (visual identity HQ)
```

---

## Quick start (60 seconds)

```bash
pip install grok-install
grok-install init my-first-agent
cd my-first-agent
grok-install run
```

That's it. Three commands from nothing to a live Grok agent on X. No Docker, no config files, no guesswork. Full walkthrough in [grok-docs](https://agentmindcloud.github.io/grok-docs/).

---

## The standard

Every agent is a single YAML file:

```yaml
version: "2.13"
name: "My Reply Bot"
description: "Replies to X mentions using Grok"

llm:
  provider: "xai"
  model: "grok-4"
  api_key_env: "GROK_API_KEY"

tools:
  - name: "reply_to_mention"
    parameters:
      type: "object"
      properties:
        mention_id: {type: "string"}
        reply_text: {type: "string", maxLength: 280}

rate_limits:
  reply_to_mention:
    qps: 0.5
    daily_cap: 200

cost_limits:
  daily_usd: 3.00
  on_limit: "block"

safety:
  pre_install_scan: true
  minimum_keys_only: true
```

The CLI does the rest: parse → validate → scan → run → deploy. The full spec lives in [grok-install](https://github.com/AgentMindCloud/grok-install).

---

## Principles

- **Open standard, Apache 2.0 everywhere.** xAI can adopt, fork, or replace any piece at any time.
- **Safety by default.** Pre-install scan on every agent. Human-in-the-loop approval for every write tool. Rate limits and cost limits declarative, not optional.
- **Grok-native.** Built on the official [xai-sdk](https://github.com/xai-org/xai-sdk), not a wrapper.
- **xAI-first, not provider-agnostic.** The ecosystem exists to make more people ship more Grok 4.20 agents, safely. Not another LangChain.
- **Build in public.** Every decision, every bug, every PR — visible.

---

## Contribute

Every repo takes contributions. The quickest wins:

- **Ship a new template** → [awesome-grok-agents](https://github.com/AgentMindCloud/awesome-grok-agents) ([CONTRIBUTING.md](https://github.com/AgentMindCloud/awesome-grok-agents/blob/main/CONTRIBUTING.md))
- **Propose a spec change** → [grok-install](https://github.com/AgentMindCloud/grok-install) RFCs ([CONTRIBUTING.md](https://github.com/AgentMindCloud/grok-install/blob/main/CONTRIBUTING.md))
- **File a bug** → the repo where you found it
- **Star the repos you use** → genuinely moves the needle for this kind of ecosystem

---

## Who builds this

Built by [@JanSol0s](https://x.com/JanSol0s) and the open-source community. Follow along on X for build-in-public updates, new templates, and spec changes.

---

## Disclaimer

GrokInstall is an independent community project. Not affiliated with xAI, Grok, or X.

## License

Apache 2.0 — see [LICENSE](LICENSE). Patent grant included.
