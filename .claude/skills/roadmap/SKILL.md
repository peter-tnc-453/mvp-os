---
name: roadmap
description: Turns a PRD's feature list into a prioritized Now/Next/Later roadmap using a real prioritization framework (RICE/ICE/MoSCoW), plus one outcome-based OKR for the MVP milestone. Use after the PRD is written and before UI/build work starts, so the build order is a decision, not a guess.
license: Apache-2.0
metadata:
  phase: define
  category: planning
  composed_from: [define-prioritization-framework, foundation-okr-writer, define-opportunity-tree]
  author: mvp-os (built on product-on-purpose/pm-skills, Apache-2.0)
---
<!-- mvp-os | composed from PM-Skills (https://github.com/product-on-purpose/pm-skills, Apache 2.0) -->
# Roadmap

Roadmap sits between PRD and UI in the pipeline: **Idea → Research → PRD → Roadmap → UI → Code → Deploy**. An MVP built in a day or a week can't build every feature in the PRD at once — this skill decides *what order*, with a visible reason, not a gut call.

## When to Use

- Right after `/prd` produces a feature list, before `/ui` or `/build` starts
- When scope creeps mid-build and the team needs to re-confirm what's actually Now vs. Later
- When a stakeholder asks "why are we building X before Y?"

## When NOT to Use

- There's only one feature and no sequencing decision to make — skip straight to `/ui`
- You need to map outcomes to opportunities to solutions from scratch (deeper discovery, not just ordering an existing list) — use `references/opportunity-tree.md` directly
- You need multi-quarter planning across a whole team — this skill is scoped to a single MVP milestone, not a company roadmap

## Instructions

1. **Pull the feature list from the PRD.** Each feature becomes one row to score.
2. **Run the prioritization framework.** Follow `references/prioritization-framework.md`: for an MVP, RICE (Reach, Impact, Confidence, Effort) is usually the right default — score each feature, and if a framework needs data you don't have (e.g. Kano needs customer research), say so and fall back to a simpler one rather than fabricating a score.
3. **Bucket into Now / Next / Later.**
   - **Now** = ships in this MVP
   - **Next** = clearly valuable, deliberately deferred
   - **Later** = nice-to-have, revisit after the MVP validates
4. **Write one outcome-based OKR for the MVP milestone**, following `references/okr-writer.md` — the Key Result must be an outcome ("X% of test users complete the booking flow"), not a delivery checkbox ("ship the booking page"). Refuse to write a delivery-disguised-as-outcome KR; flag it back to the user instead.
5. **If the ordering itself is contested** (team disagrees on what the real opportunity is, not just the score), drop down to `references/opportunity-tree.md` to re-derive it from the outcome, not the feature list.

## Output Contract

A markdown roadmap: a scored table (framework + scores + rationale), a `Now / Next / Later` grouping, and one OKR block (Objective + 1-3 outcome-based Key Results). Every "Now" item must trace to a row in the scoring table — no unscored feature ships first.

## Quality Checklist

- [ ] Every PRD feature appears in the scoring table
- [ ] Framework choice matches available data (no fabricated Kano/customer-research scores)
- [ ] Now/Next/Later grouping is explicit and justified by the scores, not vibes
- [ ] The OKR's Key Results are outcomes, not delivery checkboxes
- [ ] Output is ready to hand to `/ui` as the build order
