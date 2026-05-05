# PM PRD Reviewer

A Claude Code skill that runs a structured PRD review through three distinct lenses: Peer PM, Lead/Group PM, and CPO. Each reviewer scores the document against a rubric, cites specific sections, and gives actionable feedback.

The standout feature: any reviewer slot can be replaced with a real person's voice, built from their past comments or a style description.

---

## What it does

- Gathers context: PRD content, stage, product context, specific concerns, and optional custom reviewer voices
- Runs a three-lens panel review with scored rubrics
- Produces per-reviewer scorecards — each criterion scored 1–10 with a key finding
- Delivers a summary scorecard across all three reviewers
- Prioritizes the top 5 edits ordered by impact
- Provides a synthesis: an honest read on whether the PRD is ready and what's in the way
- Offers to rewrite weak sections on the spot

---

## Who it's for

Product managers preparing a PRD for leadership review, peer feedback, or engineering kickoff. Especially useful before taking a spec to your Group PM, CPO, or a cross-functional stakeholder who will poke holes in it.

---

## Output structure

1. Three reviewer panels — Peer PM, Lead PM, CPO — each with rubric scores and citations
2. Per-reviewer scorecards (each criterion 1–10)
3. Summary scorecard
4. Top 5 prioritized edits (section, issue, consequence)
5. Synthesis: ready or not, and why
6. Offer to rewrite any section

---

## How to use it

Install via [Claude Code](https://claude.ai/code). Clone this repo and copy the folder into your skills directory:

**macOS / Linux:**
```bash
cp -r ProductManagerPRDReviewer ~/.claude/skills/prd-reviewer
```

**Windows:**
```powershell
Copy-Item -Recurse ProductManagerPRDReviewer "$env:USERPROFILE\.claude\skills\prd-reviewer"
```

Restart Claude Code. Then trigger with natural language:

- "Can you review this PRD before I take it to my Group PM?"
- "Stress test this spec — I need to find the holes before leadership does"
- "Is my PRD ready for an exec review?"
- "What would my CPO say about this?"
- Paste your PRD and ask for feedback

---

## Custom reviewer voices

For any reviewer slot, provide:

- A name and title ("Marcus, my Group PM")
- Past feedback or comments they've left on your work
- A style description ("always pushes on metrics, skeptical of scope, asks about rollback before anything else")

The skill uses that context to shape the reviewer's tone, focus areas, and language — so the feedback sounds like it actually came from that person.

**Example:**
> "My Group PM David always asks 'what's the v0 of this?' and pushes on whether configuration could solve it instead of new UI. He also always flags legal/compliance before anything gets on the roadmap. Use David's voice for the Lead PM reviewer."

---

## Evals

Three test cases in `evals/`:

1. **Weak early-draft PRD** — vague problem, solution-first, missing metrics
2. **Strong PRD with custom Lead PM voice** — tests the custom reviewer feature with a skeptical, scope-focused persona
3. **Pre-CPO PRD with custom CPO voice** — tests a narrative-focused persona against a strong-but-not-perfect document
