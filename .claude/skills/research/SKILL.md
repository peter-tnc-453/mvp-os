---
name: research
description: Runs the opening research pass for a new MVP idea — problem framing, target job-to-be-done, and a lightweight market-size sanity check. Use at the very start of a new project, before writing a PRD, to ground the idea in a real problem instead of a guess.
license: Apache-2.0
metadata:
  phase: discover
  category: research
  composed_from: [define-problem-statement, define-jtbd-canvas, discover-market-sizing, discover-interview-synthesis]
  author: mvp-os (built on product-on-purpose/pm-skills, Apache-2.0)
---
<!-- mvp-os | composed from PM-Skills (https://github.com/product-on-purpose/pm-skills, Apache 2.0) -->
# Research

Research is the first station on the MVP pipeline: **Idea → Research → PRD → UI → Code → Deploy**. Its job is to turn a one-line idea into three grounded artifacts before anyone writes a spec — a **problem statement**, a **JTBD (jobs-to-be-done) canvas**, and a **market sanity check**. Skip this stage and the PRD ends up specifying a solution to a problem nobody has confirmed.

## When to Use

- Right after the user states an MVP idea in one or two sentences
- Before calling `/prd` — the PRD skill expects a problem statement and target job as input
- When a stakeholder asks "why are we building this?" and there's no written answer yet

## When NOT to Use

- The problem is already documented and agreed — skip straight to `/prd`
- You need a full persona (who the user is), not the job they're trying to do — use `/persona`
- You need to know who else competes for this job — use `/competitor`
- You have raw interview transcripts to process — that's `references/interview-synthesis.md`'s job; run it first, then feed its output into this skill as evidence

## Instructions

1. **Capture the idea as stated.** Do not expand scope yet — write down exactly what the user asked for.
2. **Write the problem statement.** Follow `references/problem-statement.md`: who has the problem, what's the cost of not solving it, what does success look like. Mark anything guessed (not sourced) as an assumption, not a fact.
3. **Build the JTBD canvas.** Follow `references/jtbd-canvas.md` — capture the functional job ("what are they trying to get done"), the emotional job, and the social job. This is what keeps the PRD from drifting into feature-list mode.
4. **Sanity-check the market, lightly.** For an MVP built in a classroom or a weekend, a full TAM/SAM/SOM model is overkill — run a *lite* pass of `references/market-sizing.md`: one top-down estimate, one bottom-up estimate, state the range, and flag confidence as Low/Medium/High. If there's no data at all, say so explicitly rather than inventing a number.
5. **If interview or user-feedback data exists**, run `references/interview-synthesis.md` over it first and fold the findings into steps 2-3 as evidence, not assumption.
6. **Output one combined brief** — problem statement + JTBD canvas + market sanity check, each under its own heading — ready to hand to `/prd`.

## Output Contract

A single markdown brief with three sections (`## Problem Statement`, `## Job to Be Done`, `## Market Sanity Check`), each following its source skill's structure, each entry tagged `[validated]` or `[assumed]`. No invented numbers — an assumption stays labeled as one.

## Quality Checklist

- [ ] Problem statement names who has the problem and the cost of not solving it
- [ ] JTBD canvas covers functional + emotional + social dimensions
- [ ] Market sanity check states a range and a confidence label, or says "no data — assumption only"
- [ ] Nothing presented as fact that wasn't sourced
- [ ] Output is ready to paste directly into `/prd` as input
