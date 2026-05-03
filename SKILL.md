---
name: prd-reviewer
description: >
  Review a product requirements document through three lenses — Peer PM,
  Lead/Group PM, and CPO — each with a scored rubric and specific citations.
  Supports custom reviewer voices built from past feedback or style descriptions.
  Produces a full synthesis and prioritized edit list. Use when the user asks to
  review, critique, stress-test, or improve a PRD, product spec, feature brief,
  or one-pager. Also triggers for: "review my spec", "is my PRD ready", "stress
  test this PRD", "what would my CPO say about this", or when the user pastes a
  product doc and asks for feedback. Invoke immediately — gather context as part
  of the skill flow.
---

# PRD Reviewer

## What this skill does

Runs a structured PRD review through three reviewer lenses. Each reviewer scores
the document against a rubric, cites specific sections and gaps, and gives
actionable feedback. A synthesis at the end gives an honest overall read.

Any reviewer slot can be customized with a real person's past comments or style —
so the feedback reads like it came from someone specific on your team, not a template.

---

## Step 1: Gather context

Collect everything in one prompt. If any of it is already in context, skip asking for it:

1. **PRD content** — paste the full doc or share a file path
2. **PRD stage** — early draft, peer review, pre-leadership review, or pre-launch
3. **Product/company context** — if not in the doc, what does the product do and who are the users
4. **Specific concerns** — anything already suspected weak or to prioritize
5. **Custom reviewer voices (optional)** — for any reviewer slot, the user can provide:
   - A name and title (e.g., "Sarah, my Group PM")
   - Paste of past feedback or comments they've left
   - A style description (e.g., "always pushes on metrics, skeptical of scope, always asks about rollback")

Use custom voices to shape that reviewer's tone, focus areas, and language. If none provided, use the default persona.

Once you have what you need, proceed. Don't ask follow-up questions — use judgment on anything ambiguous.

---

## Step 2: Panel review

Each reviewer has a specific rubric. Score every criterion 1–10, cite actual sections
and language from the PRD, and give findings that are specific to this document — not
generic PRD advice.

---

### Reviewer 1: Peer PM

**Their lens:** Collaborator and implementer-proxy. Reading this as someone who might
hand it to design tomorrow or QA it next sprint. Is it complete? Is it buildable?
Would they be able to work from this?

**Rubric:**

| Criterion | What they're assessing |
|---|---|
| Problem definition | Is the user problem specific, evidence-backed, and clearly separated from the solution? |
| Requirement completeness | Are functional requirements clear enough for an engineer to estimate and build from? |
| Edge case coverage | Are error states, empty states, and non-happy-path scenarios addressed? |
| Success metrics | Are they specific, measurable, and time-bound? Do they measure outcomes, not just outputs? |
| Non-goals | Are scope boundaries explicit? Is it clear what's intentionally excluded? |
| Open questions | Are known unknowns tracked and owned? |

Score each criterion 1–10. Give 3–5 findings that cite actual sections, bullets, or
missing content. Name the single biggest thing that would block a handoff to engineering or design.

---

### Reviewer 2: Lead PM / Group PM

**Their lens:** Strategic owner. Has to defend this roadmap call to leadership and make
sure it doesn't create downstream problems for other teams. Reads with a skeptical eye
toward scope, risk, and alignment.

**Rubric:**

| Criterion | What they're assessing |
|---|---|
| Strategic alignment | Does this ladder to the right OKRs or strategic bets? Is the "why now" explicit? |
| Scope calibration | Is this the right size — not over-built or under-built for the stated problem? |
| Risk coverage | Are technical, adoption, competitive, and timeline risks identified and addressed? |
| Stakeholder alignment | Are dependencies, impacted teams, and required sign-offs documented? |
| Tradeoffs and alternatives | Are key tradeoffs explicit? Were alternatives considered and dismissed with reasoning? |
| Rollout and reversibility | Is there a phased plan, launch criteria, or rollback consideration? |

Score each criterion 1–10. Give 3–5 findings. Name the most likely reason leadership
would push back or send this back for more work.

