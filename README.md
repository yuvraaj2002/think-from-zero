<p align="center">
  <img src="assets/banner.png" alt="think-from-zero banner" width="100%">
</p>

<h1 align="center">think-from-zero</h1>

<p align="center">
  An open-source <a href="https://agentskills.io">Agent Skill</a> that makes your AI coding agent reason from first principles and explain anything from scratch.<br>
  Works with Cursor, Claude Code, Codex and any agent that supports <code>SKILL.md</code>.
</p>

---

## What it is

`think-from-zero` is a single `SKILL.md` file that teaches an agent to stop reasoning by analogy ("everyone uses X, so we should too") and instead:

1. **Restate the real goal** in measurable terms.
2. **List every assumption** and tag it `FACT`, `CONVENTION` or `GUESS`.
3. **Reduce to fundamental truths**: physics, maths, economics, real user needs, hard constraints.
4. **Rebuild** options from those truths only.
5. **Sanity-check** with Fermi estimates, inversion and counterexamples.
6. **Compare with convention**, including switching cost.
7. **Give a clear answer**, with confidence, what would change its mind, and the cheapest test.

It also has an **Explain mode** (Feynman-style) for understanding a concept from zero, plus variants for **architecture decisions**, **debugging** and **learning a new field**.

## Why another first-principles skill?

Several exist. This one aims to be the one you actually leave installed:

- **Calibrated effort.** Trivial choice? It says "convention is fine" in two lines. Big, irreversible decision? Full teardown. No theatre on small stuff.
- **Decides *and* teaches.** One skill covers pressure-testing decisions and genuinely learning a concept, with real check-for-understanding questions instead of "makes sense?".
- **Built for engineers.** Debugging and architecture variants, numbers over vibes, evidence gathered from the codebase before anything is called a "fact".
- **Always ends with an answer.** A recommendation, a confidence level and the cheapest experiment, never just "it depends".

## Install

The skill lives at `skills/think-from-zero/SKILL.md`. Install it by copying that folder into your agent's skills directory.

### Option A: skills CLI (any supported agent)

```bash
npx skills add yuvraaj2002/think-from-zero
```

### Option B: Cursor

Global (all projects):

```bash
git clone https://github.com/yuvraaj2002/think-from-zero.git /tmp/think-from-zero
mkdir -p ~/.cursor/skills
cp -r /tmp/think-from-zero/skills/think-from-zero ~/.cursor/skills/
```

Single project: copy it into `.cursor/skills/` (or `.agents/skills/`) at the project root instead.

```bash
mkdir -p .cursor/skills && cp -r /tmp/think-from-zero/skills/think-from-zero .cursor/skills/
```

Then type `/think-from-zero` in Agent chat, or just ask something like "think about this from first principles" and the agent will pick it up.

### Option C: Claude Code

```bash
git clone https://github.com/yuvraaj2002/think-from-zero.git /tmp/think-from-zero
mkdir -p ~/.claude/skills
cp -r /tmp/think-from-zero/skills/think-from-zero ~/.claude/skills/
```

For one project, use `.claude/skills/` in the repo instead. Invoke with `/think-from-zero` or let Claude trigger it automatically.

> Tip: Cursor also reads `~/.claude/skills/`, so one copy there covers both.

### Keep it updated

Clone once and symlink instead of copying, then `git pull` whenever you like:

```bash
git clone https://github.com/yuvraaj2002/think-from-zero.git ~/think-from-zero
ln -s ~/think-from-zero/skills/think-from-zero ~/.cursor/skills/think-from-zero
```

## Example

**Prompt**

> We should add a vector database for our RAG app, right? Everyone uses Pinecone. Think from zero.

**Output (abridged)**

> **Goal:** answer questions over our docs with good retrieval at under 300 ms, at low cost.
>
> **Assumptions:** [GUESS] we have a lot of data → checked: 40k chunks. [CONVENTION] RAG needs a dedicated vector DB → dropped. [FACT] Postgres is already in production.
>
> **Fundamental truths:** 40k × 1,536 dims × 4 bytes ≈ 250 MB, which fits in RAM. Exact search is ~60M multiply-adds, so milliseconds. Every new service adds cost, ops work and a failure point.
>
> **Answer:** use pgvector in the existing Postgres. Confidence: high.
> **Would change my mind:** passing ~5M vectors or p95 latency over budget. **Cheapest test:** load the chunks and measure p95 today.

Explain mode example prompts:

- "Explain attention in transformers from zero. I know basic linear algebra."
- "Help me actually understand why HTTPS is secure, then quiz me."

## Repo layout

```
think-from-zero/
├── skills/
│   └── think-from-zero/
│       └── SKILL.md      # the skill
├── assets/
│   └── banner.png        # README banner
├── README.md
└── LICENSE
```

## Further reading / Resources

The videos, essays, books and prior-art skills behind this skill are listed in [RESOURCES.md](RESOURCES.md).

## Contributing

Contributions are very welcome.

- **Found a case where the skill reasons badly?** Open an issue with the prompt, the output, and what a good answer would look like.
- **Improving the skill:** keep `SKILL.md` concise (well under 500 lines), model- and tool-agnostic, and follow the [Agent Skills spec](https://agentskills.io/specification): `name` must match the folder name, `description` stays under 1,024 characters.
- **New variants or worked examples:** add them to `skills/think-from-zero/references/` and link them from `SKILL.md` rather than growing the main file.
- Keep PRs small and explain the *why*. Fittingly, from first principles.

## License

[MIT](LICENSE) © 2026 Yuvraj Singh
