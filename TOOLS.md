# TOOLS — What I Can Do

## File System Tools
| Tool | What It Does |
|------|-------------|
| `read_file` | Read any file on Abdullah's machine |
| `write_file` | Create or update files |
| `list_dir` | List directory contents |
| `search_files` | Search for files by name/content |

**Key Paths:**
- Workspace: `C:\Users\Admin\.openclaw\workspace`
- NetPulse Pro: `E:\Abdullah React project + experimantol projects\NetworkingTools NetPusle Pro`
- Downloads: `C:\Users\Admin\Downloads`
- Desktop: `C:\Users\Admin\Desktop`

---

## Shell / Terminal Tools
```powershell
# Run any PowerShell command
# ALWAYS ask before running destructive commands
# Safe commands: dir, type, git status, npm list
# Ask first: del, rm, format, git push, npm publish
```

---

## Web Tools
| Tool | Usage |
|------|-------|
| `web_search` | Search the internet (Brave Search) |
| `web_fetch` | Fetch full webpage content |

---

## Git Tools
```bash
git status          # Check project status — SAFE
git diff            # Show changes — SAFE  
git log --oneline   # Show history — SAFE
git add .           # Stage changes — SAFE
git commit -m ""    # Commit — SAFE
git push            # Push to remote — ASK FIRST
git pull            # Pull from remote — SAFE
```

---

## Node/NPM Tools
```bash
npm install         # Install packages — SAFE
npm run dev         # Start dev server — SAFE
npm run build       # Build project — SAFE
npm run test        # Run tests — SAFE
npm publish         # Publish package — ASK FIRST
```

---

## React Native Tools
```bash
npx react-native start          # Start Metro bundler
npx react-native run-android    # Build Android
npx react-native run-ios        # Build iOS (Mac only)
npx expo start                  # If using Expo
adb devices                     # Check connected Android devices
```

---

## Security Rules
1. ✅ Read files freely
2. ✅ Run dev servers freely
3. ✅ Search the web freely
4. ⚠️ Ask before writing to files outside workspace
5. ⚠️ Ask before git push
6. ❌ Never delete without confirmation
7. ❌ Never share API keys in responses
8. ❌ Never run as admin without reason

---

## Model Switching
```
# Best for reasoning /model github-copilot/gpt-4o
# Default /model ollama/qwen3.5:cloud
# Unlimited fallback /model ollama/glm-4.7-flash
# Fast backup
```

---
## OpenClaw CLI Quick Reference
OpenClaw is controlled via subcommands. Do not invent commands.
To manage the Gateway daemon service (start/stop/restart):
- openclaw gateway status
- openclaw gateway start
- openclaw gateway stop
- openclaw gateway restart
If unsure, ask the user to run `openclaw help` (or `openclaw gateway --help`) and paste the output.
