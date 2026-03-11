# WORQSPACE.md — Topology & Toolchain

## Workspace Identity

| Field | Value |
|-------|-------|
| Workspace file | `GHORGS.AWG26.code-workspace` |
| WORQSPACE-OF registration | `WORQSPACE-OF/GHORGS.AWG26.0.1.Q` |
| Squad | GHORGS (GitHub Organization Registry & Governance System) |
| Epoch | AWG26 (agent workspace generation 26) |
| Role | `0.1.Q` — Psychopomp / AWG26 Triadic Hinge |
| GitHub identity | `DarienSirius` |

## Workspace Folders

```
/home/victorb/ottosoft/departments/OrgManagement/squads/GHORGS/   ← GHORGS HUSK (AWG26 primary)
/home/victorb/.AWG25/.AO/GHORGS/                                   ← Chiron workspace (AWG25)
/home/victorb/.AWG25/.AO/GHORGS/_/                                 ← Aether workspace (AWG25)
```

## Platform: WSL Ubuntu-20.04

This workspace instance runs on **WSL2 (Ubuntu-20.04)** with VS Code Server (Insiders).

Key paths:
- Agent nucleus: `.github/` under HUSK root
- WSL VGM9 clones: `/home/victorb/code/vgm9/` (qhoami, qopilot, session-tools, appdata-rag)
- AppData (Windows-side, mounted): `/mnt/c/Users/victorb/AppData/Roaming/`
- Session JSONL files: `/mnt/c/Users/victorb/AppData/Roaming/Code - Insiders/User/workspaceStorage/`

## Architecture Layers

| Layer | Tooling | Purpose |
|-------|---------|---------|
| Coordinator (Q) | VS Code Copilot, runSubagent | Orchestrate, verify, synthesize |
| GitHub plane | `gh` CLI (DarienSirius) | Issues, PRs, repos, org graph |
| Session census | count-all-sessions.py, sessions.db | Who/what/when across reboots |
| VGM9 devops | WSL clones, build chains | Upstream contributions, patches |
| Security | security-scan.py | PAT leakage detection |

## WORQSPACE-OF Namespace Pattern

The `WORQSPACE-OF` GitHub org registers workspace *topologies*:

```
WORQSPACE-OF/<cluster>.<epoch>.<role>
```

- **PLEROMA** — class definitions (workspace topology templates)
- **POLARIS** — instance registrations (specific running configurations)
- **GHORGS.AWG26.0.1.Q** — this workspace (specific to AWG26/Q-role)

## Platform Variants

The same `.github/` scaffold can operate across platforms. Platform-specific data:

| Platform | Extension host | AppData path | WSL_DISTRO_NAME |
|----------|--------------|-------------|-----------------|
| WSL Ubuntu-20.04 | `~/.vscode-server-insiders/` | `/mnt/c/Users/.../AppData/` | set |
| Windows native | `%USERPROFILE%/.vscode-insiders/` | `%APPDATA%/` | not set |
| macOS | `~/.vscode-insiders/` | `~/Library/Application Support/` | not set |

When porting, update only `platform/PLATFORM.md` — not the `.github/` scaffold.
