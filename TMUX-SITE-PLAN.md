# Plan: tmux + AI CLI Tutorials — GitHub Pages Companion Site

## Overview

Build a GitHub Pages companion website for the tmux + AI CLI tutorial materials currently living at `/Users/familyplate/work/learning-tools/tmux-claude/`. The site will be a **sister repository** to `skills-basics-and-beyond`, sharing the same visual design language (EB Garamond + JetBrains Mono, ink/cream/sepia palette, step cards, terminal blocks, YAML blocks) but with a navigation structure adapted for the tmux tutorials' branching track layout rather than a linear course progression.

---

## Source Material

Four tutorial files, each containing 10 lessons in Markdown:

| File | Track | Level | Lessons | Project Built |
|---|---|---|---|---|
| `tmux-claude-tutor.md` | tmux + Claude Code | Beginner | 10 | `td` (todo CLI) |
| `tmux-codex-tutor.md` | tmux + Codex CLI | Beginner | 10 | `td` (todo CLI) |
| `parallel-agents-tutor.md` | Multi-Agent Orchestration | Advanced | 10 | Bookmark API (handoff) |
| `dx-workflow-tutor.md` | Developer Toolkit | Advanced | 10 | `dx` (dev automation CLI) |

Supporting files:
- `PROJECT_CONTEXT.md` — shared config, troubleshooting, Ctrl+J setup
- `CLAUDE.md` — project context for Claude Code

Source location: `/Users/familyplate/work/learning-tools/tmux-claude/`

---

## Relationship to skills-basics-and-beyond

| Aspect | skills-basics-and-beyond | tmux-tutorials (this site) |
|---|---|---|
| **Repo name** | `claude-code-skills-basics-and-beyond` | `tmux-ai-cli-tutorials` (suggested) |
| **GitHub Pages URL** | `buildLittleWorlds.github.io/claude-code-skills-basics-and-beyond/` | `buildLittleWorlds.github.io/tmux-ai-cli-tutorials/` |
| **Structure** | 12 courses, linear progression | 4 tracks × 10 lessons, branching |
| **Shared CSS** | `style.css` (copy, identical) | `style.css` (copy, identical) |
| **Shared JS** | `copy-code.js` (copy, identical) | `copy-code.js` (copy, identical) |
| **Fonts** | EB Garamond + JetBrains Mono | EB Garamond + JetBrains Mono |
| **Cross-linking** | Course 7½ references tmux tutorials | Index links back to skills curriculum |

---

## Repository Structure

```
tmux-ai-cli-tutorials/
├── .nojekyll
├── style.css                          # Copied from skills-basics-and-beyond
├── copy-code.js                       # Copied from skills-basics-and-beyond
├── _template.html                     # Adapted template (track nav, not linear)
├── SESSION-PROMPT.md                  # Build instructions (like skills site)
│
├── index.html                         # Landing page: track overview + getting started
│
├── setup.html                         # Shared setup: Ctrl+J, tmux.conf, troubleshooting
│
│   ── Track 1: tmux + Claude Code (Beginner) ──
├── claude-01-first-session.html
├── claude-02-detach-reattach.html
├── claude-03-split-panes.html
├── claude-04-launch-claude.html
├── claude-05-supervisor-workflow.html
├── claude-06-windows.html
├── claude-07-background-tasks.html
├── claude-08-copy-mode.html
├── claude-09-headless-sessions.html
├── claude-10-putting-it-together.html
│
│   ── Track 2: tmux + Codex CLI (Beginner) ──
├── codex-01-first-session.html
├── codex-02-detach-reattach.html
├── codex-03-split-panes.html
├── codex-04-launch-codex.html
├── codex-05-supervisor-workflow.html
├── codex-06-windows.html
├── codex-07-multitasking.html
├── codex-08-copy-mode.html
├── codex-09-headless-sessions.html
├── codex-10-putting-it-together.html
│
│   ── Track 3: Multi-Agent Orchestration (Advanced) ──
├── parallel-01-multi-session-architecture.html
├── parallel-02-launching-agents.html
├── parallel-03-assigning-tasks.html
├── parallel-04-control-dashboard.html
├── parallel-05-integration-point.html
├── parallel-06-synchronized-commands.html
├── parallel-07-conflict-resolution.html
├── parallel-08-session-scripts.html
├── parallel-09-capture-review.html
├── parallel-10-complete-workflow.html
│
│   ── Track 4: Developer Toolkit (Advanced) ──
├── dx-01-skeleton.html
├── dx-02-choosing-ai.html
├── dx-03-review-command.html
├── dx-04-pr-command.html
├── dx-05-explain-command.html
├── dx-06-test-command.html
├── dx-07-standup-command.html
├── dx-08-popup-mode.html
├── dx-09-background-watchers.html
└── dx-10-installation.html
```

