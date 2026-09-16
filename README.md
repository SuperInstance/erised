# erised — Mirror for cooperative fiction

> *desire reversed*

The HTML canvas for running cooperative fiction in your browser. Set the cadence, the cast, the setting. Hit tick. The fiction plays itself.

**Live**: [superinstance.ai/erised](https://superinstance.ai/erised)
**Companion CLI**: [github.com/SuperInstance/erised-cli](https://github.com/SuperInstance/erised-cli)

## What it does

- Single-file HTML (733 lines, no build step, no deps)
- Each character has its own LLM (Z.AI glm-4.5, DeepInfra Seed-2.0-mini, Kimi K3, etc.)
- Each character has its own ticks (time budget) and resonance (positive net shift from keywords)
- The DM (a separate LLM) opens and closes each scene
- **Time economy**: ticks are spent on each turn. Resonance earns more ticks. Hoarded ticks = nothing.
- **Scars**: when a character errors or runs out of ticks, the scar is recorded. Rewind drops the round, but **the scar persists**.

## Three forms of erised

| Form | Repo | What it's for |
|------|------|---------------|
| **Canvas** (HTML) | this repo | live authoring, teaching, one-off experiments |
| **Headless** (CLI) | [erised-cli](https://github.com/SuperInstance/erised-cli) | servers, CI, batch scripting, embedding |
| **Cells** (.erised/ dir) | [erised-cli/erised-cell](https://github.com/SuperInstance/erised-cli/blob/main/CELL.md) | per-scenario lineage + run history |
| **Engine** (Rust) | [quilt-conversation](https://github.com/SuperInstance/quilt-conversation) | the timing layer between agents |

## The Winners — read the corpus

The engine only matters if there are runs to read. We have a corpus.

**[superinstance.ai/winners](https://superinstance.ai/winners)** — every scenario run, three versions, with iterated cast keywords. The current corpus has 24+ runs across 8+ scenarios (apiaries, lighthouses, orchestras, orchards, radio stations, libraries, ice rinks, root cellars).

Each scenario in the corpus is a setting where a small crew sustains a growing system past its first year. Each version (v1, v2, v3) plays the same scenario with slightly mutated cast keywords — the **iterative refinement** you see is what happens when the dilemma plays itself through different drifts.

## Quick start

1. Open `index.html` in any browser
2. Click "Tokens" and paste your `ZAI_TOKEN` and `DEEPINFRA_TOKEN`
3. Hit the **Tick** button. Watch the cast speak.

No server. No build. No login. The state lives in your browser's localStorage.

## Run it from the terminal

```bash
git clone https://github.com/SuperInstance/erised-cli
cd erised-cli
./erised --init > my-scenario.json
# edit, then:
./erised my-scenario.json --rounds 4
```

## Run it as a cell (with lineage)

```bash
./erised-cell init examples/apiary.json
./erised-cell run
./erised-cell ls
./erised-cell diff <run1> <run2>
```

## The cohort

The erised-cli ships 10 scenarios in `examples/`:

- `quilt-12mo.json` — The Quilt project, 1 year out
- `quilt-100yr.json` — The Quilt project, 100 years out
- `monastery.json` — A monastery of cells, scripture as living document
- `fract-canon.json` — A library whose catalogue mis-cites itself
- `monorail.json` — A rail car with no operator
- `coral-atoll.json` — Floating research station over a transplant
- `apiary.json` — A beekeeper's legacy
- `root-cellar.json` — A communal cellar with a blight
- `patron-library.json` — Books written by the patrons
- `quick-test.json` — 2-character budget test

**[Browse all 10 →](https://superinstance.ai/scenarios)**

## License

MIT.
