<p align="center">
  <img src="https://n2osync.com/logo-square.png" alt="N2O Sync" width="110" />
</p>

<h1 align="center">N2O Sync</h1>

<p align="center">
  <strong>Your Notion and Obsidian, finally one workspace.</strong><br/>
  Edit on either side. N2O keeps both current and never overwrites your work.
</p>

<p align="center">
  <a href="https://github.com/n2osync/n2o/releases/latest"><img src="https://img.shields.io/github/v/release/n2osync/n2o?style=flat-square&sort=semver&label=version" alt="Latest release"></a>
  <img src="https://img.shields.io/badge/Obsidian-1.4.0%2B-7c3aed?style=flat-square" alt="Obsidian 1.4.0+">
  <img src="https://img.shields.io/badge/trial-14%20days%2C%20no%20card-22c55e?style=flat-square" alt="14-day trial">
</p>

<p align="center">
  <a href="https://n2osync.com">Website</a> /
  <a href="https://n2osync.com/docs">Docs</a> /
  <a href="https://n2osync.com/docs/pro/overview/">Pricing</a> /
  <a href="https://github.com/n2osync/n2o/issues/new">Report a bug</a> /
  <a href="https://github.com/n2osync/n2o/issues/new">Request a feature</a>
</p>

---

> **Not a Notion product.** N2O is an independent Obsidian plugin. It is not made
> by, endorsed by, or affiliated with Notion Labs or Obsidian. It uses Notion's
> public API with a token you provide.

> **Before you turn on two-way sync, keep Notion's page history enabled.** N2O
> writes to your real Notion workspace. It is careful about it, and the whole
> merge design exists so it never clobbers you, but a sync tool that writes to a
> live workspace deserves a safety net underneath it. Start with sync direction
> set to "Notion to Obsidian only" if you want to watch it work first.

## The two-tool tax

Your team lives in Notion. Project boards, meeting notes, the shared wiki, the
databases everyone actually uses. Your own thinking lives in Obsidian, because
that is where thinking happens: local files, backlinks, no loading spinner.

So you keep two copies of everything. You paste a Notion page into Obsidian to
work on it, then paste it back. The two versions drift. And somewhere in the back
of your head is the worry that one day a sync will quietly eat something you
cared about.

N2O makes them one workspace. Edit a page in either app and the other catches up
on its own. When both sides changed, N2O merges them instead of picking a winner.

## Key features

- 🔁 **Two-way sync.** Notion to Obsidian and Obsidian back to Notion, same
  content, same fidelity in both directions.
- 🛡️ **A merge that protects you.** Three-way merge against a stored base
  version. Non-overlapping edits from both sides are kept. N2O checks Notion's own
  last-edited time before it writes, so an edit you made in Notion is never
  silently clobbered, and a failed sync never leaves you with an empty page.
- ⏱️ **It runs on its own.** Notion changes arrive in your vault about a minute
  after you make them. Your Obsidian edits go back a few seconds after you stop
  typing.
- 🗂️ **Databases stay alive.** A Notion database becomes a folder of notes plus a
  native Obsidian Bases view: table, cards or board, carrying the Notion view type
  and its filters. Not a dead flat table.
- 🎨 **Your vault looks like Notion.** Page icons and covers, callout shapes,
  column layouts, rich bookmark cards, long-form dates, code copy buttons.
  Optional, and strictly display-only.
- ⚡ **Only what changed moves.** A content-aware block differ patches the blocks
  you touched instead of rewriting the page, and incremental sync only refetches
  pages Notion says have moved.
- 🔒 **Your content stays local.** Sync traffic goes straight to `api.notion.com`
  and straight into your vault. Your pages never pass through an N2O server.

## Why people install it

Beyond the obvious one:

