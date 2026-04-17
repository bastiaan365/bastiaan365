# bastiaan365 (GitHub profile README)

The repo whose `README.md` renders as the landing page at <https://github.com/bastiaan365>. Maintained by Bastiaan ([@bastiaan365](https://github.com/bastiaan365)).

This file scopes Claude's behaviour for this repo. The global `~/.claude/CLAUDE.md` covers personal conventions; everything below is repo-specific.

## What this repo is

- A **single-file profile README** that's the first thing recruiters, peers, and curious strangers see when they land on the GitHub profile.
- Public-facing copy. Tone, accuracy, and freshness matter more than they would in any other repo. A stale claim or broken link here is a credibility leak.
- Not a creative writing project — keep it factual, present-tense, and let the linked repos do the showing.

## Repo conventions

### Honesty calibration (highest-priority rule)

- **Every claim about a project must match its current state.** If a repo is shipped (has working code + tests + documentation), describe it in present tense. If it is vapor (README only, no implementation), tag it `*(coming soon)*` like the existing pattern.
- **No future-tense without the tag.** "Will support X" or "I'm building Y" without `*(coming soon)*` reads as a broken promise to anyone clicking through.
- **No past-tense for active work.** "Built X" without ongoing maintenance becomes a "where is it now?" question.
- **Repo-table descriptions** must each be one short sentence. Match the existing kebab-format. Don't editorialise.

### When a linked repo's state changes

- **Vapor → shipped**: drop the `*(coming soon)*` tag, optionally add a credibility hook (test count, GUI mention, deployment medium).
- **Shipped → archived/abandoned**: remove the row entirely, or move it to a "Past projects" section if you want the credit.
- **New repo published**: add a row in the appropriate table position, verify the link resolves before commit (`gh api repos/bastiaan365/<repo-name>`).

### Sections — what changes and what doesn't

| Section | Edit cadence | Notes |
|---|---|---|
| Header / `whoami` block | Rarely | Career-level changes only — new role, new title |
| GitHub Stats badges | Never edit by hand | shields.io URLs auto-fetch from GitHub. If a badge is broken, fix the URL, don't redirect to a static value. |
| What I work with | When stack adds/drops a category | Keep alphabetical-ish within each row |
| Homelab | When the lab changes meaningfully | Don't update for cosmetic upgrades |
| Projects table | Whenever a repo state changes | See "Honesty calibration" above |
| Certifications | When you actually get a cert | Don't pre-list "studying for" — that's noise |
| Background | Career-level only | Job changes, employer additions |
| Get in touch | When a contact channel changes | |

### Validation gates

Before any commit:

- `markdown-link-check README.md` if it's installed (`npm install -g markdown-link-check`). Catches dead external links and wrong GitHub paths.
- For each repo listed in the projects table, `gh api repos/bastiaan365/<name>` returns a real repo. (We did this audit on 2026-04-17 — all 12 then-listed repos existed.)
- `wc -L README.md` to spot accidental long lines (table rows that wrap badly on smaller screens).
- Spell-check via your editor or `aspell` if you're paranoid.

## Workflow expectations for Claude

When I ask you to **add a new repo to the table**:

1. Verify the repo exists publicly: `gh api repos/bastiaan365/<repo-name>`.
2. Inspect the repo's content level (size, file count) to decide whether `*(coming soon)*` applies. The 2026-04-17 audit thresholds were: <5 KB / <3 files = vapor; otherwise shipped.
3. Match the existing one-line-description style.
4. Place it logically — adjacent to similar projects. Don't put a network repo between two security repos just because it's alphabetically next.
5. Show the diff before commit.

When I ask you to **modify a description**:

1. Show the diff with old/new visible.
2. Flag any embedded factual claim (test counts, "shipped", "live") that you can verify and intend to verify.
3. If the new description hypes something that isn't shipped yet, push back — credibility is more valuable than the embellishment.

When I ask you to **rewrite a section**:

1. Show the proposed full new section first as a code-block — don't apply.
2. Only apply after I confirm the tone matches (this is my voice on the public-facing landing page; small changes have outsized effect).

When **reviewing a change**:

1. Flag any honesty-calibration violation first (overstated claim, stale tag, wrong tense).
2. Flag broken links second.
3. Style/tone third.

## Things to avoid

- Adding emojis beyond the existing set without reason. The current README uses ✨ 🏗️ 🔒 📊 🧠 📝 🔗 sparingly as section markers. Don't sprinkle them inside descriptions.
- Adding new shields.io badges that count something not worth counting (commit count, follower count). The existing two badges (Stats + Top Languages) cover what matters.
- Mentioning specific employers / clients beyond what's already in the README (KLM, KLM Health Services). Anything else needs explicit go-ahead.
- Linking to private repos, draft repos, or Gist URLs. Profile shows public work only.
- Updating "Working on" certifications — flip them to "Done" only when the cert is actually achieved.

## Drift from target structure

_Claude maintains this section. List anything in the README that doesn't match the conventions above, with why it's still there and what would need to happen to fix it._

- **2026-04-17 audit findings**: One stale `*(coming soon)*` tag found on `Job-Agent` (which is actually shipped — 51 tests, GUI, .exe) — corrected. One missing `*(coming soon)*` tag found on `mcp-it-ops` (3 KB, README only) — corrected. All 11 other linked repos verified as substantive (>20 KB, multiple files).
