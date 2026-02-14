# tmux Tutorials: Session Build Prompts

## How to Use

Each session builds one HTML lesson page. Copy the prompt template below, replace the bracketed placeholders using the lookup table, and paste it into Claude Code.

Build in order: Track 1 first (establishes the pattern), then Track 2, 3, 4.

---

## Prompt Template

```
I'm building the companion website for the tmux + AI CLI tutorials.

## Context files — read all of these first:

1. **Site plan** (architecture, content transformation rules, navigation):
   /Users/familyplate/work/learning-tools/tmux-fundamentals/TMUX-SITE-PLAN.md

2. **Source tutorial** (the content to transform):
   /Users/familyplate/work/learning-tools/tmux-claude/[SOURCE-FILE]
   Extract Lesson [N] from this file.

3. **Styling reference** (CSS with all component classes):
   /Users/familyplate/work/learning-tools/tmux-fundamentals/style.css

4. **Template** (HTML structure with placeholders):
   /Users/familyplate/work/learning-tools/tmux-fundamentals/_template.html

5. **Design reference** (completed page from this site, for visual matching):
   /Users/familyplate/work/learning-tools/tmux-fundamentals/[REFERENCE-PAGE].html

## What to build

Create: `/Users/familyplate/work/learning-tools/tmux-fundamentals/[FILENAME].html`

This is **Lesson [N]: [TITLE]** in the [TRACK-NAME] track ([LEVEL]).

## Navigation

- **Track**: [TRACK-NAME]
- **Prev**: [PREV-FILENAME].html — "[PREV-TITLE]"
- **Next**: [NEXT-FILENAME].html — "[NEXT-TITLE]"
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

## Session Lookup Table

### Track 1: tmux + Claude Code

Source: `tmux-claude-tutor.md`

| Session | Lesson | Filename | Title | Prev | Next | Reference Page |
|---|---|---|---|---|---|---|
| claude-01 | 1 | `claude-01-first-session.html` | Your First Session | `setup.html` / "Setup & Configuration" | `claude-02-detach-reattach.html` / "Detach & Reattach" | `setup.html` |
| claude-02 | 2 | `claude-02-detach-reattach.html` | Detach and Reattach | `claude-01-first-session.html` / "Your First Session" | `claude-03-split-panes.html` / "Split Panes" | `claude-01-first-session.html` |
| claude-03 | 3 | `claude-03-split-panes.html` | Split Panes | `claude-02-detach-reattach.html` / "Detach & Reattach" | `claude-04-launch-claude.html` / "Launch Claude Code" | `claude-02-detach-reattach.html` |
| claude-04 | 4 | `claude-04-launch-claude.html` | Launch Claude Code | `claude-03-split-panes.html` / "Split Panes" | `claude-05-supervisor-workflow.html` / "Supervisor Workflow" | `claude-03-split-panes.html` |
| claude-05 | 5 | `claude-05-supervisor-workflow.html` | The Supervisor Workflow | `claude-04-launch-claude.html` / "Launch Claude Code" | `claude-06-windows.html` / "Windows" | `claude-04-launch-claude.html` |
| claude-06 | 6 | `claude-06-windows.html` | Windows (Multiple Workspaces) | `claude-05-supervisor-workflow.html` / "Supervisor Workflow" | `claude-07-background-tasks.html` / "Background Tasks" | `claude-05-supervisor-workflow.html` |
| claude-07 | 7 | `claude-07-background-tasks.html` | Background Claude Tasks | `claude-06-windows.html` / "Windows" | `claude-08-copy-mode.html` / "Copy Mode" | `claude-06-windows.html` |
| claude-08 | 8 | `claude-08-copy-mode.html` | Copy Mode (Scrolling Back) | `claude-07-background-tasks.html` / "Background Tasks" | `claude-09-headless-sessions.html` / "Headless Sessions" | `claude-07-background-tasks.html` |
| claude-09 | 9 | `claude-09-headless-sessions.html` | Headless Claude Sessions | `claude-08-copy-mode.html` / "Copy Mode" | `claude-10-putting-it-together.html` / "Putting It Together" | `claude-08-copy-mode.html` |
| claude-10 | 10 | `claude-10-putting-it-together.html` | Putting It Together | `claude-09-headless-sessions.html` / "Headless Sessions" | *(none — use `<span></span>`)* | `claude-09-headless-sessions.html` |

### Track 2: tmux + Codex CLI

Source: `tmux-codex-tutor.md`

| Session | Lesson | Filename | Title | Prev | Next | Reference Page |
|---|---|---|---|---|---|---|
| codex-01 | 1 | `codex-01-first-session.html` | Your First Session | `setup.html` / "Setup & Configuration" | `codex-02-detach-reattach.html` / "Detach & Reattach" | `claude-01-first-session.html` |
| codex-02 | 2 | `codex-02-detach-reattach.html` | Detach and Reattach | `codex-01-first-session.html` / "Your First Session" | `codex-03-split-panes.html` / "Split Panes" | `claude-02-detach-reattach.html` |
| codex-03 | 3 | `codex-03-split-panes.html` | Split Panes | `codex-02-detach-reattach.html` / "Detach & Reattach" | `codex-04-launch-codex.html` / "Launch Codex CLI" | `claude-03-split-panes.html` |
| codex-04 | 4 | `codex-04-launch-codex.html` | Launch Codex CLI | `codex-03-split-panes.html` / "Split Panes" | `codex-05-supervisor-workflow.html` / "Supervisor Workflow" | `claude-04-launch-claude.html` |
| codex-05 | 5 | `codex-05-supervisor-workflow.html` | The Supervisor Workflow | `codex-04-launch-codex.html` / "Launch Codex CLI" | `codex-06-windows.html` / "Windows" | `claude-05-supervisor-workflow.html` |
| codex-06 | 6 | `codex-06-windows.html` | Windows (Multiple Workspaces) | `codex-05-supervisor-workflow.html` / "Supervisor Workflow" | `codex-07-multitasking.html` / "Multitasking" | `claude-06-windows.html` |
| codex-07 | 7 | `codex-07-multitasking.html` | Multitasking with Codex | `codex-06-windows.html` / "Windows" | `codex-08-copy-mode.html` / "Copy Mode" | `claude-07-background-tasks.html` |
| codex-08 | 8 | `codex-08-copy-mode.html` | Copy Mode (Handling Long Output) | `codex-07-multitasking.html` / "Multitasking" | `codex-09-headless-sessions.html` / "Headless Sessions" | `claude-08-copy-mode.html` |
| codex-09 | 9 | `codex-09-headless-sessions.html` | Headless Codex Sessions | `codex-08-copy-mode.html` / "Copy Mode" | `codex-10-putting-it-together.html` / "Putting It Together" | `claude-09-headless-sessions.html` |
| codex-10 | 10 | `codex-10-putting-it-together.html` | Putting It Together | `codex-09-headless-sessions.html` / "Headless Sessions" | *(none — use `<span></span>`)* | `claude-10-putting-it-together.html` |

### Track 3: Multi-Agent Orchestration

Source: `parallel-agents-tutor.md`

| Session | Lesson | Filename | Title | Prev | Next | Reference Page |
|---|---|---|---|---|---|---|
| parallel-01 | 1 | `parallel-01-multi-session-architecture.html` | Multi-Session Architecture | `setup.html` / "Setup & Configuration" | `parallel-02-launching-agents.html` / "Launching the Agents" | `claude-01-first-session.html` |
| parallel-02 | 2 | `parallel-02-launching-agents.html` | Launching the Agents | `parallel-01-multi-session-architecture.html` / "Multi-Session Architecture" | `parallel-03-assigning-tasks.html` / "Assigning Tasks" | `parallel-01-multi-session-architecture.html` |
| parallel-03 | 3 | `parallel-03-assigning-tasks.html` | Assigning Tasks | `parallel-02-launching-agents.html` / "Launching the Agents" | `parallel-04-control-dashboard.html` / "Control Dashboard" | `parallel-02-launching-agents.html` |
| parallel-04 | 4 | `parallel-04-control-dashboard.html` | The Control Dashboard | `parallel-03-assigning-tasks.html` / "Assigning Tasks" | `parallel-05-integration-point.html` / "Integration Point" | `parallel-03-assigning-tasks.html` |
| parallel-05 | 5 | `parallel-05-integration-point.html` | Integration Point | `parallel-04-control-dashboard.html` / "Control Dashboard" | `parallel-06-synchronized-commands.html` / "Synchronized Commands" | `parallel-04-control-dashboard.html` |
| parallel-06 | 6 | `parallel-06-synchronized-commands.html` | Synchronized Commands | `parallel-05-integration-point.html` / "Integration Point" | `parallel-07-conflict-resolution.html` / "Conflict Resolution" | `parallel-05-integration-point.html` |
| parallel-07 | 7 | `parallel-07-conflict-resolution.html` | Conflict Resolution | `parallel-06-synchronized-commands.html` / "Synchronized Commands" | `parallel-08-session-scripts.html` / "Session Scripts" | `parallel-06-synchronized-commands.html` |
| parallel-08 | 8 | `parallel-08-session-scripts.html` | Session Scripts | `parallel-07-conflict-resolution.html` / "Conflict Resolution" | `parallel-09-capture-review.html` / "Capture & Review" | `parallel-07-conflict-resolution.html` |
| parallel-09 | 9 | `parallel-09-capture-review.html` | Capture and Review | `parallel-08-session-scripts.html` / "Session Scripts" | `parallel-10-complete-workflow.html` / "Complete Workflow" | `parallel-08-session-scripts.html` |
| parallel-10 | 10 | `parallel-10-complete-workflow.html` | The Complete Workflow | `parallel-09-capture-review.html` / "Capture & Review" | *(none — use `<span></span>`)* | `parallel-09-capture-review.html` |

### Track 4: Developer Toolkit

Source: `dx-workflow-tutor.md`

| Session | Lesson | Filename | Title | Prev | Next | Reference Page |
|---|---|---|---|---|---|---|
| dx-01 | 1 | `dx-01-skeleton.html` | The dx Skeleton | `setup.html` / "Setup & Configuration" | `dx-02-choosing-ai.html` / "Choosing Your AI" | `claude-01-first-session.html` |
| dx-02 | 2 | `dx-02-choosing-ai.html` | Choosing Your AI | `dx-01-skeleton.html` / "The dx Skeleton" | `dx-03-review-command.html` / "Review Command" | `dx-01-skeleton.html` |
| dx-03 | 3 | `dx-03-review-command.html` | The Review Command | `dx-02-choosing-ai.html` / "Choosing Your AI" | `dx-04-pr-command.html` / "PR Command" | `dx-02-choosing-ai.html` |
| dx-04 | 4 | `dx-04-pr-command.html` | The PR Command | `dx-03-review-command.html` / "Review Command" | `dx-05-explain-command.html` / "Explain Command" | `dx-03-review-command.html` |
| dx-05 | 5 | `dx-05-explain-command.html` | The Explain Command | `dx-04-pr-command.html` / "PR Command" | `dx-06-test-command.html` / "Test Command" | `dx-04-pr-command.html` |
| dx-06 | 6 | `dx-06-test-command.html` | The Test Command | `dx-05-explain-command.html` / "Explain Command" | `dx-07-standup-command.html` / "Standup Command" | `dx-05-explain-command.html` |
| dx-07 | 7 | `dx-07-standup-command.html` | The Standup Command | `dx-06-test-command.html` / "Test Command" | `dx-08-popup-mode.html` / "Popup Mode" | `dx-06-test-command.html` |
| dx-08 | 8 | `dx-08-popup-mode.html` | Tmux Popup Mode | `dx-07-standup-command.html` / "Standup Command" | `dx-09-background-watchers.html` / "Background Watchers" | `dx-07-standup-command.html` |
| dx-09 | 9 | `dx-09-background-watchers.html` | Background Watchers | `dx-08-popup-mode.html` / "Popup Mode" | `dx-10-installation.html` / "Installation" | `dx-08-popup-mode.html` |
| dx-10 | 10 | `dx-10-installation.html` | Installation and Polish | `dx-09-background-watchers.html` / "Background Watchers" | *(none — use `<span></span>`)* | `dx-09-background-watchers.html` |

---

## Quick Reference: Filling the Template

| Placeholder | Where to Find It |
|---|---|
| `[SOURCE-FILE]` | Source column in lookup table (e.g., `tmux-claude-tutor.md`) |
| `[N]` | Lesson column (1–10) |
| `[FILENAME]` | Filename column |
| `[TITLE]` | Title column |
| `[TRACK-NAME]` | Track header (e.g., "tmux + Claude Code") |
| `[LEVEL]` | "Beginner" for Tracks 1–2, "Advanced" for Tracks 3–4 |
| `[PREV-FILENAME]` / `[PREV-TITLE]` | Prev column |
| `[NEXT-FILENAME]` / `[NEXT-TITLE]` | Next column |
| `[REFERENCE-PAGE]` | Reference Page column (a completed page for visual matching) |

---

## Special Cases

### Final lessons (claude-10, codex-10, parallel-10, dx-10)
- No "Next" link — use `<span></span>` as placeholder in page-nav
- "What's Next" callout should link back to `index.html` with a suggestion to try the next track

### Track 1 establishes the pattern
- Build Track 1 first. The first completed lesson (`claude-01`) becomes the design reference for all subsequent lessons.
- Track 2 shares structure with Track 1 (same tmux concepts, different AI tool). Don't copy-paste — each has tool-specific commands.

### Track 4 code density
- DX Toolkit lessons contain substantial bash scripts. Use `skill-file` components with headers for named files and `terminal-block` for command invocations. These pages will be the longest.

---

## Build Progress

- [x] Phase 0: Repository setup (.nojekyll, style.css, copy-code.js, _template.html)
- [x] Session 1: `index.html`
- [x] Session 2: `setup.html`
- [x] Track 1: claude-01 through claude-10
- [x] Track 2: codex-01 through codex-10
- [x] Track 3: parallel-01 through parallel-10
- [ ] Track 4: dx-01 through dx-10
  - [x] dx-01-skeleton.html
  - [x] dx-02-choosing-ai.html
  - [x] dx-03-review-command.html
  - [x] dx-04-pr-command.html
  - [x] dx-05-explain-command.html
  - [ ] dx-06-test-command.html
  - [ ] dx-07-standup-command.html
  - [ ] dx-08-popup-mode.html
  - [ ] dx-09-background-watchers.html
  - [ ] dx-10-installation.html
