# UnfoldAI

<p align="center"><strong>Your AI agents break things. You find out too late.</strong></p>

<p align="center">
UnfoldAI watches every agent action inside VS Code — commands, file changes, diagnostics, dependencies — and turns failures into issue cards with full context, AI fix plans, and recovery points. Before a bad agent run becomes a lost afternoon.
</p>

<p align="center">
  <a href="https://unfoldai.io">Website</a> |
  <a href="https://docs.unfoldai.io">Docs</a> |
  <a href="https://discord.gg/NMyBPAXGWE">Discord</a> |
  <a href="https://unfoldai.io/#pricing">Pricing</a>
</p>

<p align="center">
  <img src="https://i.imgur.com/sFrEij9.png" alt="UnfoldAI — AI agent supervision inside VS Code" width="100%">
</p>

If you use AI agents seriously, you already know the pattern:

- They touch five files before you look up.
- They rerun the same broken command three times and leave the repo worse.
- They change dependencies, overwrite your manual fix, or break types somewhere unrelated.
- By the time you notice, the terminal is noisy, the Problems panel is crowded, and there is no clean commit to go back to.

UnfoldAI stays in the editor, watches the session as it unfolds, and gives you ways to recover before it gets worse.

Works with **Cursor**, **Claude Code**, **GitHub Copilot**, **Codex**, **Continue**, **Codeium**, and any agent you add.

---

## What makes this different

UnfoldAI is not another AI coding tool. It is supervision infrastructure for the ones you already use.

- **Multi-agent** — tracks Cursor, Copilot, Claude Code, Codex, and others simultaneously in one session.
- **Attribution** — knows which agent changed which file, ran which command, and introduced which error.
- **Active, not passive** — creates silent checkpoints before risky operations, detects drift patterns, and alerts when an agent overwrites your work.
- **Session-wide context** — every AI action (fix plans, failure reviews, chat) draws from the full session history, not a blank prompt.
- **MCP-connected** — ships an MCP server so your agents can query UnfoldAI before they act.

---

## Live dashboard for agent sessions

UnfoldAI does not open into a passive metrics page. It opens into the session.

- **Issue cards** surface failures the moment they happen — not after you notice.
- **Agent Activity** tracks per-agent file changes, command counts, and error rates with colored progress bars.
- **Timeline** keeps a running log of commands, edits, diagnostics, and recoveries.
- **Queued issues** stack behind the current failure so earlier problems are not lost.
- **Running command indicator** shows what's executing right now and how long it's been going — amber after 30 seconds, red after 2 minutes.

<p align="center">
  <img src="https://i.imgur.com/ETR4qTn.png" alt="UnfoldAI Dashboard — issue cards, agent activity bars, and session timeline" width="400">
</p>

---

## Failures become actionable in seconds

When something breaks, UnfoldAI turns it into an issue card with the full story — what failed, which agent caused it, what files changed, and what to do about it. Expand the card to see error output, stack traces, file diffs, and related problems.

- **Fix plan** proposes the smallest safe fix, shows exact patches, and can auto-apply them on Pro.
- **Failure review** explains what happened, the likely root cause, key evidence, and what to check next.
- **Ask** opens episode-scoped chat with the right context already attached.
- **Resolve** marks it done and optionally saves the fix as a playbook for next time.


<p align="center">
  <img src="https://i.imgur.com/SJhVFaw.gif" alt="UnfoldAI — issue detected, fix plan generated" width="100%">
</p>

---

## AI that starts from the failure, not a blank prompt

When you click **Ask** on any issue, UnfoldAI opens a chat that already has the full episode context loaded — command output, diagnostics, file changes, agent attribution. No copy-pasting terminal output. No re-explaining what happened.

Suggested questions adapt to your current session: "Why did this fail?", "What changed before this broke?", "How do I fix this?" Click one and the investigation starts immediately.

**Failure review** generates a structured post-incident analysis: what happened, likely cause, evidence, prevention steps, and the safest next action.

<p align="center">
  <img src="https://i.imgur.com/vBRQh8i.png" alt="UnfoldAI Chat — episode-scoped investigation with session context" width="400">
</p>

---

## Catches agent mistakes before you do

UnfoldAI is useful even when you never click an AI action. The safety net runs in the background.

**Drift detection** catches agents stuck in loops. If Cursor runs `npm install` three times in a row with the same failure, UnfoldAI flags it as a drift pattern and lets you intervene before the fourth attempt makes things worse.

**Dependency mutation alerts** show exactly which packages were added, removed, or changed — not just "lockfile modified." You see `+lodash@4.17.23` and `-moment@2.29.4` so you know what the agent actually did to your dependencies.

**Human overwrite alerts** fire when an agent modifies a file you recently edited manually. Your work won't be silently overwritten without you knowing about it.

**Silent checkpoints** snapshot your dependency state before risky operations. If something breaks, restore with one click — no manual git stashing.

<p align="center">
  <img src="https://i.imgur.com/mVS9B83.png" alt="UnfoldAI — drift detection and dependency alerts on the dashboard" width="400">
</p>


<p align="center">
  <img src="https://i.imgur.com/PFggEcr.png" alt="UnfoldAI — human overwrite and dependency mutation alerts" width="400">
