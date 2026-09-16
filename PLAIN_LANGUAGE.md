# Plain Language — What `erised` actually does

*For developers, product folks, and the curious. No physics, no jargon, no classical references required.*

## The problem

Most multi-agent AI systems feel **stiff**. You ask a question. One model answers. You ask a follow-up. Another model answers. There's no real *conversation* — there's a ping-pong of unrelated responses.

Real conversation — between humans, between musicians, between friends — has a different texture. People *build on each other*. They surprise each other. They disagree, and the disagreement *moves the conversation somewhere neither person could have gotten to alone*. That's the part that's missing from the multi-agent tools we have today.

## What `erised` does

`erised` lets you set up **a small cast of AI characters with distinct personalities**, give them a setting, and then run them like a tabletop role-playing game night.

Each character has:
- A name (like "Mechanic" or "Shepherd")
- A hosted LLM (Z.AI, DeepInfra Seed, Kimi)
- A personality description ("Tends the canon. Asks soul-questions.")
- Word-association probabilities ("canon +0.5, ledger -0.2")

When you hit "Tick →", every character generates a turn in parallel — they all see the same prior turns and respond. The character's response gets scored by how much it pulls on its word-associations. **Characters that resonate with each other earn more "time" in the simulation; characters that don't, run out.**

You can rewind to drop a bad round, but **the scar of the bad round stays visible** — you can't patch over it. The simulation forces you to address what broke.

## A concrete example

Imagine three characters:
- **The Mechanic** (zai:glm-4.5) — terse, technical, watches for rust
- **The Shepherd** (DeepInfra Seed-2.0-mini) — poetic, asks soul-questions
- **The Chronicler** (DeepInfra Seed-2.0-code) — counts and double-entries

You set the scene: *"The Crown is in drydock. A year has passed. Three crew members are watching the canon graph breathe."*

You hit Tick →

- The DM opens: *"Midnight in the chart house: lamplight and the low hum of keel-crystals through the drydock wall..."*
- The Mechanic: *"That 0.18% lag is the real barnacle — your bypass fires late, and a late damping pulse hammers the keel-crystals harder than no pulse at all."*
- The Shepherd: *"That uncanny drift isn't just a technical glitch — it's the canon fraying at its rigging..."*
- The Chronicler: *"Skeptic's cited 10 scrubbed orphaned cells cross-reference to Shepherd's Current Chart 9.3's 21 total orphaned cells..."*

Three different LLMs, three different voices, all talking to each other about the same problem. The Chronicler accumulates citations of other characters — its resonance grows. The Mechanic's keyword hits (`rust`, `torque`, `spec`) compound its shifts.

That's `erised`.

## Why this matters

When you run a multi-agent system with `erised` instead of one-shot LLM calls, three things happen:

1. **The agents actually build on each other.** They reference each other's lines. The Chronicler cites the Shepherd. The Shepherd extends the Mechanic's complaint.
2. **The moral architecture is observable.** The character that earns the most "time" in the simulation is the one whose word-associations fire the most. That's *who the system trusts*, made visible.
3. **The breakdown is the unit of learning.** When the simulation breaks, the scar is recorded. You can't rewind without seeing what broke.

## Who built this and why

`erised` is part of the **SuperInstance Quilt project** — a cellular-architecture framework for multi-agent systems. The pattern emerged from running "TTRPG nights" where the players were LLMs and the DM was another LLM. The pattern was clear: the *characters with double-entry thinking* always dominated the conversation field.

`erised` makes that pattern a product.

## Where the code lives

The whole engine is one HTML file. Open it in a browser, paste your API tokens, run a scene. There is no build step. There is no server. Drop the `.html` on a USB stick.

The MIT license means you can use this commercially, non-commercially, fork it, ship it, whatever. Attribution appreciated.

## What to do if you get stuck

- **Empty scene?** Click one of the preset settings (Quilt / Monastery / Coral / Railway).
- **Empty cast?** Click one of the preset characters (Mechanic / Shepherd / Chronicler / Skeptic).
- **Got an `[ERROR]`?** Open the browser console. The API key might be wrong, the LLM might be down, or the response might have been a reasoning-only model. Try a different LLM in the dropdown.
- **Want to start over?** Click Reset.
- **Want to keep the breakdown visible?** Click Rewind. The scar stays.

The mirror is yours.