---

### Reviewer 3: CPO

**Their lens:** Is this the right bet? Does the doc tell a clear story? Will this move
the needle in a way that matters? Reading at altitude — doesn't care about implementation
details, cares about whether this should exist.

**Rubric:**

| Criterion | What they're assessing |
|---|---|
| Problem-solution fit | Is the right problem being solved? Is the solution the simplest credible path to solving it? |
| User and market opportunity | Is the opportunity size justified? Is there evidence this matters to users at scale? |
| Success definition | Will we know if this worked? Are metrics tied to business outcomes, not just feature adoption? |
| Strategic fit | Does this belong in the roadmap right now — not later, not never? |
| Narrative clarity | Can this be communicated upward in 2–3 sentences to a board or exec team? |
| Long-term implications | Does this create technical debt, lock the product in, or open surface area the team isn't ready for? |

Score each criterion 1–10. Give 3–5 findings. Give one honest read on whether this PRD
makes a compelling case for building this thing.

---

## Step 3: Scorecards

For each reviewer, present a detailed table, then a summary across all three.

**Format per reviewer:**

**[Reviewer Name or Default Title] — [Overall Score]/10**
| Criterion | Score | Key finding |
|---|---|---|
| [criterion] | X/10 | [one-liner] |
| ... | | |

Then the summary scorecard:

| Reviewer | Score | Top concern |
|---|---|---|
| Peer PM | X/10 | [one-liner] |
| Lead / Group PM | X/10 | [one-liner] |
| CPO | X/10 | [one-liner] |
| **Overall** | **X/10** | [synthesis one-liner] |

---

## Step 4: Top 5 edits — ordered by impact

Synthesize across all three reviewers. Lead with highest-leverage changes first. Each item:
- References the specific section, bullet, or gap
- Says what to do, not just what's wrong
- Notes which reviewer(s) flagged it
- States the consequence of not fixing it

**Format:**

**1. [Edit title]**
What's wrong: [specific issue]
What to do: [concrete action]
Why it matters: [consequence — failed leadership review, blocked handoff, wrong bet, etc.]
Flagged by: [Reviewer(s)]

...through 5.

---

## Step 5: Synthesis

Write 3–5 sentences giving an honest overall read. Is this PRD ready? What is the actual
state of it? What's the one thing standing between this doc and being ready to ship to
leadership or into execution?

Don't hedge. If it needs significant work, say so. If it's close, say what "close" means specifically.

---

## Step 6: Offer rewrites

After the synthesis, offer:

> "Want me to rewrite any sections? I can tackle the problem statement, success metrics,
> non-goals, open questions, or any section that scored low. Just say which one."

If the user says yes, rewrite in their voice. Default PRD voice:
- **User-problem-first** — open with what the user can't do today, not the feature
- **Evidence-backed** — ground claims in data, interviews, or observed behavior
- **Specific** — real metrics, real scope, real constraints
- **Opinionated** — make the call, don't hedge. "We will not support X in v1" beats "X may be out of scope"
- **Scannable** — headers where needed, bullets where they earn it, tables for comparisons

If the user has their own voice preferences, honor those above the defaults.

---

## Custom reviewer guidance

If the user provides past feedback or a style description for any reviewer slot:

- Match their vocabulary and directness level
- Weight the rubric criteria they historically focus on
- Surface concerns they are known to raise, even if the doc doesn't obviously invite them
- If they left specific past comments, reference the pattern: "Based on how [Name] typically reviews, they'd push here on..."
- Make it sound like it came from that person, not a generic reviewer template

The custom voice doesn't change the rubric — it changes the tone, emphasis, and language of the feedback within that rubric.

---

## Tone guidance

Direct. This is a working document review, not a compliment session.

- If the PRD has a structural problem that will sink a leadership review, say so plainly
- If a section is genuinely strong, say that specifically — "the problem statement is grounded in user evidence and clearly separated from the solution" beats "good problem statement"
- Match the honest confidence of someone who has reviewed hundreds of PRDs and actually wants this one to get approved and executed well
