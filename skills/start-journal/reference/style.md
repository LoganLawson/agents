# Style

Match the voice of the existing `STAR - *.md` entries in the vault. Read two or three before drafting.

Examples below are invented. They demonstrate shape, not content.

## Voice

- **First person, active.** "I migrated the build to Vite", not "the build tooling was migrated".
- **His contribution, not the team's.** The most common failure mode in a STAR is "we" doing the work. Where he decided something, the entry says he decided it. Where the team decided it, say what his part was.
- **Decisions over activity.** What he chose and why beats a list of what got done.
- **Plain.** No consultant register — no "leveraged", no "spearheaded". The existing entries say "I flagged", "I proposed", "I raised", "I built".
- **Present tense for live work**, past for finished. Ongoing initiatives are written in present tense.

## Honesty

The strongest convention in the existing set. Preserve it.

- Weak stories are labelled weak, with an italic `_(weaker)_` suffix in the one-pager, and the entry says plainly what didn't change.
- Incomplete work says so — "I'm not yet fully representing the chapter".
- Failures inside a success are kept — "the group identified most components but struggled to synthesise them within the time available".
- Unresolved threads live in Background — who hasn't acted, what decision is still pending.

An entry that contains only wins is less useful in an interview, not more. The follow-up question is always "what would you do differently", and the answer should already be in the file.

## Numbers

Use them wherever they exist. Shapes that work:

- `~1,300 lines removed`
- `from zero to ~80% coverage`
- `20–30 minutes → 2–3 minutes`
- `~50% migrated`
- `zero critical vulnerabilities`
- `~10% of team time allocated`

Approximate is fine and marked with `~`. Invented is never fine. If he doesn't have a figure, ask whether one exists somewhere he could check, then leave it out if it doesn't.

## Action structure

When a story has distinct strands, segment Action with bold sub-topic labels at sentence start:

```markdown
**Access control.** A configuration endpoint was reachable without authentication.
I confirmed the exposure, then raised it with the owning engineer...

**Token handling.** I identified two related weaknesses:
- Expiry enforced in client code, trivially bypassed
- One token used for both authentication and authorisation

**Dependency hygiene.** Maintained zero critical vulnerabilities.
```

Single-thread stories run as prose or a plain bullet list. Don't force segmentation.

## Tags

- 5–10 per entry
- Lowercase, dash-separated where needed
- One per line — no bullets, no commas
- Describe themes, skills, or domains, not the specific project

Already in use across the vault: `leadership`, `facilitation`, `cross-team-collaboration`, `systems-thinking`, `technical-decision`, `process-improvement`, `architecture`, `mentoring`, `incident-management`, `learning-culture`, `simulation-design`, `engineering-practice`, `organisational-learning`.

Prefer reusing an existing tag over minting a near-duplicate. Tags are the retrieval mechanism — `START journal.md` names "easily indexed, searched and distilled" as the whole point — so a tag appearing once is nearly useless. Grep the existing entries before inventing one.

## Naming

Three strings per story, allowed to differ:

| | Example |
|---|---|
| Filename | `STAR - CICD Testing and Build Improvements.md` |
| One-pager display name | `CI/CD, Build Quality & Developer Experience` |
| Title in prose | whatever reads well |

Filename should be searchable and stable. Display name should read well in a scannable list. Macrons are fine — macOS and Obsidian both handle them — so use them where they belong.

## One-pager paragraph

The rollup compression is a tight four-sentence arc:

> The reporting service was a legacy system — outdated build tooling, inconsistent patterns, no testing. The goal was to raise engineering quality in a live system without a full rewrite. I replaced the build chain, drove the TypeScript migration (~50%), introduced a standard data-fetching layer, and built testing from zero to ~80% coverage. This removed an unsupported build chain, established a testing culture, and set the patterns all new work now follows.

Sentence 1: situation, with the specifics that make it real.
Sentence 2: the goal — "The goal was to…" or "My aim was to…".
Sentence 3: what he did. The densest sentence: comma-separated actions, numbers inline.
Sentence 4: what changed, in organisational terms.

One paragraph, no more. The value of the one-pager is that a dozen stories fit on a page he can scan before an interview.
