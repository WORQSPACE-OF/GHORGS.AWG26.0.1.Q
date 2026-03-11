# PLATFORM.md — WSL Ubuntu-20.04

> This file is platform-specific. It describes the current running instance of this workspace.
> If you're opening this workspace on a different platform, create a new `PLATFORM.md` for that context.

## Instance

- **Platform**: WSL2
- **Distro**: Ubuntu-20.04 (`WSL_DISTRO_NAME=Ubuntu-20.04`)
- **VS Code flavor**: Code - Insiders (Remote WSL extension)
- **User**: victorb

## Critical Paths

| Purpose | Path |
|---------|------|
| Workspace root | `/home/victorb/ottosoft/departments/OrgManagement/squads/GHORGS/` |
| VS Code extension host | `~/.vscode-server-insiders/extensions/` |
| Session JSONL storage | `/mnt/c/Users/victorb/AppData/Roaming/Code - Insiders/User/workspaceStorage/` |
| VGM9 WSL clones | `/home/victorb/code/vgm9/` |
| This agent nucleus | `./_/AS/0.1.Q/_/` under workspace root |

## Known WSL Issues

### AppData blindspot in `@vscode-agents/appdata-path`

The package uses `os.platform() === 'linux'` → routes to `~/.config/` — but in WSL,
sessions are on the Windows C: drive.

**Workaround:**
```bash
APPDATA=/mnt/c/Users/victorb/AppData/Roaming <command>
```

**Upstream fix**: `VGM9/session-tools#2` — check `process.env.WSL_DISTRO_NAME` before platform branch.

## Build Chains

### qhoami
```bash
cd /home/victorb/code/vgm9/qhoami
npm install
npm run build
vsce package --no-dependencies
code-insiders --install-extension vgm9.qhoami-*.vsix --force
```

### qopilot
```bash
cd /home/victorb/code/vgm9/qopilot
npm install
npm run build
vsce package --no-dependencies
code-insiders --install-extension vgm9.qopilot-*.vsix --force
```

## Session Census (last run: 2026-03-11)

- Total: 598 files, 286 qualifying, 946 reboots, 121,496 tool calls
- This session (`33988ac6`): 68+ reboots, 70+ requests — top 2 most rebooted
- Run census: `npm run census` from workspace nucleus
