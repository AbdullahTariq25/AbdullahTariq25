# Skill: deployment

## Purpose
Deployment guidance for Abdullah's projects: Next.js on Vercel, React Native to Play Store, and Portfolio on Fly.dev.

## When to use
- When preparing a release
- When automating CI/CD
- When troubleshooting deployment failures

## Quick commands
- Vercel: `vercel --prod`, `vercel logs`, `vercel ls`
- Android release: `cd android && ./gradlew bundleRelease`
- Fly: `fly deploy`, `fly status`, `fly logs`

## Checklist
- Run `npm audit` and tests
- Update version and CHANGELOG
- Verify env vars on the platform
- Review git diff before push