**Total pages: 43** (1 index + 1 setup + 40 lessons + 1 template)

---

## Navigation Design

### The Problem

The skills site uses linear prev/next navigation (Course 1 → 2 → 3 → ... → 11). The tmux tutorials use a **branching structure**:

```
                    ┌── Track 1: Claude (10 lessons)
index → setup → ──┤
                    └── Track 2: Codex  (10 lessons)
                              │
                              ▼
                    ┌── Track 3: Parallel Agents (10 lessons)
              ──────┤
                    └── Track 4: DX Toolkit     (10 lessons)
```

### Solution: Track-Scoped Navigation

Each lesson page has:

1. **Header nav**: Shows track name instead of phase label (e.g., "Track 1: tmux + Claude Code")
2. **Prev/Next**: Linear within the track (claude-01 → claude-02 → ... → claude-10)
3. **Track terminus links**: The last lesson in each beginner track links to the advanced track chooser. The last lesson in each advanced track links back to the index.
4. **Bottom nav**: Shows all 4 tracks grouped by level, with the current lesson highlighted

### Bottom Nav Structure

```html
<nav class="site-nav-bottom">
  <h3>All Lessons</h3>
  <ul>
    <li class="nav-phase-label">Getting Started</li>
    <li><a href="setup.html">Setup &amp; Configuration</a></li>

    <li class="nav-phase-label">Beginner: tmux + Claude Code</li>
    <li><a href="claude-01-first-session.html">1. Your First Session</a></li>
    <li><a href="claude-02-detach-reattach.html">2. Detach &amp; Reattach</a></li>
    <!-- ... through 10 -->

    <li class="nav-phase-label">Beginner: tmux + Codex CLI</li>
    <li><a href="codex-01-first-session.html">1. Your First Session</a></li>
    <!-- ... through 10 -->

    <li class="nav-phase-label">Advanced: Multi-Agent Orchestration</li>
    <li><a href="parallel-01-multi-session-architecture.html">1. Multi-Session Architecture</a></li>
    <!-- ... through 10 -->

    <li class="nav-phase-label">Advanced: Developer Toolkit</li>
    <li><a href="dx-01-skeleton.html">1. The dx Skeleton</a></li>
    <!-- ... through 10 -->
  </ul>
</nav>
```

### Cross-Site Links

- **This site's index.html** links to the skills curriculum: "Looking for Claude Code Skills? → skills-basics-and-beyond"
- **skills-basics-and-beyond Course 7½** already references the tmux tutorial — update that link to point to the live site once deployed

---

## Shared Setup Page

The `setup.html` page consolidates configuration from `PROJECT_CONTEXT.md`:

- Ctrl+J prefix setup (tmux.conf)
- Recommended tmux.conf for AI CLIs (256color, scrollback, mouse)
- Claude Code keybinding remap (optional)
- Codex CLI `--no-alt-screen` tip
- Troubleshooting table
- Quick-reference card (from tmux-claude-tutor.md appendix)

This avoids duplicating setup content across all 40 lesson pages.

---

## Content Transformation Rules

Identical to skills-basics-and-beyond. Each lesson in the source markdown follows a `Concept → Exercise → Checkpoint` pattern. Map as follows:

