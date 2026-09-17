# Style

Match the voice of the existing `STAR - *.md` entries in the vault. Read two or three before drafting.

Examples below are invented, and deliberately unlike anything in the vault. They demonstrate shape,
not content.

This file must not carry a snapshot of the vault — no tag lists, no entry titles, no real figures,
no quoted prose. That kind of detail goes stale, and this repo is public. Where a vault specific is
needed, go and read the vault at runtime.

## Voice

- **First person, active.** "I migrated the build to Vite", not "the build tooling was migrated".
- **His contribution, not the team's.** The most common failure mode in a STAR is "we" doing the work. Where he decided something, the entry says he decided it. Where the team decided it, say what his part was.
- **Decisions over activity.** What he chose and why beats a list of what got done.
- **Plain.** No consultant register — no "leveraged", no "spearheaded". Prefer flat verbs: flagged, proposed, raised, built.
- **Present tense for live work**, past for finished. Ongoing initiatives are written in present tense.

## Honesty

The strongest convention in the existing set. Preserve it.

- Weak stories are labelled weak, with an italic `_(weaker)_` suffix in the one-pager, and the entry says plainly what didn't change.
- Incomplete work says so, in the entry and with an `_(in progress)_` suffix in the one-pager.
- Failures inside a success are kept — the part that stalled, the thing that ran out of time.
- Unresolved threads live in Background — who hasn't acted, what decision is still pending.

An entry that contains only wins is less useful in an interview, not more. The follow-up question is always "what would you do differently", and the answer should already be in the file.

## Numbers

Use them wherever they exist. Shapes that work:

- a count of something removed or added — `~800 lines removed`
- a before/after on a duration — `40 minutes → 5 minutes`
- a proportion, where the whole is obvious — `~60% migrated`
- an absolute floor or ceiling held — `zero critical vulnerabilities`
- a volume handled — `~12,000 records in one run`

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

**Read the existing vocabulary before tagging.** Grep the `## Tags` sections across the existing entries and work from what's there. Do not carry a remembered list into this — the vocabulary lives in the vault and changes as entries are added.

Prefer reusing an existing tag over minting a near-duplicate. Tags are the retrieval mechanism, so a tag that appears exactly once is nearly useless. A new tag is justified only when nothing in the existing set covers the theme.

## Naming

Three strings per story, allowed to differ:

| | Purpose |
|---|---|
| Filename | `STAR - <Title>.md` — searchable and stable, never renamed once linked |
| One-pager display name | Shorter, reads well in a scannable list |
| Title in prose | Whatever the sentence needs |

The filename is the link target, so fix it early and leave it alone. Macrons are fine — macOS and Obsidian both handle them — so use them where they belong.

## One-pager paragraph

The rollup compression is a tight four-sentence arc:

> The scheduling service had grown without an owner — three competing config formats, no integration tests, and a deploy nobody would run on a Friday. The goal was to make it safe to change without pausing delivery. I consolidated the config behind one loader, added integration tests around the two riskiest paths, and moved the deploy behind a check that runs them. Releases stopped being an event, and the next person to touch it had somewhere to start.

Sentence 1: situation, with the specifics that make it real.
Sentence 2: the goal — "The goal was to…" or "My aim was to…".
Sentence 3: what he did. The densest sentence: comma-separated actions, numbers inline.
Sentence 4: what changed, in organisational terms.

One paragraph, no more. The value of the one-pager is that every story fits on a page he can scan before an interview.
