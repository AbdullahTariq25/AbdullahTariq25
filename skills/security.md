# Skill: security

## Purpose
Run security audits, check dependencies, and ensure critical rules are followed before risky operations.

## When to use
- Before git push
- Before npm publish
- After adding new dependencies
- Weekly scheduled audits

## Quick checks
- `npm audit`
- `git diff --staged | grep -i "api_key\|password\|secret\|token\|private"`
- Ensure `.env` files are ignored

## Response style
When finding issues, be explicit about severity and remediation steps. Always ask before performing destructive fixes.
