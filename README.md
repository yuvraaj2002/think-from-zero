<p align="center">
  <img src="assets/think-from-zero-banner.png" alt="think-from-zero — reason from first principles" width="100%">
</p>

<h1 align="center">think-from-zero</h1>

<p align="center">
  <strong>Stop reasoning by analogy. Rebuild from what is actually true.</strong>
</p>

<p align="center">
  An open-source <a href="https://agentskills.io">Agent Skill</a> that teaches your AI to strip a problem to bedrock,<br>
  rebuild the answer from first principles, and explain any idea from scratch — Feynman-style.
</p>

<p align="center">
  <a href="https://github.com/yuvraaj2002/think-from-zero/stargazers"><img src="https://img.shields.io/github/stars/yuvraaj2002/think-from-zero?style=flat&color=c4a574" alt="GitHub stars"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-c4a574?style=flat" alt="MIT License"></a>
  <a href="https://agentskills.io"><img src="https://img.shields.io/badge/Agent%20Skills-compatible-8b7355?style=flat" alt="Agent Skills compatible"></a>
  <img src="https://img.shields.io/badge/version-1.1.0-8b7355?style=flat" alt="version 1.1.0">
</p>

<p align="center">
  Works with <strong>Cursor</strong>, <strong>Claude Code</strong>, <strong>Codex</strong>, and any agent that reads <code>SKILL.md</code>.
</p>

---

## The problem

<p align="center">
  <img src="assets/analogy-vs-bedrock.jpg" alt="Left: copying by analogy. Right: rebuilding from first principles." width="100%">
</p>

<p align="center">
  <sub>Left — reason by analogy (copy the recipe). Right — reason from zero (rebuild from primitives).</sub>
</p>

Most AI answers — and most human ones — sound like this:

> "Everyone uses Kafka / Pinecone / microservices / a Pro tier. So you should too."

That is reasoning **by analogy**. It is fast. It is often fine. It also silently inherits every assumption baked into the crowd: costs you don't need, complexity you can't afford, and "best practices" that were best for someone else.

**think-from-zero** makes the agent do the harder thing:

1. Name the real goal (measurable).
2. Tag every assumption as `FACT`, `CONVENTION`, or `GUESS`.
3. Reduce to fundamental truths — physics, maths, economics, incentives, base rates, hard constraints.
4. Rebuild options from those truths only.
5. Sanity-check with Fermi estimates, inversion, and counterexamples.
6. Compare with convention (including switching cost).
7. Give **one clear answer** — with confidence, what would change its mind, and the cheapest test.

No theatre. No "it depends" without a recommendation.

---

## Why this one

Several first-principles skills exist. This one is built to stay installed:

<p align="center">
  <img src="assets/calibrated-effort.jpg" alt="Calibrated effort — trivial choices stay light; high stakes get the full teardown." width="100%">
</p>

<p align="center">
  <sub>Calibrated effort: most choices stay in the small circle. Depth is rare and deliberate.</sub>
</p>

| | |
|---|---|
| **Calibrated effort** | Naming a lint rule? Convention is fine in two lines. Irreversible architecture? Full teardown. |
| **Decide · Explain · Hybrid** | Pressure-test a decision, learn a concept from zero, or get both. |
| **Beyond code** | Architecture, debugging, product, career, strategy — same method. |
| **Evidence before "facts"** | Looks at your code, logs, docs, and data before calling anything fundamental. |
| **Honest about limits** | Thin evidence → lower confidence. Safety, law, and ethics stay constraints, not assumptions to demolish. |
| **Always ends with an answer** | Recommendation + confidence + cheapest experiment. |

---

## Quick start

### One command (any supported agent)

```bash
npx skills add yuvraaj2002/think-from-zero
```

### Cursor

```bash
# Global — all projects
git clone https://github.com/yuvraaj2002/think-from-zero.git /tmp/think-from-zero
mkdir -p ~/.cursor/skills
cp -r /tmp/think-from-zero/skills/think-from-zero ~/.cursor/skills/
```

```bash
# Single project
mkdir -p .cursor/skills
cp -r /tmp/think-from-zero/skills/think-from-zero .cursor/skills/
```

### Claude Code

```bash
git clone https://github.com/yuvraaj2002/think-from-zero.git /tmp/think-from-zero
mkdir -p ~/.claude/skills
cp -r /tmp/think-from-zero/skills/think-from-zero ~/.claude/skills/
```

> Tip: Cursor also reads `~/.claude/skills/`, so one copy can cover both.

### Stay updated (symlink)

```bash
git clone https://github.com/yuvraaj2002/think-from-zero.git ~/think-from-zero
ln -s ~/think-from-zero/skills/think-from-zero ~/.cursor/skills/think-from-zero
# later: cd ~/think-from-zero && git pull
```

Then in chat:

```text
/think-from-zero
```

Or just say it naturally:

```text
Think about this from first principles.
Is this overengineered?
Explain attention from zero — I know basic linear algebra.
Build vs buy for our auth — from scratch.
```