| | |
|---|---|
| **A backup you can actually read** | A continuously updated, plain-Markdown mirror of your Notion on your own disk. Notion's own export is a manual `.zip` of UUID filenames and broken links. |
| **Offline, and fast** | Obsidian works on a plane. Local search is instant and takes regex. |
| **A graph of your Notion** | Relations become wikilinks, so you get backlinks and a graph view over content Notion can only draw as a table. |
| **Run AI over your own notes** | Copilot, Smart Connections and every RAG tool want Markdown on disk. Now your Notion is exactly that, locally. |
| **Queries Notion cannot express** | Dataview and Bases query across databases, folders and tags at once. |
| **Version control your workspace** | Put the vault in git and get per-commit diffs, blame and restore over your whole Notion. |
| **Migrate without a flag day** | Move off Notion gradually while both sides stay in step. No weekend where everything is broken. |
| **An exit ramp** | Price rise, account lockout, a company that pivots. Your knowledge is already in an open format you own. |

## Fidelity

**Blocks.** Paragraphs, H1 to H4, quotes, dividers, bulleted and numbered lists
with nesting, to-dos with checked state, callouts (icon mapped to the matching
Obsidian callout type), toggles and toggle headings, images, video, audio, PDFs,
file attachments, bookmarks, embeds, link previews, code blocks with the language
tag, inline and block maths, tables, multi-column layouts, synced blocks, child
pages, page mentions.

**Rich text.** Bold, italic, strikethrough, inline code, underline, links, text
colour and background colour.

**Properties.** All 23 Notion property types map to YAML frontmatter. Relations
become wikilink arrays. A property named "Tags" maps to Obsidian's native `tags:`
key. Property names are sanitised deterministically, and you can rename, exclude,
reorder or reformat any of them per database.

**Media.** Downloaded into `_files/` next to the note, because Notion's file URLs
expire after about an hour. Local files you add in Obsidian upload back to Notion.