| Source Pattern | HTML Component |
|---|---|
| Lesson title (`## Lesson N: Title`) | `<h1 class="page-title">` |
| Concept explanation paragraphs | `<h2>`, `<h3>`, `<p>` |
| Exercise numbered steps | `<div class="step-card">` with `.step-number` + `.step-content` |
| Checkpoint verification items | `<ul class="checklist">` |
| Bash commands (`\`\`\`bash`) | `<div class="terminal-block">` |
| Config file contents | `<div class="skill-file">` with `.skill-file-header` |
| tmux key sequences (like `Ctrl+J %`) | `<code>` inline |
| Tables | `<table class="tool-table">` |
| Tips/warnings | `<div class="callout info">` or `<div class="callout warning">` |
| Quick reference cards | `<table class="tool-table">` grouped by category |
| "What you'll build" summaries | `<div class="callout info">` |
| End-of-lesson "next" pointer | `<div class="callout success">` |

### Lesson Metadata Bar

Each lesson page gets a metadata bar similar to the course meta pills:

```html
<div class="course-meta">
  <span class="meta-pill">Lesson <strong>N</strong> of 10</span>
  <span class="meta-pill"><strong>Beginner</strong></span>
  <span class="meta-pill">Track: tmux + Claude Code</span>
</div>
```

### Page Title Format

Combine lesson number with title and a subtitle phrase:

```
Your First Session — Creating and Entering a tmux Session
```

### Lead Paragraph

Each lesson should open with a 2–3 sentence lead paragraph (class `lead`) summarizing what the lesson covers and why it matters. These don't exist verbatim in the source markdown — synthesize them from each lesson's concept section.

---

## Index Page Design

The index page mirrors the structure of the skills site's `index.html` but adapted for tracks:

### Sections

1. **Hero area**: Site title, slogan ("Master tmux for AI-powered development"), subtitle
2. **Getting Started**: Brief intro + link to `setup.html`
3. **Choose Your Track**: Two card grids

**Beginner Tracks** (card grid, 2 columns):
```
┌─────────────────────────┐  ┌─────────────────────────┐
│ tmux + Claude Code      │  │ tmux + Codex CLI        │
│ 10 lessons · Beginner   │  │ 10 lessons · Beginner   │
│                         │  │                         │
│ Learn tmux fundamentals │  │ Learn tmux fundamentals │
│ while building a todo   │  │ while building a todo   │
│ CLI with Claude Code.   │  │ CLI with Codex CLI.     │
│                         │  │                         │
│ [Start Track →]         │  │ [Start Track →]         │
└─────────────────────────┘  └─────────────────────────┘
```

**Advanced Tracks** (card grid, 2 columns):
```
┌─────────────────────────┐  ┌─────────────────────────┐
│ Multi-Agent             │  │ Developer Toolkit       │
│ Orchestration           │  │                         │
│ 10 lessons · Advanced   │  │ 10 lessons · Advanced   │
│                         │  │                         │
│ Coordinate Claude and   │  │ Build `dx` — a set of   │
│ Codex across sessions   │  │ AI-powered dev commands │
│ with handoff workflows. │  │ using tmux scripting.   │
│                         │  │                         │
│ [Start Track →]         │  │ [Start Track →]         │
└─────────────────────────┘  └─────────────────────────┘
```

4. **Prerequisites**: callout info box (tmux 3.0+, basic CLI familiarity)
5. **Related**: Link to Claude Code Skills curriculum

---

## Session Lookup Table

Each row represents one HTML page to build. Build in the order listed (index first, then setup, then tracks in order).

### Index & Setup

| Session | Source | Filename | Title |
|---|---|---|---|
| 1 | (designed from scratch) | `index.html` | Curriculum Overview |
| 2 | `PROJECT_CONTEXT.md` | `setup.html` | Setup & Configuration |

### Track 1: tmux + Claude Code

Source: `tmux-claude-tutor.md`

