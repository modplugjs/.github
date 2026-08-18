# modplay.js

# 🚧 Work in progress

modplay.js is still being built. It is in the planning phase and nothing is playable yet. There are no releases and no npm package — expect this to change as the project matures.

| Area | Status |
|---|---|
| Planning & architecture | 🔄 in progress |
| Core (the manager) | ⬜ not started |
| Format plugins (MOD, S3M, XM, IT) | ⬜ not started |
| Effect (sound) plugins | ⬜ not started |
| Output plugins (Web Audio, PCM/WAV) | ⬜ not started |
| Fidelity verification | ⬜ not started |

---

## What is this?

modplay.js is a browser library that **parses and plays classic tracker module files** — the `.mod`, `.s3m`, `.xm`, and `.it` formats from the tracker era — with sound that is as close as possible to the original trackers.

It gives you:

- Load a tracker module file in the browser
- Hear it played back with near-reference accuracy
- Audio delivered through modern Web Audio (AudioWorklet) or as raw PCM / WAV data

## How it is built (in plain words)

The library is **fully modular** — everything plugs into a small core:

- **Core** — the manager. Loads a module, runs the playback loop, holds the samples (and can swap samples in while playing).
- **One plugin per format** — each tracker format (MOD, S3M, XM, IT) is its own plugin that teaches the core how to read that format.
- **One plugin per effect** — each sound effect (echo, reverb, filter, …) is its own plugin.
- **One plugin per output** — where the sound goes: Web Audio in the browser, or raw PCM/WAV data.

New formats, effects, or outputs can be added as plugins without touching the core.

## Fidelity

Parsing and playback target **near-perfect accuracy** against the reference implementations:

- [OpenMPT](https://www.openmpt.org/)
- [libxmp](https://libxmp.github.io/)
- Paula Tracker

No simplified or guessed behavior — every effect is ported from the reference source code.

## Roadmap (v1)

1. Planning & architecture
2. Core + first format (MOD) playable end-to-end
3. Remaining formats (S3M, XM, IT)
4. Shared effects package (effects used by all four formats)
5. Paula-sound effect plugin (the first ported effect)
6. Web Audio + PCM/WAV outputs
7. Fidelity verification against reference renders

## Not in v1

- Other tracker formats (MTM, 669, MED, …)
- GUI / tracker editor
- npm publishing (local use only for now)
- Node.js output (the core stays platform-neutral, though)

## License

TBD — not decided yet for this project.

The reference projects are all permissively licensed, so porting from them carries no copyleft obligations:

- **OpenMPT** — BSD-3-Clause
- **libxmp** — MIT (Copyright (C) 1996-2026 Claudio Matsuoka and Hipolito Carraro Jr)
- **Paula Tracker** — MIT
