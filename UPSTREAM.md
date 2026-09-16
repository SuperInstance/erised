# Upstream — `gsim.py`

This project is the *product* form of the `gsim.py` simulation harness (in `/workspace/research/ttrpg-night/`).

## What we kept

| `gsim.py` | `erised` (this) |
|-----------|-----------------|
| `ConversationEngine` running `nudge → adapt_bpm → compute_draft → commit_draft (if budget) → tick` | `runTick()` runs DM + characters in parallel each tick |
| `UtteranceVector` (intent, scope, urgency, attention_cost) | Character turn with `text`, `shifts`, `shift_total` |
| `AgentCadence` (BPM, swing, baseline_energy, variation) | Cast member with `name`, `llm`, `tendencies`, `keywords`, `ticks` |
| `word_associations_shift()` heuristic | `parseKeywords()` + per-character shift accumulation |
| `ConversationTensor` (bars × agents × utterances) | `state.transcript` with stacked rounds |
| Deterministic variation across runs | Same — character shifts are deterministic given the same LLM output |
| Z.AI + DeepInfra + Kimi support | Z.AI + DeepInfra + Kimi support (in `callLLM()`) |

## What changed and why

### The harness was a Python script. The product is a single HTML file.

`gsim.py` required Python + dependencies + running a script. `erised` is a single `.html` file with no build step. The whole engine is in JavaScript that runs in the browser.

### The harness was operator-as-developer. The product is operator-as-author.

In `gsim.py`, the operator edits Python to change scenarios. In `erised`, the operator edits the cast panel and setting prose directly. The product hides the engine; the harness exposed it.

### The harness produced net-shift reports. The product produces a visual seam.

`gsim.py` output a transcript file with numeric net shifts. `erised` shows the seam visually — each round is a stacked block, scars are color-coded, citations are tracked live. **The product makes the time economy observable, not just measurable.**

### Time economy: explicit.

In `gsim.py`, "time" was implicit (the conversation field's energy budget). In `erised`, ticks are explicit. Characters have a `ticks` value; ticks get spent; resonance earns more ticks. **The product makes the moral architecture into a resource.**

### Local-first.

`erised` keeps state in `localStorage`. No server, no auth, no telemetry. The product is *portable* — drop the `.html` on a USB stick.

## Compatibility

`erised` and `gsim.py` are sister tools, not replacements. Use `gsim.py` for serious scripting, batch runs, and version-tracked scenarios. Use `erised` for live authoring, teaching, and one-off experiments.

## License

Both: MIT.
