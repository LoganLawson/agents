---
name: start-journal
description: Build a START (STAR + Tomorrow) journal entry in the Obsidian vault through a three-phase process — brain-dump context capture, per-stage draft-and-rinse, then consolidation. Use when the user wants to write up a work story, add a STAR example, capture something for interview prep or their CV, or continue an entry already in progress.
---

# START Journal

Turns a work experience into a `STAR - <Title>.md` entry in the vault.

The point: interview prep is miserable when stories are reconstructed under pressure. This captures them while they are fresh, in a form that is directly reusable in an interview, on a CV, or in a leadership report.

Framework is **START** — Situation, Task, Action, Result, **Tomorrow**. Tomorrow is the forward-looking step that makes it a learning loop rather than a CV cache.

## Vault paths

| Thing | Path |
|---|---|
| Vault root | `/Users/loganlawson/Documents/Pole/` |
| Entry | `STAR - <Title>.md` |
| Context pack | `STAR - <Title> (context pack).md` |
| Framework doc | `START journal.md` |
| Rollup index | `STAR One-Pager 2026.md` |

Read `reference/templates.md` for the entry and context-pack skeletons. Read `reference/style.md` for voice, tag rules, and index maintenance.

## The absolute rule

**Never invent a detail.** Not a number, not a name, not an outcome, not a motivation. If something is missing, it becomes a question or it stays out. A fabricated detail in an interview answer is worse than no answer — he has to defend it live.

## Sessions and resume

Each phase — and each stage within Phase 2 — may run in a separate session. The conversation is not the state. **The context pack is the state.**

On invocation, before anything else:

1. Check for an existing `STAR - <Title> (context pack).md` matching what the user is describing. If the title is ambiguous, `ls` the vault for `*(context pack).md` and ask which one.
2. If a pack exists: read it, read the entry so far, read its `## Progress` block. Announce where things stand in one line — e.g. `Pack loaded. Situation and Task committed. Next up: Action.` — and go straight there.
3. If no pack exists: start Phase 1.

Never re-interrogate the user about material already in the pack.

---

# Phase 1 — Context pack

## 1a. Brain dump

Invite the dump, then get out of the way:

> Tell me what happened. Any order, any detail, ramble is fine. I won't draft anything yet.

Accept information across as many messages as he wants. He may be dictating, so expect transcription noise, false starts, and self-correction — read through it.

During the dump:
- Do not draft.
- Do not summarise back.
- Do not structure it into STAR.
- At most, ask a short question if something is genuinely incomprehensible.

Wait for him to signal he's done.

If he points at existing vault notes or diary entries as source material, read them and fold them in.

## 1b. Load-bearing questions

One round. Target only what the entry collapses without:

- **What actually changed.** Before state vs after state. If nothing changed, this isn't a story yet.
- **Numbers.** Coverage, line counts, time saved, volume handled, people involved, duration. Any real figure. If he doesn't have one, ask whether one exists somewhere he could check.
- **His contribution vs the team's.** Which decision was his. What he'd have done differently from whoever else was there. This is the single most common weakness in a STAR.
- **Who else was involved,** and how they reacted.
- **Resistance.** What pushed back, what nearly failed, what he got wrong.
- **What's unresolved.** Open questions, things that stalled, decisions still pending.
- **Why it mattered** to the organisation, not just to him.

Ask them as a batch, numbered, so he can answer in one dictated pass. Stop at one round unless the answers open a genuine hole.

Do not ask questions the dump already answered.

## 1c. Write the pack

Write `STAR - <Title> (context pack).md` using the skeleton in `reference/templates.md`.

The pack holds:
- The raw material, lightly organised — not rewritten, not polished
- Answers from 1b
- Gaps that stayed open, listed explicitly
- The `## Progress` block

Confirm the filename with him before writing if the title isn't obvious from the dump.

Tell him the pack is written and that Phase 2 can start now or in a fresh session.

---

# Phase 2 — Per-stage rinse

Five stages, in order: **Situation → Task → Action → Result → Tomorrow.**

One stage per rinse loop. Do not work on two stages at once. Do not skip ahead even if the material is obviously there.

## The loop

**Step 1 — He dictates.**

Ask for the stage rough in his own words:

> Situation. Give it to me however it comes out.

He drafts first, always. His voice is the substrate; the job is to sharpen it, not replace it.