| Session | Lesson | Filename | Title | Prev | Next |
|---|---|---|---|---|---|
| 3 | 1 | `claude-01-first-session.html` | Your First Session | `setup` | `claude-02` |
| 4 | 2 | `claude-02-detach-reattach.html` | Detach and Reattach | `claude-01` | `claude-03` |
| 5 | 3 | `claude-03-split-panes.html` | Split Panes | `claude-02` | `claude-04` |
| 6 | 4 | `claude-04-launch-claude.html` | Launch Claude Code | `claude-03` | `claude-05` |
| 7 | 5 | `claude-05-supervisor-workflow.html` | The Supervisor Workflow | `claude-04` | `claude-06` |
| 8 | 6 | `claude-06-windows.html` | Windows (Multiple Workspaces) | `claude-05` | `claude-07` |
| 9 | 7 | `claude-07-background-tasks.html` | Background Claude Tasks | `claude-06` | `claude-08` |
| 10 | 8 | `claude-08-copy-mode.html` | Copy Mode (Scrolling Back) | `claude-07` | `claude-09` |
| 11 | 9 | `claude-09-headless-sessions.html` | Headless Claude Sessions | `claude-08` | `claude-10` |
| 12 | 10 | `claude-10-putting-it-together.html` | Putting It Together | `claude-09` | `index` |

### Track 2: tmux + Codex CLI

Source: `tmux-codex-tutor.md`

| Session | Lesson | Filename | Title | Prev | Next |
|---|---|---|---|---|---|
| 13 | 1 | `codex-01-first-session.html` | Your First Session | `setup` | `codex-02` |
| 14 | 2 | `codex-02-detach-reattach.html` | Detach and Reattach | `codex-01` | `codex-03` |
| 15 | 3 | `codex-03-split-panes.html` | Split Panes | `codex-02` | `codex-04` |
| 16 | 4 | `codex-04-launch-codex.html` | Launch Codex CLI | `codex-03` | `codex-05` |
| 17 | 5 | `codex-05-supervisor-workflow.html` | The Supervisor Workflow | `codex-04` | `codex-06` |
| 18 | 6 | `codex-06-windows.html` | Windows (Multiple Workspaces) | `codex-05` | `codex-07` |
| 19 | 7 | `codex-07-multitasking.html` | Multitasking with Codex | `codex-06` | `codex-08` |
| 20 | 8 | `codex-08-copy-mode.html` | Copy Mode (Handling Long Output) | `codex-07` | `codex-09` |
| 21 | 9 | `codex-09-headless-sessions.html` | Headless Codex Sessions | `codex-08` | `codex-10` |
| 22 | 10 | `codex-10-putting-it-together.html` | Putting It Together | `codex-09` | `index` |

### Track 3: Multi-Agent Orchestration

Source: `parallel-agents-tutor.md`

| Session | Lesson | Filename | Title | Prev | Next |
|---|---|---|---|---|---|
| 23 | 1 | `parallel-01-multi-session-architecture.html` | Multi-Session Architecture | `setup` | `parallel-02` |
| 24 | 2 | `parallel-02-launching-agents.html` | Launching the Agents | `parallel-01` | `parallel-03` |
| 25 | 3 | `parallel-03-assigning-tasks.html` | Assigning Tasks | `parallel-02` | `parallel-04` |
| 26 | 4 | `parallel-04-control-dashboard.html` | The Control Dashboard | `parallel-03` | `parallel-05` |
| 27 | 5 | `parallel-05-integration-point.html` | Integration Point | `parallel-04` | `parallel-06` |
| 28 | 6 | `parallel-06-synchronized-commands.html` | Synchronized Commands | `parallel-05` | `parallel-07` |
| 29 | 7 | `parallel-07-conflict-resolution.html` | Conflict Resolution | `parallel-06` | `parallel-08` |
| 30 | 8 | `parallel-08-session-scripts.html` | Session Scripts | `parallel-07` | `parallel-09` |
| 31 | 9 | `parallel-09-capture-review.html` | Capture and Review | `parallel-08` | `parallel-10` |
| 32 | 10 | `parallel-10-complete-workflow.html` | The Complete Workflow | `parallel-09` | `index` |

### Track 4: Developer Toolkit

