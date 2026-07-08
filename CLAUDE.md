# CLAUDE.md — MVP OS

This repo is a Product Operating System, not a code sample. When working in this repo, follow the rules below — they exist so an MVP gets built in one sitting without the common failure modes (over-scoped stack, unverified layers stacking on each other, a live deploy attempted on a broken build).

## The Pipeline

```
Idea → /research → /prd → /roadmap → /ui → /build (→ /frontend /backend /database) → /debug → /deploy
```

Full rationale: `framework/workflow.md`. Each skill's own `SKILL.md` has a "When NOT to Use" section — a stage can be skipped for a small enough idea, but skip it on purpose, don't skip it by accident.

## Ground Rules

1. **Verify before advancing a stage.** A PRD written without confirming the research brief, a database that hasn't been queried back, a frontend that hasn't been opened in a browser — all fail the same way: an unverified assumption surfaces later, with more context stacked on top of it, and costs more to fix than it would have at the stage it was made.

2. **Smallest stack that satisfies the PRD.** Default: SQLite + a single-file backend + plain HTML/CSS/JS. Reach for a framework, a heavier database, or a multi-file architecture only when the PRD's actual requirements demand it — not because it's "more proper." An MVP built in a class session doesn't get graded on architecture sophistication.

3. **Build order is Database → Backend → Frontend.** Verify each layer directly (query the DB, curl the endpoint) before the next layer depends on it. Building a frontend against an unverified backend means a bug could be in either layer — twice the debugging surface for no reason.

4. **State assumptions, don't bury them.** Every skill's output tags claims `[validated]` (has a source) or `[assumed]` (a stated guess). If a user asks for a number and none exists, say so and label the substitute as an assumption — don't present a guess as a fact.

5. **One root-cause fix at a time.** If a fix doesn't resolve the reproduced bug, form a different hypothesis rather than retrying variations of the same one. Two failed attempts at the same root cause means the approach is wrong, not the execution.

6. **Deploy only a verified build.** `/deploy` is the last stage for a reason — a live deploy of a broken build just moves the debugging onto a slower feedback loop (build logs, cold starts, env vars) instead of catching it locally where it's faster to see.

7. **No feature beyond what the PRD's "Now" bucket says.** Extra scope during a live build is the most common way a class demo runs out of time. If a good idea comes up mid-build, note it under `roadmap.md`'s "Later" — don't build it now.

## Skill Index

| Skill | Stage | Purpose |
|---|---|---|
| `/research` | Discover | Problem statement + JTBD + market sanity check |
| `/persona` | Discover | Evidence-calibrated product/marketing persona (optional depth) |
| `/competitor` | Discover | Competitive landscape (optional depth) |
| `/lean-canvas` | Define | One-page business model |
| `/prd` | Define | What's being built, why, how success is measured |
| `/roadmap` | Define | Now/Next/Later + one outcome-based OKR |
| `/ui` | Design | Screen list, layout, states — before code |
| `/build` | Build | Decides the stack, dispatches frontend/backend/database |
| `/frontend` | Build | UI code for one screen |
| `/backend` | Build | API/server layer |
| `/database` | Build | Schema + migration + seed data |
| `/debug` | Build | Root-cause fix when something breaks |
| `/deploy` | Deploy | Vercel (static) or Railway (has backend) → live URL |

## For Students Extending This Kit

Adding a new skill: copy an existing `.claude/skills/<name>/SKILL.md` as a starting shape (frontmatter + When to Use / When NOT to Use / Instructions / Output Contract / Quality Checklist) — consistency across skills is what makes the kit teachable in under an hour.