Block-by-block mapping tables, including exactly what does and does not survive a
push back to Notion:
[supported blocks](https://n2osync.com/docs/reference/supported-blocks/) and
[supported properties](https://n2osync.com/docs/reference/supported-properties/).

## What it does not do perfectly

Every sync tool has edges. Ours are written down rather than discovered:

- Notion columns come into Obsidian with all their content, but pushed back they
  return as sequential blocks, not columns.
- A toggle can come back as a callout. The content is identical; the block type
  can flip. This is deliberate.
- Synced blocks push only their first child. The Notion API cannot create
  "original" synced blocks.
- Numbered lists lose custom start numbers and letter or Roman formatting on push.
- Table of contents blocks and auto-expanded URL previews cannot be recreated
  through the API.
- Formulas, rollups and system timestamps are read-only in Notion, so they pull
  but never push.
- Inbound changes are polled, not pushed. Notion does have a webhooks API, but it
  delivers to a public HTTPS endpoint, and a plugin running on your machine cannot
  be one. Routing your workspace activity through an N2O server would make it
  instant and would also mean your activity passes through us, which is the one
  thing this plugin exists to avoid. So we poll.
- Page and block comments are not exposed by the Notion API, so they do not sync.

The full list: [limitations](https://n2osync.com/docs/reference/limitations/).

## Install

Setup takes about five minutes.

**Via BRAT (keeps itself updated)**

1. Install **BRAT** from Obsidian's Community plugins
2. BRAT settings > **Add Beta Plugin**
3. Enter `https://github.com/n2osync/n2o`

**Manually**

1. Download `main.js`, `manifest.json`, `styles.css` and `sql-wasm.wasm` from the
   [latest release](https://github.com/n2osync/n2o/releases/latest)
2. Put them in `<your-vault>/.obsidian/plugins/n2o/`
3. Restart Obsidian and enable N2O in Community plugins

Requires Obsidian 1.4 or newer. Desktop only, on Windows, macOS and Linux.

Then connect: **Settings > N2O Sync > Connection**, either **Connect with Notion**
or paste an internal integration token from
[notion.so/my-integrations](https://www.notion.so/my-integrations).

Start your trial from the N2O dashboard. No card.

## How syncing works

| Action | Direction | What it does |
|---|---|---|
| **Sync** | Both ways | Reconciles Notion and your vault with a safe merge. Never silently overwrites; a real clash leaves a backup note. |
| **Send to Notion** | Obsidian to Notion | Pushes your local edits up |
| **Overwrite from Notion** | Notion to Obsidian | Replaces local files with Notion's version, no merge. A recovery action. |
| **Preview sync** | Neither | Shows what would change without writing anything |
| **Check this note matches Notion** | Neither | Verifies a single note against its Notion source |

**Automatic:** turn on **Get changes from Notion** and N2O checks about once a
minute while you are active, backing off when idle, with a periodic full re-scan
that also catches new pages and deletions. Turn on **Send my edits to Notion** and
your changes go up 3 to 30 seconds after you stop typing. Notes just written by an
inbound sync are not pushed back, so there is no loop.

**Direction control:** both ways, Notion to Obsidian only (a safe read-only
mirror), or Obsidian to Notion only.

## Commands

Not exhaustive. The full list is in the command palette under `N2O`.

- **Sync**: `Sync with Notion`, `Sync this note with Notion`, `Preview sync`
- **Send**: `Send changes to Notion`, `Send this note to Notion`,
  `Create this note in Notion`, `Delete this note from Notion`
- **Recover**: `Overwrite from Notion`, `Overwrite this note from Notion`
- **Verify**: `Check this note matches Notion`, `Scan vault for Notion files`
- **Automation**: `Pause auto-sync`, `Resume auto-sync`
- **Views**: `Open Dashboard`, `Open N2O panel`, `Manage Base Views`,
  `Open this note in Notion`
- **State**: `Export sync state to JSON`, `Import sync state from JSON`,
  `Copy diagnostics for support`, `Refresh license`

## Pricing

Start with a **14-day free trial**, every feature unlocked, up to 300 pages, no
card. After that, Pro (monthly or annual) and Lifetime are both one click away:

| | Trial | Pro | Lifetime |
|---|:---:|:---:|:---:|
| Synced pages | 300 | Unlimited | Unlimited |
| Databases | Unlimited | Unlimited | Unlimited |
| All blocks and properties | Yes | Yes | Yes |
| Two-way sync | Yes | Yes | Yes |
| Three-way merge | Yes | Yes | Yes |
| Automatic sync, both directions | Yes | Yes | Yes |
| Bases views and templates | Yes | Yes | Yes |
| Priority support | Yes | Yes | Yes |

[See pricing and buy](https://n2osync.com/pricing)

All sales are final, which is exactly why the trial gives you everything for 14
days with no card. Try it properly first.

Want pull-only, free, forever? [N2O Sync Lite](https://github.com/n2osync/n2o-lite)
is in the Obsidian community store and is open source under MIT.

## Why I built this

I kept two separate copies of everything, one in Notion for my team and one in
Obsidian for myself. Every week I would spend time manually syncing them. N2O
started as a script to automate that. It grew into something that handles
databases, properties, attachments, conflicts, and everything else that makes
syncing between two very different apps hard.

If you use both Notion and Obsidian, this was built for you.

## Access and privacy

N2O holds a Notion token and writes to your vault, so here is exactly what it
touches and why.

**What it reads and writes**

- **Your Notion workspace**, limited to the pages and databases you explicitly
  share with the integration, through `api.notion.com`. If you connect with an
  internal integration token, Notion only exposes what you shared from each page's
  **Connections** menu.
- **Your vault**, inside the sync folder you choose, plus a local SQLite file
  holding sync state.
- **Media**, downloaded from the Notion-hosted URLs the API returns.

**Where your content does and does not go**

- Your note content never passes through an N2O server. Sync is a direct
  conversation between your machine and Notion.
- The N2O license server receives your license and device id, plugin and Obsidian
  version and platform, and per-sync diagnostics: counts (pages, databases,
  conflicts), timings, and sanitised error messages. Error text is redacted so
  page titles and content are not included. Diagnostics can be turned off in one
  click under **Settings > Account**.
- No advertising, no cross-site tracking, no selling of anything to anyone.

**Your token** is stored in the vault's plugin settings and is only ever sent to
`api.notion.com`. Treat that file the way you would treat any credential, and do
not commit it or share it.

[Privacy policy](https://n2osync.com/docs/legal/privacy/) /
[Terms](https://n2osync.com/docs/legal/terms/)

## FAQ

<details>
<summary><strong>What happens if I edit the same page in both apps at once?</strong></summary>

N2O merges them. It compares Notion's version, your local version, and the version
stored from the last sync, and keeps changes from both sides where they do not
overlap. Where they genuinely conflict, it follows your setting: ask, prefer
Notion, prefer Obsidian, or prefer the newest edit. With backups on, the version
that was not kept is saved as a `.conflict.md` note so nothing is lost.

</details>

<details>
<summary><strong>Is it really instant?</strong></summary>

No. Inbound changes land in about a minute while you are working, and outbound
pushes go within seconds of you stopping typing.

Notion does publish a webhooks API, so the honest reason is not "Notion cannot".
Webhooks deliver to a public HTTPS endpoint, and a plugin running on your laptop
is not one. We could put an N2O server in the middle and make it instant, at the
cost of every change in your workspace passing through our infrastructure. That
trade is the opposite of why this plugin exists, so we poll instead.

</details>

<details>
<summary><strong>Will it hammer my Notion rate limit?</strong></summary>

Notion allows 3 requests per second. N2O targets 2.5, backs off when idle, and
syncs incrementally so it only refetches pages Notion reports as changed.

</details>

<details>
<summary><strong>Can I sync only part of my workspace?</strong></summary>

Yes. Pick specific pages and databases, with toggles for sub-pages and inline
databases, and per-database filters so you sync only the rows matching a
condition.

</details>

<details>
<summary><strong>Can I make it read-only so it never writes to Notion?</strong></summary>

Yes. Set sync direction to "Notion to Obsidian only". Nothing is ever written back.
This is a good way to start.

</details>

<details>
<summary><strong>What happens to my files if my licence lapses?</strong></summary>

Everything already synced stays in your vault, untouched. Syncing pauses until you
start Pro or Lifetime. Your notes are plain Markdown and remain yours regardless.

</details>

<details>
<summary><strong>Does it work on mobile?</strong></summary>

Not yet. Desktop only, on Windows, macOS and Linux. The sync state lives in a
local SQLite file and the plugin is marked desktop-only in its manifest.

</details>

<details>
<summary><strong>What is the difference from N2O Sync Lite?</strong></summary>

Lite pulls from Notion into Obsidian, on demand, free, with no page limit, and is
open source. N2O Sync adds pushing back to Notion, automatic background sync in
both directions, live Bases database views, the conflict review screen and
templates.

</details>

<details>
<summary><strong>Something went wrong. What do you need from me?</strong></summary>

Your Obsidian version, your N2O version, what you were doing, and anything in the
developer console (Ctrl+Shift+I on Windows and Linux, Cmd+Option+I on macOS).
`Copy diagnostics for support` in the command palette collects a sanitised report
for you.

</details>

## Support

- **Docs and guides**: [n2osync.com/docs](https://n2osync.com/docs)
- **Bugs**: [GitHub issues](https://github.com/n2osync/n2o/issues)
- **Questions, billing, licences**: support@n2osync.com

---

<p align="center">
  N2O Sync is a commercial plugin. This repository hosts releases and issues.<br/>
  The free pull-only edition, <a href="https://github.com/n2osync/n2o-lite">N2O Sync Lite</a>, is open source under MIT.
</p>