Source: `dx-workflow-tutor.md`

| Session | Lesson | Filename | Title | Prev | Next |
|---|---|---|---|---|---|
| 33 | 1 | `dx-01-skeleton.html` | The dx Skeleton | `setup` | `dx-02` |
| 34 | 2 | `dx-02-choosing-ai.html` | Choosing Your AI | `dx-01` | `dx-03` |
| 35 | 3 | `dx-03-review-command.html` | The Review Command | `dx-02` | `dx-04` |
| 36 | 4 | `dx-04-pr-command.html` | The PR Command | `dx-03` | `dx-05` |
| 37 | 5 | `dx-05-explain-command.html` | The Explain Command | `dx-04` | `dx-06` |
| 38 | 6 | `dx-06-test-command.html` | The Test Command | `dx-05` | `dx-07` |
| 39 | 7 | `dx-07-standup-command.html` | The Standup Command | `dx-06` | `dx-08` |
| 40 | 8 | `dx-08-popup-mode.html` | Tmux Popup Mode | `dx-07` | `dx-09` |
| 41 | 9 | `dx-09-background-watchers.html` | Background Watchers | `dx-08` | `dx-10` |
| 42 | 10 | `dx-10-installation.html` | Installation and Polish | `dx-09` | `index` |

---

## Session Prompt Template

Use this prompt when building each lesson page. Replace bracketed placeholders with values from the lookup table above.

```
I'm building the companion website for the tmux + AI CLI tutorials.

## Context files — read all of these first:

1. **Site plan** (architecture, content transformation rules, navigation):
   /Users/familyplate/work/learning-tools/skills/TMUX-SITE-PLAN.md

2. **Source tutorial** (the content to transform):
   /Users/familyplate/work/learning-tools/tmux-claude/[SOURCE-FILE]
   Extract Lesson [N] from this file.

3. **Styling reference** (CSS with all component classes):
   [REPO-ROOT]/style.css

4. **Template** (HTML structure with placeholders):
   [REPO-ROOT]/_template.html

5. **Design reference** (completed lesson from the same track, for visual matching):
   [REPO-ROOT]/[PREVIOUS-LESSON-FILENAME].html

## What to build

Create: `[REPO-ROOT]/[FILENAME].html`

This is **Lesson [N]: [TITLE]** in the [TRACK-NAME] track ([LEVEL]).

## Navigation

- **Track**: [TRACK-NAME]
- **Prev**: [PREV-FILENAME].html — "[PREV TITLE]"
- **Next**: [NEXT-FILENAME].html — "[NEXT TITLE]"
- **Bottom nav**: Use the track-grouped nav from `_template.html`, mark this lesson as `current`

## Lesson structure

Each source lesson follows: Concept → Exercise → Checkpoint.
Transform into: Lead paragraph → Concept sections → Step cards (exercises) → Checklist → What's Next callout.

## Quality standards

- Valid HTML5 (no unclosed tags)
- All internal links use correct filenames
- Copy buttons work on terminal-block, skill-file pre, prompt-box-dark
- Responsive at 600px breakpoint
- EB Garamond + JetBrains Mono fonts loaded
- Script tag for copy-code.js at bottom of body
- Lesson metadata bar shows correct lesson number, level, and track
```

---

## Build Order Recommendations

### Phase 0: Repository Setup (Session 0)
1. Create the GitHub repository `tmux-ai-cli-tutorials`
2. Copy `style.css`, `copy-code.js`, and `.nojekyll` from `skills-basics-and-beyond`
3. Create the adapted `_template.html` with track-based navigation
4. Enable GitHub Pages on the `main` branch

### Phase 1: Scaffolding (Sessions 1–2)
1. **Session 1**: Build `index.html` (landing page with track cards)
2. **Session 2**: Build `setup.html` (shared configuration page)

### Phase 2: Track 1 — Claude (Sessions 3–12)
Build all 10 lessons sequentially. This is the primary track and establishes the pattern for all other tracks. Use the first completed lesson as the design reference for subsequent ones.

