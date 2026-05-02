# substack-notes

A Claude Code skill that drafts **Substack Notes** (50–250 words) calibrated for the platform's algorithm and your specific goal — picking from 8 Note types, refusing to fabricate, and closing with conversation-driven CTAs.

## Installation

This is a [Claude Code skill](https://docs.claude.com/en/docs/claude-code/skills). Drop the `substack-notes` folder into your skills directory:

**User-level (available in every project):**
```
~/.claude/skills/substack-notes/
```

**Project-level (this repo only):**
```
<your-project>/.claude/skills/substack-notes/
```

Copy the contents of [skills/substack-notes/](skills/substack-notes/) — `SKILL.md` plus the `references/` folder — preserving the structure:

```
substack-notes/
├── SKILL.md
└── references/
    ├── note-types.md
    └── anti-fabrication.md
```

Restart Claude Code (or the IDE extension) so the skill is picked up.

## Usage

### Trigger by slash command

Type the skill name as a slash command to invoke it explicitly:

```
/substack-notes
/substack-notes <your idea, topic, or link>
```

With no argument, the skill asks for your idea. With an argument, it goes straight into clarification → type proposal → draft.

### Trigger by natural language

The skill also auto-activates when your message matches its description. Example phrases that trigger it:

- `Draft a Substack Note about the build I shipped this week.`
- `Write a short post for Substack on <topic>.`
- `Turn this paragraph into a contrarian-take Note.`
- `Repurpose my latest post into a Note that funnels back to it.`
- `Restack commentary on this Note: <quote or link>.`

### What the skill does

1. **Detects missing critical info** (goal, audience, specific detail) and batches 1–3 clarifying questions via `AskUserQuestion`.
2. **Proposes 1–2 Note types** from the 8 formats with a one-line reason — and optionally previews hook drafts side-by-side so you can compare.
3. **Drafts the Note** in first-person, conversational, read-aloud-friendly prose, applying the chosen type's template (hook ≤10 words, 3–5 short paragraphs, conversation CTA).
4. **Outputs** the Note plus a meta line: `[{type-id} · {N}w]`.
5. **Iterates on feedback** — concrete revisions ("shorter", "change CTA to a question") apply directly; vague feedback ("make it better") triggers a clarifying question on which dimension to adjust.

### Output example

```
I shipped my first paid post yesterday.

Three subscribers upgraded in the first hour. None were people I knew.

I almost didn't publish it — the post sat in drafts for a week.

The lesson: the post you keep editing is the one that's already done.

What are you sitting on right now?
```

`[micro-story · 56w]`

## License

[MIT](LICENSE) © Luan Doan
