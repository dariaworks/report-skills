<p align="center">
  <img src="assets/hero.jpg" alt="Report Skills — AI report generator skills for Claude Code and Codex: AI reports, decks and client reports published via the ReportRoom MCP" width="900" />
</p>

# Report Skills — Claude Code & Codex skills for AI reports, decks & client reports

<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-Compatible-D97757?logo=anthropic&logoColor=white" alt="Claude Code Compatible">
  <img src="https://img.shields.io/badge/Codex-Compatible-111827" alt="Codex Compatible">
  <img src="https://img.shields.io/badge/Claude-Skills-8A63D2" alt="Claude Skills">
  <img src="https://img.shields.io/badge/License-MIT-22C55E.svg" alt="MIT License">
  <img src="https://img.shields.io/badge/PRs-welcome-F59E0B.svg" alt="PRs Welcome">
</p>

**Report Skills is an AI report generator and AI report writer for Claude Code and Codex** — 5 skills that turn what your agent just made (research, analysis, proposals, status updates) into beautiful live web reports, client reports, and slide decks you can share with clients and your team. Published in one step via [ReportRoom](https://reportroom.io), with view analytics reported back to you ("your report picked up 42 views this week, peaking Tuesday"). A lightweight, tracked DocSend alternative for agent-made documents — no copy-pasting into Google Docs, no ugly PDF exports.

## What's inside

| Skill | What it does | Say things like |
|---|---|---|
| **report-publisher** | Any research or markdown → live, designed web report with a shareable URL | "publish this", "make this shareable", "turn this into a report" |
| **client-reporter** | Recurring client reports (SEO client report, monthly status, audits) as branded pages | "monthly report for my client", "send this to the client" |
| **proposal-tracker** | Publish a proposal as a tracked link — a DocSend alternative that tells you whether it's getting read | "send the proposal", "did they open it?" |
| **deck-publisher** | Content → responsive, presenter-friendly slide deck at a live URL | "make this a deck", "turn this into slides" |
| **report-designer** | Polish an existing page to the design bar: hierarchy, charts, dark mode, link previews | "make it beautiful", "improve the design" |

## Install

### Claude Code (CLI)

```bash
/plugin marketplace add dashaworks/report-skills
/plugin install report-skills@report-skills
```

### claude.ai (web)

1. Open https://claude.ai/code
2. Go to **Skills** in the sidebar
3. Click **Add from GitHub**
4. Paste: `dashaworks/report-skills`

### Claude Desktop (Mac / Windows)

1. Click **Customize** → **+** next to **Personal plugins** → **Add marketplace**
2. Choose **Add from a repository** and paste: `dashaworks/report-skills`
3. Install the plugin and start a new conversation

### Codex CLI

```bash
codex plugin marketplace add dashaworks/report-skills
codex plugin add report-skills@report-skills
```

### skills CLI ([skills.sh](https://www.skills.sh))

Install the five skills into any agent that reads `SKILL.md` (Claude Code, Codex, and others) with Vercel's `skills` CLI:

```bash
npx skills add https://github.com/dashaworks/report-skills/tree/main/skills
```

## How do I publish a report from Claude Code?

Install the plugin, then say "publish this" — the skill fetches ReportRoom's design system, authors a self-contained HTML report, lints it, shows you a preview, and publishes it as a live tracked URL. No account setup upfront: the skills create a ReportRoom account in-conversation on first use.

Under the hood, the skills publish through the **ReportRoom MCP server** — an agent-native publishing API (one call → live, tracked URL on your domain):

1. `get_design_system` — the agent fetches ReportRoom's design language
2. The agent authors a self-contained HTML report or deck following it
3. `lint_document` — automated quality check before anything goes live
4. `publish` — live URL back in seconds, analytics attached

No ReportRoom account yet? The skills self-provision one on first use — `create_account` issues an API key right in the conversation; verify your email (one click) and publish. Docs: https://docs.reportroom.io

Live documents count against your plan (free = 10, Pro = 100, Team/Business = unlimited). When you hit the cap, the skills offer to retire an old page to make room or point you to an upgrade — they never silently drop your new one. Team workspaces can also publish team-only pages and serve from a custom domain.

## Why not a PDF or a DocSend link?

- **Live pages beat attachments** — responsive, dark-mode, always the latest version, presentable from any device.
- **You learn what happens after you hit send** — view analytics come back to the agent as a signal it can act on, not a dashboard you have to remember to check. It's the DocSend read-tracking idea, agent-native.
- **Beautiful by default** — the design system supplies the taste; the agent supplies the content.

| | Report Skills + ReportRoom | PDF export | DocSend |
|---|---|---|---|
| Created by | Your agent, in one step from the chat | Manual export and formatting | Manual upload |
| Recipient gets | Live responsive web page, dark mode, always the latest version | Static attachment | File in a viewer |
| Analytics | Aggregate view counts, reported back to the agent | None | Per-viewer |
| Access control | Public link by default; [data rooms](https://github.com/dashaworks/data-room-skill) (Business plan) add email/passcode/allowlist gating, NDA, expiry, revocation, and per-viewer analytics | None | Email capture, passcodes |
| Updating after send | Republish to the same URL | Re-send the file | Re-upload a version |
| Works inside Claude Code / Codex | Yes — that's the point | Manual | No |
| Price to start | Free (10 live documents) | Free | Paid subscription |

## Safety defaults

Every skill shows you a preview and waits for your approval before anything client-facing goes live. Published pages are public URLs — the skills warn you before publishing anything that looks sensitive. Every page carries a discreet "Published with ReportRoom" footer credit, and the skills flag it before client-facing content goes out so it's never a surprise.

## FAQ

### What are Claude skills?

Claude skills are packaged instructions that teach Claude Code (and Codex) how to do a specific job well — here, publishing agent-made content as live web pages. Report Skills is a bundle of Claude Code skills (and Codex skills) you install once; each one triggers on plain requests like "publish this" or "send this to my client."

### Claude skills vs agents — what's the difference here?

The skill supplies the *how* (the report-writing craft, the design bar, the publish flow); your agent supplies the *what* (your content) and runs the tools. You keep driving the agent in natural language — the skill just makes its output publish-ready and on-brand.

### Is this a DocSend alternative?

For agent-made documents, yes — it's a DocSend alternative built for AI agents. `proposal-tracker` publishes a proposal or deck as a tracked link and reports back whether it's getting read (aggregate views by day) — the core DocSend move, without leaving your Claude Code or Codex session. When you need to know *which named person* read what — with email/passcode gating, NDA acceptance, expiry, and per-viewer analytics — that's a ReportRoom data room (Business plan); see the [virtual data room skill](https://github.com/dashaworks/data-room-skill).

### Are published reports private?

No. A published report or deck is a public URL that search engines can index — the hard-to-guess slug is obfuscation, not access control. The skills warn you before publishing anything that looks sensitive. For content that must be gated to named people, use a data room (email/passcode/allowlist access, NDA, expiry, instant revocation); for internal material, team workspaces can publish team-only pages.

### What can the AI report generator produce?

Client reports, SEO client reports, research write-ups, project status updates, audits, proposals, and slide decks — anything your agent just produced becomes a designed, shareable live page.

## Related skills

Report Skills is part of a family of publishing skills for Claude Code and Codex, all powered by the [ReportRoom](https://reportroom.io) MCP ([docs](https://docs.reportroom.io)):

- **[data-room-skill](https://github.com/dashaworks/data-room-skill)** — a virtual data room skill: gated document sharing for fundraising and due diligence, with email/passcode access, NDA acceptance, expiry, revocation, and per-viewer analytics.
- **[share-as-link-skill](https://github.com/dashaworks/share-as-link-skill)** — a share-as-a-link skill: the fastest path from any agent output to a live, shareable URL.
- **[seo-client-report-skill](https://github.com/dashaworks/seo-client-report-skill)** — a monthly SEO client report skill: recurring, branded SEO reports for agencies and freelancers.

## License

MIT — see [LICENSE](LICENSE). Contributions welcome.