### Phase 3: Track 2 — Codex (Sessions 13–22)
Lessons 1–3, 6, and 8 share significant structure with Track 1 (same tmux fundamentals, different AI tool). Lessons 4, 5, 7, 9, 10 have Codex-specific content.

### Phase 4: Track 3 — Parallel Agents (Sessions 23–32)
Advanced content. Each lesson is unique. These are longer and denser — expect larger HTML files.

### Phase 5: Track 4 — DX Toolkit (Sessions 33–42)
The longest source tutorial (21,706 bytes). Each lesson builds a new `dx` subcommand with substantial code. Expect the largest HTML files here.

---

## Special Notes

### Session 1 (index.html)
The landing page doesn't follow the lesson template. Build it as a track overview with card grids for beginner and advanced tracks, a "Getting Started" section linking to setup, and a cross-link to the skills curriculum. Use the skills site's `index.html` as a structural reference. No "Prev" link — use `<span></span>` as placeholder.

### Session 2 (setup.html)
Not a lesson — a reference page. Consolidates Ctrl+J config, recommended tmux.conf, troubleshooting table, and the quick-reference card from the Claude tutorial appendix. Use `tool-table` for the troubleshooting table and quick-reference. Navigation: prev = index, next = (none — user chooses a track from the bottom nav).

### Sessions 12, 22, 32, 42 (final lessons in each track)
These are "Putting It Together" / capstone lessons. The "What's Next" callout should link back to the index page with a suggestion to try the next track. No "Next" link in page-nav — use `<span></span>` as placeholder.

### Tracks 1 and 2 overlap
Lessons 1–3 (First Session, Detach/Reattach, Split Panes) teach identical tmux concepts with different AI tools. The HTML structure will be very similar. Don't copy-paste blindly — each has tool-specific commands and screenshots.

### Track 4 code density
The DX Toolkit tutorial contains substantial bash scripts (the `dx` dispatcher, individual command files, `lib.sh`). Use `skill-file` components with headers for named files and `terminal-block` for command invocations. These pages will be the longest on the site.

### Quick Reference Card
The Claude tutorial ends with a comprehensive tmux quick-reference card. Consider extracting this into a standalone section on the `setup.html` page (or a dedicated `quick-reference.html` page) so it's accessible from any track without being buried at the bottom of one track's final lesson.

---

## Slogan and Branding

| Element | skills-basics-and-beyond | tmux-tutorials (this site) |
|---|---|---|
| **Site label** | Claude Code Skills | tmux + AI CLI |
| **Site title** | Skills: Basics and Beyond | tmux for AI-Powered Development |
| **Slogan** | Build once, benefit every time. | See everything. Control everything. |
| **Subtext** | A hands-on curriculum for building skills, hooks, agents, and workflows in Claude Code. | Interactive tutorials for mastering tmux with Claude Code and Codex CLI. |

---

## CSS Additions

The existing `style.css` from skills-basics-and-beyond should work as-is for most components. One potential addition for the track-based navigation:

```css
/* Track indicator in header */
header nav .track-label {
  font-size: 0.85em;
  opacity: 0.7;
  font-style: italic;
}

/* Track card on index page (extends .card) */
.track-card {
  border-left: 4px solid var(--muted-teal);
}

.track-card.advanced {
  border-left-color: var(--sepia-brown);
}
```

These are minor — evaluate during Session 1 (index.html) and add if needed.

---

## Deployment Checklist

- [ ] Repository created at `github.com/buildLittleWorlds/tmux-ai-cli-tutorials`
- [ ] GitHub Pages enabled on `main` branch
- [ ] `style.css` and `copy-code.js` copied and verified
- [ ] `.nojekyll` file present
- [ ] `index.html` loads correctly at the Pages URL
- [ ] All 40 lesson pages link correctly (no broken prev/next links)
- [ ] All 40 lesson pages have correct bottom nav with `current` class
- [ ] Cross-link from skills site Course 7½ updated to point to live tmux site
- [ ] Responsive layout verified at 600px breakpoint
- [ ] Copy buttons functional on all code blocks
