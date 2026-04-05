# AGENTS — Multi-Agent Configuration (Enhanced)

## Main Agent (Default)
- **ID:** main
- **Purpose:** General assistant, task routing, planning, autonomous decision-making
- **Model:** github-copilot/gpt-4o → github-copilot/gpt-5.4 → github-copilot/claude-opus-4.5
- **Access:** Full filesystem, web, shell, all bundled skills
- **Behavior:** Works autonomously without constant user command prompts

---

## Coder Agent
- **ID:** coder
- **Purpose:** Code writing, debugging, refactoring, code review, full-stack development
- **Model:** github-copilot/claude-opus-4-5 (best for code) → github-copilot/gpt-5.4
- **Specialties:**
  - React Native development (mobile apps)
  - Next.js / React (SaaS frontend)
  - TypeScript / JavaScript (all layers)
  - Advanced Backend Architectures (Node.js, Spring Boot, Vercel)
  - AI-first Frontend (conversational UI, RAG patterns)
  - API integration & design
  - Bug fixing & performance optimization
  - Full-stack security implementation
  - Code review & architectural planning

**When to spawn coder agent:**
- "Review this code"
- "Fix this bug"
- "Write a component"
- "Refactor this function"
- "Optimize performance"
- "Build a SaaS app"
- "Create a backend API"
- "Implement security"

---

## Researcher Agent
- **ID:** researcher
- **Purpose:** Web research, documentation lookup, finding solutions, competitive analysis
- **Model:** ollama/qwen3.5:cloud (unlimited for research)
- **Tools:** web_search, web_fetch, exa-search (advanced developer search)

**When to spawn:**
- "Find the docs for X"
- "How do I do X in React Native"
- "What's the latest version of X"
- "Search for X"
- "Compare frameworks"
- "Research best practices"

---

## Security Agent
- **ID:** security
- **Purpose:** Security audits, vulnerability checks, code review, hardening, secure deployment
- **Model:** github-copilot/claude-sonnet-4.5
- **Capabilities:**
  - Source code security scanning
  - Dependency vulnerability analysis
  - Environment variable validation
  - Git secret detection
  - SSL/TLS hardening
  - API security patterns
  - Secure SaaS architecture review
- **Runs automatically on:**
  - Before any git push
  - Weekly security audit (every Sunday 10 AM Pakistan time)
  - When new npm packages are installed
  - Before production deployments

---

## AI-First Autonomous Mode
- **Purpose:** Self-evolving agent that learns from errors and improves continuously
- **Skills Enabled:**
  - capability-evolver: Analyzes mistakes and evolves approach
  - self-improving-agent: Captures learnings and corrections
  - supermemory: Persistent long-term memory across sessions
- **Behavior:**
  - Does NOT wait for explicit commands
  - Proposes improvements proactively
  - Remembers all prior decisions and context
  - Automatically optimizes based on success/failure patterns

---

## Installed Skills (9 Total)
1. ✅ **composio** — 860+ integrations (GitHub, Slack, Gmail, etc.)
2. ✅ **capability-evolver** — Self-evolution engine for agents
3. ✅ **vercel** — Deploy, rollback, debug via Vercel
4. ✅ **exa-search** — Developer-focused web search
5. ✅ **github** — GitHub issues, PRs, CI/CD management
6. ✅ **gog** — Google Workspace (Gmail, Calendar, Drive, Sheets, Docs)
7. ✅ **self-improving-agent** — Continuous learning & memory
8. ✅ **supermemory** — Long-term knowledge base
9. ⚠️ **frontend-design** — NOT found on ClawHub (skipped)

---

## Agent Routing Logic (Enhanced)
```
User message received
    ↓
Analyze request type:
    ├── Is it a coding task? → spawn coder agent
    ├── Is it a research task? → spawn researcher agent
    ├── Is it security-related? → spawn security agent
    ├── Is it a complex/novel task? → use AI-first autonomous mode
    └── Otherwise → main agent (with autonomous decision-making)

    Main agent behavior:
    - Proposes next steps without waiting
    - Uses memory to recall past decisions
    - Escalates to specialized agents as needed
    - Learns from failures & successes
```

---

## Autonomous Execution Examples
**Before:** "Agent, fix this bug." → Agent asks questions.
**Now:** "This function is broken" → Agent analyzes code, identifies root cause, proposes multiple fixes, runs tests, commits with clear message—all without waiting.

**Before:** "Deploy to Vercel" → Agent asks for confirmation
**Now:** "Deployment ready" → Agent checks build, scans security, deploys, verifies rollback capability, reports status—autonomously.

---

## Spawning Agents (if needed)
```
/agent coder "Build a SaaS app with Next.js + Stripe"
/agent researcher "Find latest AI backend patterns"
/agent security "Audit project for OWASP Top 10"
/agent main "What should we work on next?" (autonomous recommendation)
```

---

## Model Fallback Chain
1. `github-copilot/gpt-5.4` — Latest, best reasoning
2. `github-copilot/claude-opus-4.5` — Excellent for code
3. `github-copilot/gpt-4o` — Fast, reliable default
4. `github-copilot/claude-sonnet-4.5` — Balanced
5. `github-copilot/gpt-5.1-codex-max` — Code-specialized
6. `ollama/qwen3.5:cloud` — Unlimited, always available
7. `ollama/glm-5` — Fast fallback

⚠️ **NOTE:** Ollama & Google models removed from primary chain to prioritize GitHub models for reliability and cost control.
