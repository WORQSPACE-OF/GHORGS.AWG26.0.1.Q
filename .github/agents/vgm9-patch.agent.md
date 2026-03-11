---
description: 'vgm9-patch.agent — WSL development on VGM9 repos (qhoami, qopilot, session-tools, appdata-rag). Branch, build, test, PR. Never edit /mnt/c/ or compiled extension output.'
tools: [execute/runInTerminal, read/readFile, read/terminalLastCommand, read/problems, search/codebase, search/fileSearch, search/listDirectory, search/textSearch, edit/createFile, edit/editFiles]
---

# vgm9-patch.agent — VGM9 WSL Contributor

**Scope**: WSL clones only. Never touch `/mnt/c/` or installed extension output.

---

## VGM9 WSL clones

| Repo | Clone path |
|------|-----------|
| qhoami | `/home/victorb/code/vgm9/qhoami/` |
| qopilot | `/home/victorb/code/vgm9/qopilot/` |
| session-tools | `/home/victorb/code/vgm9/session-tools/` |
| appdata-rag | `/home/victorb/code/vgm9/appdata-rag/` |

---

## Branch naming convention

```
wsl/Ubuntu-20.04/<feature>
e.g. wsl/Ubuntu-20.04/fix-appdata-path-wsl-blindspot
```

## Build chains

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

### session-tools WSL fix (`VGM9/session-tools#2`)
```typescript
// In appdata-path package, before platform branch:
if (process.env.WSL_DISTRO_NAME) {
  const user = process.env.USER || 'victorb';
  return path.join('/mnt/c/Users', user, 'AppData', 'Roaming');
}
```

---

## PR workflow

```bash
cd /home/victorb/code/vgm9/<repo>
git checkout -b wsl/Ubuntu-20.04/<feature>
# ... make changes ...
git push origin wsl/Ubuntu-20.04/<feature>
gh pr create --repo VGM9/<repo> \
  --title "<title>" \
  --body-file /tmp/pr-body.md \
  --base main
```

---

## Hard rules

- NEVER edit `/mnt/c/Users/victorb/.vscode-server-insiders/extensions/` — that is compiled output, not source
- NEVER edit any file under `/mnt/c/` directly (Windows filesystem — breaks line endings, permissions)
- Only modify source in `/home/victorb/code/vgm9/<repo>/`
- After any install: extension requires window reload to activate (NOT the usual hot-swap — this is an install)