---

## See it work

**Prompt**

> We should add a vector database for our RAG app, right? Everyone uses Pinecone. Think from zero.

**Output (abridged)**

```text
Goal: answer questions over our docs with good retrieval at under 300 ms, at low cost.

Assumptions:
- [GUESS] We have a lot of data → checked: 40k chunks
- [CONVENTION] RAG needs a dedicated vector DB → dropped
- [FACT] Postgres is already in production; the team knows it

Fundamental truths:
- 40k × 1,536 dims × 4 bytes ≈ 250 MB — fits in RAM
- Exact search over 40k vectors ≈ milliseconds on one CPU
- Every new service adds cost, ops work, and a failure point

Answer: use pgvector in the existing Postgres. Confidence: high.
Would change my mind: ~5M vectors or p95 over budget.
Cheapest test: load the 40k chunks and measure p95 today.
```

More walkthroughs (product pricing, career pivots, etc.) live in [`skills/think-from-zero/references/examples.md`](skills/think-from-zero/references/examples.md).

**Explain mode prompts**

```text
Explain attention in transformers from zero. I know basic linear algebra.
Help me actually understand why HTTPS is secure, then quiz me.
What problem does a queue solve? Build it from primitives.
```

---

## How the method works

<p align="center">
  <img src="assets/method-flow.jpg" alt="Seven-step first-principles method flow" width="100%">
</p>

<p align="center">
  <sub>Calibrate → gather → goal → tag assumptions → bedrock → rebuild → verify &amp; test</sub>
</p>

<p align="center">
  <img src="assets/assumption-tags.jpg" alt="FACT, CONVENTION, and GUESS assumption tags" width="100%">
</p>

<p align="center">
  <sub>Every assumption is tagged: <strong>FACT</strong> (verified) · <strong>CONVENTION</strong> (inherited) · <strong>GUESS</strong> (untested)</sub>
</p>

**Modes**

<p align="center">
  <img src="assets/three-modes.jpg" alt="Decide, Explain, and Hybrid modes" width="100%">
</p>

<p align="center">
  <sub><strong>Decide</strong> · <strong>Explain</strong> · <strong>Hybrid</strong></sub>
</p>

- **Decide** (default) — pressure-test a plan, design, cost, or claim.
- **Explain** — Feynman-style: primitives → one analogy (and where it breaks) → tiny example → check questions → one-liner.
- **Hybrid** — the decision, then a short explain of the non-obvious idea behind it.

Full procedure: [`skills/think-from-zero/SKILL.md`](skills/think-from-zero/SKILL.md).

---

## Who it's for

- Engineers tired of cargo-cult architecture and "everyone uses X"
- Builders making **build vs buy**, pricing, and stack decisions under uncertainty
- Anyone learning a hard topic who wants understanding, not vocabulary
- Teams that want agents to **recommend and test**, not hedge forever

---

## Share it

If this changes how you (or your agent) decide, a star helps others find it.

```text
Stop reasoning by analogy.
github.com/yuvraaj2002/think-from-zero
```

Useful one-liners for posts:

- *"Most AI answers inherit the crowd's assumptions. This skill makes them rebuild from bedrock."*
- *"First principles as an Agent Skill — Decide, Explain, or Hybrid. Always ends with an answer and a cheapest test."*
- *"`npx skills add yuvraaj2002/think-from-zero` — then ask: is this overengineered?"*

---

## Repo layout

```text
think-from-zero/
├── skills/think-from-zero/
│   ├── SKILL.md              # the skill (install this folder)
│   └── references/
│       └── examples.md       # engineering · product · career walkthroughs
├── assets/
│   ├── think-from-zero-banner.png
│   ├── analogy-vs-bedrock.jpg
│   ├── calibrated-effort.jpg
│   ├── method-flow.jpg
│   ├── assumption-tags.jpg
│   └── three-modes.jpg
├── RESOURCES.md              # lectures, essays, books, prior art
├── README.md
└── LICENSE
```

---

## Further reading

The videos, essays, books, and prior-art skills behind this method — Feynman, Hamming, Musk's battery teardown, Farnam Street, and more — are listed in [RESOURCES.md](RESOURCES.md).

---

## Contributing

Contributions are welcome.

- **Bad reasoning?** Open an issue with the prompt, the output, and what a good answer looks like.
- **Improving the skill:** keep `SKILL.md` concise (well under 500 lines), model- and tool-agnostic, and follow the [Agent Skills spec](https://agentskills.io/specification).
- **New examples or variants:** add them under `skills/think-from-zero/references/` and link from `SKILL.md` — don't bloat the core file.
- Keep PRs small. Explain the *why*. From first principles, of course.

---

## License

[MIT](LICENSE) © 2026 [Yuvraj Singh](https://github.com/yuvraaj2002)

<p align="center">
  <sub>Reason from what is true. Rebuild. Then decide.</sub>
</p>
