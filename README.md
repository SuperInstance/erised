# erised

> *desire reversed.*

**A mirror for cooperative fiction — model-only TTRPG engine.**

You author the conditions: state, cadence, cast, setting. The fiction plays itself. Power is given, not taken. Time is finite; resonance earns more.

A single-file HTML app. Open in a browser. Plug in your Z.AI and DeepInfra API tokens. Run a scene.

---

## What it does

`erised` runs a model-only cooperative fiction. Each round:

1. **DM opens** (round 1) or **continues** (subsequent rounds) the scene
2. **All characters respond in parallel** — each calls its assigned LLM
3. **Word-association shifts accumulate** per character
4. **Citations are tracked** — every reference to another character compounds resonance
5. **Scars are recorded** — broken turns become visible artifacts
6. **Operator can rewind** — last round drops, but the scar persists

The character with the highest cumulative net shift has the most resonance in the field. The character with the fewest citations has the most to gain.

---

## Quick start

1. Download `index.html` and open in any modern browser
2. Paste your `ZAI_TOKEN` and `DEEPINFRA_TOKEN` when prompted (saved in `localStorage`)
3. Pick a preset setting (Quilt / Monastery / Coral / Railway)
4. Edit the cast if needed
5. Hit **Tick →** to start

The DM opens the scene. Each subsequent tick runs all characters in parallel.

---

## Cast & sheets

Each character has:
- **name** — what they're called in the fiction
- **LLM** — which hosted model (Z.AI glm-4.5 / DeepInfra Seed-2.0-mini / Seed-2.0-code / Kimi-K3)
- **tendencies** — the prose that defines their character
- **keywords** — `word+0.5, word-0.2, ...` (word-association probabilities)
- **ticks** — initial time budget (default 20; resonance earns more)

The shift on a keyword fires every time that word appears in the character's turn. Net shift accumulates across rounds.

---

## Time economy

- Each character starts with `ticks` (default 20).
- Tick is spent when the character produces a turn.
- Resonance earned (positive net shift from keywords) is **converted to more ticks** (1 tick per +1.0 shift, floored).
- Characters with low influence run out of ticks first. **High influence compounds.**
- Out-of-ticks characters become *off-screen* — they exist but can't act.

This is the inverse of every prestige economy. Hoarded ticks are nothing; **resonance ticks compound**.

---

## Resonance graph

Every round, citations accumulate. When a character references another character by name (full name or first name, length ≥ 3), it's a citation.

The resonance graph lives in the right panel. The most-cited cells earn the most long-term stability.

---

## Scars & rewind

When a character errors out, runs out of ticks, or the simulation breaks down, **the scar is recorded**. You can rewind to drop the last round — but the scar stays visible. **You can't patch over it.** The next iteration has to address it.

This is the unit of learning. The simulation makes the breakdown visible.

---

## Cite / fork / extend

The whole engine is in `index.html`. No build, no deps, no network state. Drop it on a USB stick and run it offline.

Three extension surfaces:
- **Presets** — `PRESETS` and `SETTINGS` dicts at the top of the script
- **LLM backends** — `callLLM()` — add new providers by extending the dispatch
- **Citation detection** — `updateCitations()` — currently regex-based; could go semantic

---

## Lineage

`erised` was born from the **gsim.py** simulation harness (Sept 16 2026). The early form ran 3-character nights in maritime-fantasy settings — monastery, coral reef, railway. The pattern was clear: the Counter/Witness/Watcher character always accumulated the highest net shift. The metaphor changed the ethics but not the dynamic.

`erised` is the *product* form. The harness was the experiment; this is the canvas.

---

## Cave / Stone / Mirror

The name carries three references:

- **Plato's cave** — the cell as first-person spatial observer. Each character sees the world from their position; their perspective is spatial, not abstract.
- **The philosophers' stone** — transmutation through resonance. What the system produces isn't just simulation; it's transformation of the operator.
- **The Mirror of Erised** — shows the heart's desire. The fiction reveals what the operator was reaching for, before they could articulate it.

Open-source. MIT. Pluggable. Model-agnostic.

The mirror is yours.
