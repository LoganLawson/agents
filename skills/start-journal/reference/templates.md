# Templates

## Entry — `STAR - <Title>.md`

```markdown
[START journal](START%20journal.md) · [review 2026](review%202026.md)

<Executive summary. Headingless. Written last, in Phase 3c. Briefing not story —
key action and outcome first. Length scales with complexity: a few sentences for
a simple story, multiple paragraphs for a complex one.>

## STAR Journal Entry

### Situation
<Context a stranger can follow. Environment, problem, constraints, why it mattered.>

### Task
<The goal and his ownership of it. What success looked like.>

### Action
<His decisions and steps, first person and active. Bold sub-topic labels where the
story has distinct strands.>

### Result
<Outcomes, impact, feedback, numbers. Bullets are fine. Honest about what didn't land.>

## Tomorrow

<Concrete, actionable next step.>

---

## Background (Detailed Context)

- Bullets only.
- Nest `###` subsections when long.

## Tags

tag-one
tag-two
tag-three
```

Notes:

- Backlink line is markdown with percent-encoded spaces, not wikilinks — match whatever the existing entries use.
- The `---` before Background appears in the full-spec entries. Keep it.
- Tags are newline-separated, not comma-separated, not a bullet list.
- S/T/A/R together land around 200–300 words. Tomorrow and Background sit outside that.
- Some older entries open with a `# Title` H1 and omit Tomorrow and Tags. That is a superseded format — do not copy it. The exec summary opens the document.

### Skeleton on first stage commit

When committing the first stage, create the file with the backlink line and all headings present, stages not yet written left empty. That way the entry file itself shows progress, and Phase 3 has a shape to fill.

---

## Context pack — `STAR - <Title> (context pack).md`

```markdown
[[START journal]] · [[STAR - <Title>]]

# Context pack — <Title>

Working file for the START journal entry. Raw material, not prose.

## Progress

- **Status:** Phase 2 — per-stage rinse
- **Committed:** Situation, Task
- **Current stage:** Action
- **Next:** Result
- **In-flight notes:**
  - Result still needs the deployment count — check Confluence
  - Decide whether the Microsoft conversation belongs in Action or Background

## Raw dump

<His words, lightly organised under loose sub-headings. Not rewritten. Not polished.
Transcription noise cleaned only where it obscures meaning.>

## Load-bearing answers

### What actually changed
### Numbers
### His contribution vs the team's
### Who else was involved
### Resistance and what nearly failed
### What's unresolved
### Why it mattered to the organisation

## Open gaps

- Things still unknown. Each one a question, never a guess.
- Carried forward until answered or explicitly dropped.

## Background candidates

- Material that's true and useful but won't fit the narrative.
- Feeds Phase 3b.
```

Notes:

- `## Progress` is the resume contract. Update it on every stage commit, before telling him the stage is done.
- **Status** is one of: `Phase 1 — context capture`, `Phase 2 — per-stage rinse`, `Phase 3 — consolidation`, `Complete`.
- The pack is linked from nowhere except itself and the entry — that's fine. It's working state, not a note to browse.

---

## One-pager block — appended to `STAR One-Pager 2026.md`

```markdown
### [[STAR - <Title>|<Short Display Name>]]
<One paragraph, roughly four sentences: situation → goal → what he did → what changed.>
```

Append a status suffix in italics where it applies — `_(in progress)_`, `_(weaker)_` — following the existing entries.

---

## Index bullet — appended to `START journal.md`

Under `## STAR examples (2026 review)`:

```markdown
- [[STAR - <Title>]]
```

Use the alias form `- [[STAR - <Title>|<Short Name>]]` only when the filename is unwieldy.
