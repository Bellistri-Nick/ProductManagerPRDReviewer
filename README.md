# prd-reviewer — Claude Code Skill

A Claude Code skill that runs a structured PRD review through three distinct lenses: Peer PM, Lead/Group PM, and CPO. Each reviewer scores the document against a rubric, cites specific sections, and gives actionable feedback.

The standout feature: any reviewer slot can be replaced with a real person's voice, built from their past comments or a style description.

---

## What it does

When triggered, the skill:

1. **Gathers context** — PRD content, stage, product context, specific concerns, and optional custom reviewer voices
2. **Runs a three-lens panel review**, each reviewer using a scored rubric:
   - **Peer PM**: problem definition, requirement completeness, edge cases, success metrics, non-goals, open questions
   - **Lead / Group PM**: strategic alignment, scope calibration, risk coverage, stakeholder dependencies, tradeoffs, rollout plan
   - **CPO**: problem-solution fit, market opportunity, success definition, strategic fit, narrative clarity, long-term implications
3. **Produces per-reviewer scorecards** — each criterion scored 1–10 with a key finding
4. **Summary scorecard** across all three reviewers
5. **Top 5 prioritized edits** — ordered by impact, each citing the specific section and consequence of not fixing it
6. **Synthesis** — an honest 3–5 sentence read on whether the PRD is ready and what's standing in the way
7. **Offers to rewrite** weak sections on the spot

---

## Custom reviewer voices

The most useful feature for teams. For any reviewer slot, you can provide:

- A name and title ("Marcus, my Group PM")
- Past feedback or comments they've left on your work
- A style description ("always pushes on metrics, skeptical of scope, asks about rollback before anything else")

The skill uses that context to shape the reviewer's tone, focus areas, and language — so the feedback sounds like it actually came from that person.

**Example:**
> "My Group PM David always asks 'what's the v0 of this?' and pushes on whether configuration could solve it instead of new UI. He also always flags legal/compliance before anything gets on the roadmap. Use David's voice for the Lead PM reviewer."

---

## Requirements

- [Claude Code](https://claude.ai/code) (CLI or desktop app)

---

## Installation

1. Clone or download this repo
2. Copy the `prd-reviewer/` folder into your Claude Code skills directory:

**macOS / Linux:**
```bash
cp -r prd-reviewer ~/.claude/skills/prd-reviewer
```

**Windows (PowerShell):**
```powershell
Copy-Item -Recurse prd-reviewer "$env:USERPROFILE\.claude\skills\prd-reviewer"
```

Your skills directory should look like:
```
~/.claude/skills/
  prd-reviewer/
    SKILL.md
    evals/
      evals.json
```

3. Restart Claude Code (or reload the window in the desktop app)

---

## Usage

Ask Claude to review your PRD. Any of these will trigger it:

- "Can you review this PRD before I take it to my Group PM?"
- "Stress test this spec — I need to find the holes before leadership does"
- "Is my PRD ready for an exec review?"
- "What would my CPO say about this?"
- Or paste your PRD and ask for feedback

The skill will gather any missing context (including custom reviewer voices), then run the full review.

---

## Evals

The `evals/` folder contains three test cases:

1. **Weak early-draft PRD** — vague problem, solution-first, missing metrics. Tests whether the skill catches the fundamentals.
2. **Strong PRD with custom Lead PM voice** — tests the custom reviewer feature with a skeptical, scope-focused Group PM persona.
3. **Pre-CPO PRD with custom CPO voice** — tests a narrative-focused CPO persona and a strong-but-not-perfect document.

---

## Customization

The reviewer personas and rubric criteria are defined in `SKILL.md`. To adapt for a specific product domain (consumer, platform, infrastructure), edit the rubric criteria descriptions under each reviewer to weight the things that matter most in your context.

---

## License

MIT