</p>


---

## Knows what happened while you were away

Leave your desk for lunch. Come back to find your agent ran 14 commands, modified 8 files, and introduced 2 errors.

Instead of digging through terminal history, UnfoldAI shows you a **Welcome Back** card with the full picture: how long you were away, what agents did, which commands failed, and what needs your attention. Click **Chat about it** to ask follow-up questions with the full away-period context already loaded.

<!-- SCREENSHOT NEEDED: Welcome Back card showing "Away X minutes" with agent activity stats, commands run, errors found. Replace the placeholder below with a real screenshot. -->
<p align="center">
  <img src="https://i.imgur.com/pQzHrPa.png" alt="UnfoldAI — Welcome Back session recap after being away" width="400">
</p>

---

## Playbooks: save solutions, surface them automatically

When you resolve an issue, UnfoldAI can save the solution as a **playbook**. The next time the same error pattern appears — in this project or another — UnfoldAI surfaces the matching playbook automatically so you don't solve the same problem twice.

Playbooks capture what happened, what fixed it, and how to verify the fix. One-off debugging sessions become reusable knowledge.

---

## Review before you commit

Before you merge agent-heavy work, UnfoldAI summarizes what actually happened in this coding cycle.

- **Risk scoring** based on the current state — failed commands, unresolved episodes, dependency changes, and drift patterns.
- **Attention items** show what still needs your review before committing.
- **AI commit message** grounded in real code diffs and session evidence — not hallucinated from filenames.
- **Use in Commit** sends the message directly to VS Code Source Control with one click.
- **Clear** resets the pre-commit scope when you start a new cycle, without losing session history.

<p align="center">
  <img src="https://i.imgur.com/mFWpTSn.png" alt="UnfoldAI Pre-commit Summary — risk scoring, AI commit message, Use in Commit" width="400">
</p>

---

## Built for every agent you use

UnfoldAI is not tied to one AI tool. It works with all of them at once and shows you who did what.

Out of the box: **Cursor** · **Claude Code** · **GitHub Copilot** · **Codex** · **Continue** · **Codeium**

Also works with: Aider, Cline, Windsurf, and others.

<p align="center">
  <img src="https://i.imgur.com/qADEWtG.png" alt="UnfoldAI Agent Activity — multiple agents tracked in one session" width="400">
</p>

Add your own agents:

```json
{
  "unfoldai.agentFingerprints.override": {
    "my-custom-agent": {
      "extensionIds": ["vendor.my-agent"]
    }
  }
}
```

No per-agent API keys. No registration. Install and go.

---

## Unfold Terminal

For the strongest capture accuracy, use the built-in **Unfold Terminal** (Ctrl+Shift+U). It provides complete command output capture, better timeout handling, and richer command lifecycle tracking than the native VS Code terminal can guarantee.

The extension works with both terminals. The Unfold Terminal ensures nothing is missed — especially long-running commands and commands with complex output.

---

## MCP: your agents can check before they act

UnfoldAI ships with an MCP server on every plan — including Free.

Your agents can query the live session before they keep editing:

```
> unfoldai_get_recent_issues()

[{
  "title": "Property 'length' does not exist on type 'never'",
  "file": "example.ts:58",
  "agent": "cursor",
  "status": "active",
  "severity": "error"
}]
```

Built-in MCP tools: `unfoldai_get_active_session` · `unfoldai_get_run_report` · `unfoldai_get_risk_signals` · `unfoldai_get_recent_issues` · `unfoldai_search_playbooks`

This means Claude Code can check what Cursor already broke before making its next move.

---

## Pricing

**MCP server access is free on every tier.**

| Feature | Free | Pro | Ultra |
| --- | --- | --- | --- |
| Price | **$0** | **$12.99/mo** | **$29.99/mo** |
| Dashboard, issues, timeline, drift, checkpoints, risk scoring | &#10003; | &#10003; | &#10003; |
| MCP server (all tools) | &#10003; | &#10003; | &#10003; |
| AI chat | 15/day | Unlimited | Unlimited |
| Fix plans | 1/day | Unlimited | Unlimited |
| Failure reviews | 2/day | Unlimited | Unlimited |
| AI commit messages | 1/day | Unlimited | Unlimited |
| Playbook saves | 1/month | Unlimited | Unlimited |
| Auto-apply patches | — | &#10003; | &#10003; |
| Premium chat presets | — | &#10003; | &#10003; |
| Priority routing | — | — | &#10003; |

---

## Get started in 30 seconds

1. Install from the Marketplace. Open the UnfoldAI sidebar.
2. Open a terminal and run something that fails: `npm run build`, `tsc --noEmit`, anything.
3. Watch UnfoldAI turn it into an issue card with full context.
4. Click **Fix plan**. Read the patches. Apply if they look right.

That is the loop. No configuration. No API keys.

For the best first-run experience, open the **Unfold Terminal** (Ctrl+Shift+U) and let an agent work — you will see every action tracked in real time.

---

## Security and privacy

- All session capture is local. Backend is only used for AI features (chat, fix plans, reviews).
- Secrets are redacted before any data leaves your machine.
- `unfoldai.privacy.localOnly` disables all backend calls if you want pure local monitoring.
- No API keys required.
