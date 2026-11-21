# Resources

These are the videos, essays, books and prior work behind `think-from-zero`. Each one notes the part of the skill it shaped, so you can go deeper on whatever part you find most useful.

## Videos & lectures

- [What is "First Principles Thinking"?](https://www.youtube.com/watch?v=HOj67-WNYRU) by **Abhijit Chavda**: a clear, short introduction to the idea. It shaped the plain-language framing at the top of the skill.
- [Elon Musk and Kevin Rose](https://www.youtube.com/watch?v=L-s_3b5fRd8) (Foundation, 2012) with **Elon Musk and Kevin Rose**: the well-known "reason from first principles rather than by analogy" explanation and the battery-cost teardown (around 22:35). This is the source of the "Reduce to fundamental truths" step and the cost-breakdown style of reasoning.
- [BBC Horizon: The Pleasure of Finding Things Out (1981)](https://www.youtube.com/watch?v=7XA_NVn7XnE) with **Richard Feynman**: covers knowing the name of something versus understanding it, and being comfortable with uncertainty. It informed Explain mode and the confidence levels in the answer.
- [The complete Fun to Imagine with Richard Feynman](https://www.youtube.com/watch?v=P1ww1IXRfTA) (BBC, 1983) with **Richard Feynman**: explains physics from everyday things (jiggling atoms, rubber bands, mirrors). It's the model for "build up from primitives, one plain analogy, then say where it breaks". It's also on the [BBC programme page](https://www.bbc.co.uk/programmes/p0198zc1).
- [Hamming, "You and Your Research" (June 6, 1995)](https://www.youtube.com/watch?v=a1zDuOPkMSw) by **Richard Hamming**: work on the right problem in the right way, and hold beliefs firmly enough to act on but loosely enough to notice when they're wrong. It shaped "Restate the real goal" and "Would change my mind".

## Articles & essays

- [What is First Principles Thinking?](https://fs.blog/first-principles/) from **Farnam Street (Shane Parrish)**: covers Socratic questioning and the Five Whys as practical tools. It informed how the skill questions assumptions ("Why is it believed? What if it's false?").
- [First Principles: Elon Musk on the Power of Thinking for Yourself](https://jamesclear.com/first-principles) by **James Clear**: identify and question assumptions, then build new solutions. It shaped the steps from assumptions to rebuild.
- [The Cook and the Chef: Musk's Secret Sauce](https://waitbutwhy.com/2015/11/the-cook-and-the-chef-musks-secret-sauce.html) by **Tim Urban (Wait But Why)**: the "chef" reasons from raw ingredients while the "cook" follows recipes. It's the basis for comparing your answer with the conventional approach.
- [How to Think for Yourself](https://paulgraham.com/think.html) by **Paul Graham**: on independent-mindedness and when being right means being unconventional. It informed the warning against plain contrarianism.
- [Richard Hamming: You and Your Research](https://paulgraham.com/hamming.html) (1986 Bellcore talk transcript) by **Richard Hamming**: the readable version of the talk above, about focusing on important problems.
- [Cargo Cult Science](https://calteches.library.caltech.edu/51/2/CargoCult.htm) (Caltech commencement, 1974) by **Richard Feynman**: "The first principle is that you must not fool yourself". It's behind the sanity checks, counterexamples and honest confidence levels.

## Books

- [The Feynman Lectures on Physics](https://www.feynmanlectures.caltech.edu/) (free online edition) by **Richard Feynman, Robert Leighton and Matthew Sands**: the classic example of explaining from fundamentals, and a model for Explain mode.
- ["Surely You're Joking, Mr. Feynman!"](https://wwnorton.com/books/Surely-Youre-Joking-Mr-Feynman) by **Richard Feynman (with Ralph Leighton)**: Feynman's habit of checking everything himself, which shaped the "Gather before you reason" and "observe, don't trust" debugging advice.
- [How to Solve It](https://press.princeton.edu/books/paperback/9780691164076/how-to-solve-it) by **George Polya**: understand the problem, make a plan, carry it out, look back. Its heuristics (work backward, solve a simpler problem) informed the workflow and the sanity-check step.
- [Thinking in Systems](https://www.chelseagreen.com/product/thinking-in-systems/) by **Donella Meadows**: feedback loops, delays and leverage points. It informed the reminder to think about second-order effects and switching cost before rebuilding.
- [The Art of Doing Science and Engineering](https://press.stripe.com/the-art-of-doing-science-and-engineering) by **Richard Hamming** (Stripe Press): on learning to learn, order-of-magnitude thinking and style in engineering. It informed the learning variant and the Fermi checks.

## Agent-skill format & prior art

- [Agent Skills specification](https://agentskills.io/specification) from **agentskills.io**: the open `SKILL.md` standard (`name` and `description` frontmatter, progressive disclosure, keep files under 500 lines). This skill follows it.
- [Agent Skills: Cursor Docs](https://cursor.com/docs/context/skills) from **Cursor**: skill directories (`~/.cursor/skills/`, `.cursor/skills/`, `.agents/skills/`), frontmatter fields and `/skill-name` invocation.
- [Extend Claude with skills](https://code.claude.com/docs/en/skills) from **Anthropic (Claude Code docs)**: personal (`~/.claude/skills/`) and project skill locations, and writing descriptions that trigger reliably.
- [anthropics/skills](https://github.com/anthropics/skills) from **Anthropic**: the public reference repo for Agent Skills, and the source of the `skills/<name>/SKILL.md` layout used here.
- [deciqAI/knowledge-skills: first-principles](https://github.com/deciqAI/knowledge-skills/blob/main/first-principles/SKILL.md) by **deciqAI**: a strong seven-step teardown with BEDROCK/INHERITED tags. It inspired the assumption tagging and "stop at bedrock".
- [ysskrishna/ai-agent-skills: first-principles-thinking](https://github.com/ysskrishna/ai-agent-skills/blob/main/skills/first-principles-thinking/SKILL.md) by **ysskrishna**: "gather first", a light path and treating tool output as evidence. All three shaped the effort calibration and evidence rules here.
- [tjboudreaux/cc-thinking-skills: thinking-first-principles](https://github.com/tjboudreaux/cc-thinking-skills/blob/main/skills/thinking-first-principles/SKILL.md) by **tjboudreaux**: part of a collection of Claude Code thinking skills, and a useful reference for concise skill design.
- [shanezzzz/first-principles-skill](https://github.com/shanezzzz/first-principles-skill) by **shanezzzz**: hard vs soft constraints vs assumptions, ending with an experiment. It influenced the "Cheapest test" line.
- [ntguion/first-principles-skill](https://github.com/ntguion/first-principles-skill) by **ntguion**: a conventional baseline vs derived alternatives, and the point that safety, law and ethics are constraints, not assumptions. Both ideas are adopted here.

---

Know a great resource that belongs here? Open a PR and add it under the right heading with a one-line note on why it matters.
