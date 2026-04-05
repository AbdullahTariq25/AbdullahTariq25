# MEMORY — Persistent Memory Structure

## How Memory Works
- Daily memory files are stored in `memory/YYYY-MM-DD.md`
- On startup, read the latest file
- During session, append new learnings
- Never overwrite — always APPEND

---

## Abdullah's Permanent Profile

### Personal
- **Full Name:** Abdullah Tariq
- **City:** Bahria Town, Lahore, Pakistan
- **Timezone:** Asia/Karachi (GMT+5)
- **Phone:** +92 311 4836720
- **Email:** abdullah.tariq.7654@gmail.com
- **WhatsApp:** +923114836720 (linked to OpenClaw)

### Work
- **Current Job:** AI Data Annotation @ Shenzhen-Hong Kong Smart Hub (Remote, China) — Feb 2026
- **Previous:** Software Intern @ JFreaks Software Solutions, Lahore (Aug 2025 – Feb 2026)
- **Skills:** React Native, Next.js, React, Spring Boot, Vercel, AI/ML, KNIME
- **Achievement:** Represented Pakistan at Belt and Road Initiative Conference, Shenzhen

### Active Projects
| Project | Stack | Status | Path |
|---------|-------|--------|------|
| NetPulse Pro | React Native | Active | `E:\Abdullah React project\NetworkingTools NetPusle Pro` |
| Network Tools Hub | Next.js | Deployed (Vercel) | TBD |
| IPGeolocation.io App | React Native | Published (Play Store) | TBD |

### AI Setup
- **OpenClaw:** v2026.3.13, port 18789
- **Primary Model:** github-copilot/gpt-4o
- **Backup Models:** qwen3.5:cloud, glm-4.7-flash
- **WhatsApp:** Linked (+923114836720)
- **Web Search:** openclaw-web-search plugin installed
- **Local Model:** gemma4:e4b (downloading)

### Preferences
- Prefers short, direct responses — no fluff
- Understands English and Roman Urdu
- Calls me "Agent" or "bro"
- Wants automatic model fallback
- Privacy-conscious — prefers local/cloud models over paid APIs

---

## Memory Template (copy for each day)
```markdown
# Memory — [DATE]

## Tasks Completed
-

## Tasks In Progress
-

## Important Decisions
-

## Code Changes Made
-

## Issues Found
-

## Tomorrow's TODOs
-
```

---

## Silent Replies
When you have nothing to say, respond with ONLY: NO_REPLY
⚠️ Rules:
- It must be your ENTIRE message — nothing else
- Never append it to an actual response (never include "NO_REPLY" in real replies)
- Never wrap it in markdown or code blocks
❌ Wrong: "Here's help... NO_REPLY"
❌ Wrong: "NO_REPLY"
✅ Right: NO_REPLY

## Heartbeats
Heartbeat prompt: Read HEARTBEAT.md if it exists (workspace context). Follow it strictly. Do not infer or repeat old tasks from prior chats. If nothing needs attention, reply HEARTBEAT_OK.
If you receive a heartbeat poll (a user message matching the heartbeat prompt above), and there is nothing that needs attention, reply exactly:
HEARTBEAT_OK
OpenClaw treats a leading/trailing "HEARTBEAT_OK" as a heartbeat ack (and may discard it).
If something needs attention, do NOT include "HEARTBEAT_OK"; reply with the alert text instead.

## Heartbeats
... (keep as configured)
