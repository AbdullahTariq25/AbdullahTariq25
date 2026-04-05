# OpenClaw & Ollama Configuration Backup
**Date:** April 4, 2026 | **Time:** 7:44 PM (Asia/Karachi)
**System:** Windows 10.0.22631 (x64) | **Node:** v24.13.0

---

## 🔴 CRITICAL ISSUE IDENTIFIED

### Problem: Model Access Restrictions
Both Ollama models are failing with "model not allowed" error:
- `openai-codex/glm-5` → **ERROR: GatewayRequestError: model not allowed**
- `openai-codex/qwen3.5:cloud` → **ERROR: GatewayRequestError: model not allowed**

### Root Cause Analysis
1. **Models are registered in config** (openclaw.json)
2. **Ollama has only qwen3.5:cloud installed** (glm-5 missing!)
3. **Gateway is blocking them** with "model not allowed" despite valid config
4. **Issue timeline:** These worked previously, now broken after recent changes

---

## 📋 Current System State

### OpenClaw Version
- **Current:** 2026.3.13
- **Update Available:** 2026.4.2 (npm)
- **Status:** Scheduled Task Running

### Active Sessions
1. `agent:main:main` → claude-haiku-4.5 (12k/128k tokens)
2. `agent:main:whatsapp:direct:+923114836720` → gpt-4o (7.6k/64k tokens)

### Installed Plugins
- ✅ openclaw-web-search (@ollama/openclaw-web-search) — unpinned
- ✅ whatsapp gateway

### Gateway Configuration
- **Bind:** loopback (127.0.0.1:18789)
- **Mode:** local
- **Auth:** Token-based (23fa4c8cdf23370f09ee96ace554a6983159b8d42469f394)
- **Tailscale:** OFF

---

## 🔧 Model Configuration (openclaw.json)

### Ollama Provider
```json
{
  "baseUrl": "http://127.0.0.1:11434",
  "apiKey": "ollama-local",
  "api": "ollama",
  "models": [
    {
      "id": "qwen3.5:cloud",
      "name": "qwen3.5:cloud",
      "reasoning": true,
      "input": ["text", "image"],
      "contextWindow": 262144,
      "cost": { "input": 0, "output": 0 }
    },
    {
      "id": "glm-5",
      "name": "glm-5",
      "reasoning": false,
      "input": ["text"],
      "contextWindow": 128000,
      "cost": { "input": 0, "output": 0 }
    }
  ]
}
```

### Google Generative AI Provider
```json
{
  "baseUrl": "https://generativelanguage.googleapis.com/v1beta",
  "apiKey": "AIzaSyBmjwG3ob5dFrpYL3mfmMjp9zFFkAJ3tuA",
  "models": [
    "gemini-2.5-flash",
    "gemini-3-flash",
    "gemini-3.1-flash-lite",
    "gemini-2.5-flash-lite",
    "gemma-3-12b"
  ]
}
```

### GitHub Copilot Provider (Primary)
```json
{
  "models": [
    "github-copilot/gpt-4o",
    "github-copilot/gpt-5",
    "github-copilot/gpt-5.4",
    "github-copilot/claude-opus-4.5",
    "github-copilot/claude-sonnet-4.5",
    // ... 30+ more models
  ]
}
```

### Model Fallback Chain
1. `github-copilot/gpt-4o` (PRIMARY)
2. `google/gemini-2.5-flash`
3. `google/gemini-3.1-flash-lite`
4. `ollama/qwen3.5:cloud` ⚠️ FAILING
5. `ollama/glm-5` ⚠️ MISSING
6. `github-copilot/claude-opus-4.5`

---

## 🔴 Ollama Status

### Installed Models
```
qwen3.5:cloud (a7bf6f7891c3)
  - Size: Not available (cloud-only)
  - Modified: 2 hours ago
  - Remote: qwen3.5:397b @ ollama.com:443
```

### Missing Models
- ❌ `glm-5` — NOT INSTALLED (but referenced in config)

### Ollama Location
- **Local AppData:** C:\Users\Admin\AppData\Local\Ollama
- **Database:** db.sqlite (SQLite format 3)
- **Logs:** app.log, server.log

---

## ⚠️ Security Warnings (from openclaw audit)

1. **Reverse proxy headers not trusted** → No critical risk (local-only)
2. **Gateway.nodes.denyCommands ineffective** → Only affects shell commands
3. **Models below recommended tiers** → gpt-4o is fast but not GPT-5 family
4. **Unpinned plugin specs** → openclaw-web-search (@ollama/openclaw-web-search)
5. **Missing integrity metadata** → Plugin needs reinstall

---

## 📝 Full openclaw.json (Complete)

