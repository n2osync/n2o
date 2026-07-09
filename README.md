<p align="center">
  <img src="https://n2osync.com/logo-square.png" alt="N2O" width="120" />
</p>

<h1 align="center">N2O - Notion to Obsidian Sync</h1>

<p align="center">
  <strong>True bidirectional sync between Notion and Obsidian.</strong><br/>
  Your knowledge, everywhere.
</p>

<p align="center">
  <a href="https://n2osync.com">Website</a> /
  <a href="https://n2osync.com/docs">Docs</a> /
  <a href="https://n2osync.com">Pricing</a> /
  <a href="https://github.com/n2osync/n2o/issues">Report a Bug</a>
</p>

---

## The Problem

You use Notion at work. Your team lives there - project boards, meeting notes, shared wikis. But your personal notes, your second brain, that lives in Obsidian. And right now, these two worlds don't talk to each other.

You're copy-pasting. You're exporting markdown that breaks. You're maintaining two separate copies of the same knowledge.

**N2O fixes that.**

## What N2O Does

- **Bidirectional sync** - changes flow both ways, Notion to Obsidian and back
- **Full content support** - all 27+ block types, 21 property types, rich text formatting
- **Database mapping** - Notion databases become Obsidian folders with frontmatter
- **Relations to Wikilinks** - Notion relations become Obsidian `[[backlinks]]`
- **Attachment sync** - images and files downloaded locally to your vault
- **Three-way merge** - when both sides change the same page, N2O merges them. You never lose data
- **Incremental sync** - only changed pages are re-fetched. Fast, even with large workspaces
- **Content stays local** - N2O talks directly to the Notion API and writes to your vault. Your note content is never sent to any N2O server

---

## Quick Start

### Via BRAT (Recommended)

N2O installs through [BRAT](https://github.com/TfTHacker/obsidian42-brat), which keeps it auto-updated:

1. Install **BRAT** from Obsidian's Community Plugins
2. Open BRAT settings > **Add Beta Plugin**
3. Enter: `https://github.com/n2osync/n2o`
4. Done. BRAT keeps it updated automatically.

### Manual Install

1. Download `main.js`, `manifest.json`, `styles.css`, and `sql-wasm.wasm` from the [latest release](https://github.com/n2osync/n2o/releases/latest)
2. Create `.obsidian/plugins/n2o/` in your vault
3. Copy all four files into that folder
4. Restart Obsidian, enable N2O in Community Plugins

---

## How It Works

| Action | Direction | What it does |
|--------|-----------|-------------|
| **Sync Now** | Notion > Obsidian | Pulls pages and writes them as Markdown |
| **Push Changes** | Obsidian > Notion | Sends your local edits back to Notion |
| **Preview** | Dry run | Shows what would change before it does |

**Automation:** Auto-sync on a timer, real-time fast polling, and auto-push on local edits.

When both Notion and Obsidian change the same page, N2O does a three-way merge using a stored base version. No data lost on either side.

---

## Pricing

Start with a **14-day free trial** (up to 300 pages, no credit card - start it from the plugin settings). After the trial, pick a plan to keep syncing with no limits:

| | Trial | Pro | Lifetime |
|---|:---:|:---:|:---:|
| Price | Free, 14 days | $8 / month | $249 once |
| Synced pages | 300 | Unlimited | Unlimited |
| All block types & properties | Yes | Yes | Yes |
| Pull + push sync | Yes | Yes | Yes |
| Three-way merge | Yes | Yes | Yes |
| Auto-sync, fast polling, auto-push | Yes | Yes | Yes |
| Custom templates & Bases views | Yes | Yes | Yes |

**Get N2O:** [Pro - $8/month](https://buy.polar.sh/polar_cl_P6gGNQIxY1HPcKYVeEUwtjaiWDVhPVaSBNYJV12q0Bk) or [Lifetime - $249](https://buy.polar.sh/polar_cl_Gc4muMDIVJNeTLgNZCzEnSwdv51jbzqCHZzMo2PbI61)

---

## Why I Built This

I kept two separate copies of everything - one in Notion for my team, one in Obsidian for myself. Every week I'd spend time manually syncing them. N2O started as a script to automate that. It grew into something that handles databases, properties, attachments, conflicts, and everything else that makes syncing between two very different apps hard.

If you use both Notion and Obsidian, this was built for you.

---

## Privacy

- **Your note content stays local.** N2O talks directly to the Notion API and writes to your vault. Your pages and notes are never sent to any N2O server.
- **License and diagnostics.** To validate your license and improve reliability, N2O sends the N2O license server your license and device id, plugin/Obsidian version and platform, and per-sync diagnostics: counts (pages, databases, conflicts), timings, and sanitized error messages. Error text is redacted so your page titles and content are not included.
- No advertising or cross-site tracking.

[Privacy Policy](https://n2osync.com/docs/legal/privacy/) / [Terms of Service](https://n2osync.com/docs/legal/terms/)

---

## Support

- **Docs** - [n2osync.com/docs](https://n2osync.com/docs)
- **Email** - support@n2osync.com
- **Issues** - [GitHub Issues](https://github.com/n2osync/n2o/issues)

---

<p align="center">
  N2O is a closed-source commercial plugin. This repository hosts releases only.
</p>