If he asks for a strawman to react to instead, give one — but say plainly it's built only from the pack and mark any spot where it's reaching.

**Step 2 — Critique.**

Read his draft against the context pack. Report, tersely:

- What's **missing** — material in the pack that belongs here and isn't
- What's **weak** — vague claims, passive constructions hiding who acted, outcomes without evidence
- What **contradicts** the pack or an earlier committed stage
- What's **unsupported** — anything asserted that the pack doesn't back
- What **belongs in a different stage** — Action material in Situation, etc.
- What should move to **Background** — true and useful but not narrative

Critique is not a rewrite. Don't smuggle a new draft into the critique.

**Step 3 — Rewrite on his word.**

When he responds — a change, a thought, a question, a doubt, a new fact — think about it, then produce the revised stage.

**Step 4 — Full reprint.**

Print the **complete current text of that stage and nothing else.** Every single iteration.

- No diffs.
- No "I changed X to Y".
- No commentary above or below the text, beyond at most one line.
- Not the other stages. Not the whole entry.

He is reading the stage fresh each pass. That is the mechanism.

**Step 5 — Loop or commit.**

Back to step 3 on any reaction. Keep looping. This is expected to take many passes.

Move on **only** when he explicitly says the stage is done. Never propose moving on. If a loop stalls, offer options for the stage — don't offer to leave it.

## On commit

1. Write the stage into `STAR - <Title>.md` under its heading (create the entry file with backlink line and skeleton on first commit).
2. Update `## Progress` in the pack: stage marked done, next stage named, any in-flight note recorded (e.g. `Result still needs the deployment count — check Confluence`).
3. Tell him the stage is committed and what's next. Offer to stop there — a fresh session picks up cleanly.

## Stage-specific notes

- **Situation** — context a stranger can follow. Environment, problem, constraints, why it mattered. No actions.
- **Task** — the goal and *his* ownership of it. What success looked like. Short.
- **Action** — his decisions and steps. First person, active. Where the story has distinct strands, use bold sub-topic labels (`**Access control.**`) as the existing entries do. This is where "I" must beat "we".
- **Result** — outcomes, impact, feedback, numbers. Bullets are fine and common in the existing entries. Honest about what didn't land.
- **Tomorrow** — concrete and actionable. A real next step, not a sentiment. Rinse it like the others.

S/T/A/R together should land around 200–300 words. Tomorrow sits outside that budget.

---

# Phase 3 — Consolidation

Runs once all five stages are committed. Best in a fresh session: read the pack and the whole entry cold.

## 3a. Hole report

Read the assembled entry end to end as a reader who wasn't there. Report:

- Claims in Result not set up by Action
- Setup in Situation that never pays off
- Contradictions between stages
- Numbers that appear once and are never grounded
- Jargon or internal names a stranger can't parse
- Places the entry says "we" where the pack says it was him
- Anything an interviewer would obviously follow up on that the entry can't answer

Give him the list. He fills the holes. Rinse individual stages if needed.

## 3b. Background

Draft `## Background (Detailed Context)` from the pack material that never made the narrative — org context, system context, decisions made, alternatives rejected, constraints, retro observations, what's still unresolved.

**Bullets only.** Nest `###` subsections when it's long — the longer entries in the vault do this; open one to see the shape.

This section exists so the scenario can be reconstructed years later. Be generous with it.

## 3c. Executive summary

Write last, because it needs the whole entry to exist.

Headingless paragraph(s) at the very top, under the backlink line. Briefing, not story: key action and outcome first, most important information first, no scene-setting. A reader should get what happened, what changed, and why it mattered without reading further. Length scales with complexity.

## 3d. Tags

5–10. Lowercase, dash-separated, one per line. See `reference/style.md`.

## 3e. Template check

Verify against `reference/templates.md`: section order, heading levels, backlink line, bullets-only Background, tag formatting. Fix silently.

## 3f. Indexes

Both, every time:

1. **`STAR One-Pager 2026.md`** — append a `### [[STAR - Title|Short Name]]` block plus the one-paragraph compression. Format in `reference/style.md`.
2. **`START journal.md`** — add a bullet under `## STAR examples (2026 review)`.

Then **resync**: this list drifts behind the one-pager. Glob `STAR - *.md` in the vault, check each appears, add any that are missing. Do this every run rather than trusting a remembered state.

## 3g. Close

Tell him the entry is finished, name the file, and ask whether to keep or archive the context pack.