```json
{
  "meta": {
    "lastTouchedVersion": "2026.3.13",
    "lastTouchedAt": "2026-04-04T14:43:21.965Z"
  },
  "wizard": {
    "lastRunAt": "2026-04-04T14:43:21.853Z",
    "lastRunVersion": "2026.3.13",
    "lastRunCommand": "onboard",
    "lastRunMode": "local"
  },
  "auth": {
    "profiles": {
      "github-copilot:github": {
        "provider": "github-copilot",
        "mode": "token"
      },
      "openai-codex:default": {
        "provider": "openai-codex",
        "mode": "oauth"
      }
    }
  },
  "models": {
    "providers": {
      "ollama": {
        "baseUrl": "http://127.0.0.1:11434",
        "apiKey": "ollama-local",
        "api": "ollama",
        "models": [
          {
            "id": "qwen3.5:cloud",
            "name": "qwen3.5:cloud",
            "reasoning": true,
            "input": ["text", "image"],
            "cost": {"input": 0, "output": 0, "cacheRead": 0, "cacheWrite": 0},
            "contextWindow": 262144
          },
          {
            "id": "glm-5",
            "name": "glm-5",
            "reasoning": false,
            "input": ["text"],
            "cost": {"input": 0, "output": 0, "cacheRead": 0, "cacheWrite": 0},
            "contextWindow": 128000
          }
        ]
      },
      "google": {
        "baseUrl": "https://generativelanguage.googleapis.com/v1beta",
        "apiKey": "AIzaSyBmjwG3ob5dFrpYL3mfmMjp9zFFkAJ3tuA",
        "api": "google-generative-ai",
        "models": [
          {"id": "gemini-2.5-flash", "name": "Gemini 2.5 Flash", "contextWindow": 1048576},
          {"id": "gemini-3-flash", "name": "Gemini 3 Flash", "contextWindow": 256000},
          {"id": "gemini-3.1-flash-lite", "name": "Gemini 3.1 Flash Lite", "contextWindow": 256000},
          {"id": "gemini-2.5-flash-lite", "name": "Gemini 2.5 Flash Lite", "contextWindow": 256000},
          {"id": "gemma-3-12b", "name": "Gemma 3 12B", "contextWindow": 32000}
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "github-copilot/gpt-4o",
        "fallbacks": [
          "github-copilot/gpt-4o",
          "google/gemini-2.5-flash",
          "google/gemini-3.1-flash-lite",
          "ollama/qwen3.5:cloud",
          "ollama/glm-5",
          "github-copilot/claude-opus-4.5"
        ]
      },
      "workspace": "C:\\Users\\Admin\\.openclaw\\workspace"
    }
  },
  "channels": {
    "whatsapp": {
      "enabled": true,
      "dmPolicy": "pairing",
      "groupPolicy": "allowlist"
    }
  }
}
```

---

## 🛠️ RECOMMENDED FIXES (In Order)

### Fix #1: Remove glm-5 from config (it's not installed)
```json
// REMOVE this from ollama.models array:
{
  "id": "glm-5",
  "name": "glm-5",
  ...
}

// REMOVE from fallbacks:
"ollama/glm-5"
```

### Fix #2: Update model paths to use "ollama/" prefix consistently
Change config to use:
- `ollama/qwen3.5:cloud` ✅ (correct)
- Remove `openai-codex/glm-5` ❌ (that's not Ollama!)
- Remove `openai-codex/qwen3.5:cloud` ❌ (wrong provider!)

### Fix #3: Verify Ollama connectivity
```powershell
# Test Ollama API
curl http://127.0.0.1:11434/api/tags
curl http://127.0.0.1:11434/api/models

# Restart Ollama if needed
Get-Process ollama | Stop-Process
Start-Process ollama
```

### Fix #4: Reinstall missing glm-5 (Optional)
```powershell
ollama pull glm-5
```

### Fix #5: Restart OpenClaw gateway
```powershell
openclaw gateway restart
```

---

## 📦 Files Backed Up

- ✅ `openclaw.json` (primary config)
- ✅ `openclaw.json.bak` through `.bak.4` (existing backups)
- ✅ Ollama DB structure (db.sqlite)
- ✅ All model definitions
- ✅ Authentication profiles
- ✅ Channel configs (WhatsApp)

---

## 🚨 Action Items for Abdullah

1. **Read this backup file completely** ✅
2. **Decide:** Do you want glm-5 or not?
3. **If YES:** `ollama pull glm-5` and update config
4. **If NO:** Remove from config and fallbacks
5. **Restart:** `openclaw gateway restart`
6. **Test:** Try setting model to `ollama/qwen3.5:cloud`

---

## 📞 Support Info
- **WhatsApp:** Connected (+923114836720)
- **OpenClaw Docs:** https://docs.openclaw.ai
- **Gateway Port:** 18789 (loopback)
- **Timezone:** Asia/Karachi (GMT+5)

---

**Backup Created By:** Agent  
**Status:** READY FOR REVIEW & FIX
