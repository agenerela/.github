## Agenerela — AI agents for Unity

Let a language model drive game agents — NPCs, companions, factions, colonies —
**constrained to actions you explicitly register.** The model picks a behaviour;
validated, deterministic game code carries it out. Local-first with
[Ollama](https://ollama.com), with a provider interface for cloud backends.

### Why

Wiring a model into a game is not the hard part. Making its output *safe to execute* is.

In prototype measurements, a 2B local model chose the correct game action **58.5%** of the
time when the rules lived in the prompt. With a state-derived schema, constrained sampling
and a deterministic validation layer, the same model reached **95%**, and beat a 4B model
that had none of that scaffolding.

**The scaffolding is the framework. The model is a swappable part.**

### How it stays safe

- Illegal actions and unknown targets are **removed from the sampling grammar**, so the
  model cannot emit them.
- The executor **re-validates every choice independently**, so a provider without
  constrained decoding is still contained.
- The model never touches Unity. It chooses; your code acts.

### Status

Early development, not yet ready to drop into a game. The framework is being built phase
by phase from that measured prototype.

- **[agenerela/agenerela](https://github.com/agenerela/agenerela)** — the framework
- **[Build plan](https://github.com/agenerela/agenerela/blob/HEAD/docs/FRAMEWORK_BUILD_PLAN.md)** —
  architecture, phases, and the evidence behind each design decision
- **[Design](https://github.com/agenerela/agenerela/tree/HEAD/docs/design)** — what a
  developer and a player will see, screen by screen
- **[Contributing](https://github.com/agenerela/agenerela/blob/HEAD/CONTRIBUTING.md)** —
  how to open a pull request

---

Senior design project, California State University, Northridge — COMP 490 / 491.
