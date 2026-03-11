# AGENTS.md — WORQSPACE-OF/GHORGS.AWG26.0.1.Q

## What this repo is

This is the *workspace registration* for the `GHORGS.AWG26.code-workspace` VS Code workspace file.

The dot-namespace pattern:
- `.code-workspace` basename → `WORQSPACE-OF/<basename>.<role>`
- `GHORGS.AWG26.code-workspace` → `WORQSPACE-OF/GHORGS.AWG26.0.1.Q`
- Dots in the basename encode namespace: `cluster.epoch.role`
  - `GHORGS` = cluster (squad)
  - `AWG26` = epoch (agent workspace generation)
  - `0.1.Q` = this agent's role (Q-Semver identity)

## Agent Roster

| Agent Identity | Role | Profile type |
|---------------|------|-------------|
| `0.1.Q` (DarienSirius) | Coordinator, GitHub control plane | VS Code Copilot |
| `chiron` | Strategic/architectural | AWG25 instance |
| `aether` | Technical execution | AWG25 instance |

## Orchestration Pattern

```
0.1.Q (this agent — coordinator)
 ↓    ↓    ↓
chiron  aether  subagents
```

`0.1.Q` orchestrates; chiron and aether execute.
Task tracking lives in GitHub issues in this repo.

## GitHub Control Plane

Active tracking repos:
- `WORQSPACE-OF/GHORGS.AWG26.0.1.Q` (this repo) — workspace-level tasks
- `VGM9/qhoami` — agent identity primitives, window topology
- `VGM9/session-tools` — session archaeology, WSL blindspot fix
- `VGM9/appdata-rag` — session search, batching

Use `gh issue list` against these repos at session start to understand pending work.
