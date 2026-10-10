# The Security Dictionary: Trail Edition 🌿

Cybersecurity, learned outside. An offline tool that turns security concepts
into kid-friendly outdoor missions — so the phone goes in your pocket and the
learning happens in the real world.

Built for the [Hacktoberfest 2026 Open-Source AI Challenge, Week 1: Touch Grass](https://dev.to/challenges/hacktoberfest-week1-2026-10-05).

A branch of [The Security Dictionary](https://www.datasecchronicles.com) by DataSec Chronicles.

## What it does

Pick an explorer age, a place, and how long you've got. The tool gives you a
security concept framed as a mission you do outside:

- **IOC** → *find three clues something was here before you*
- **Alert** → *notice what grabs your attention*
- **Firewall** → *find barriers that let some things through and keep others out*
- **Encryption** → *invent a secret signal only you and a friend understand*
- **Phishing** → *spot something tempting — feel the pull, but don't go to it*

A warm voice reads the mission aloud, so a child can listen instead of read,
pocket the phone, and go. The definition comes *after* the experience.

Each mission comes in three reading levels (ages 5–7, 8–10, 11–13).

## How it's built

- **Local open-weight model — Google Gemma (via [Ollama](https://ollama.com), `gemma2:2b`).**
  Every mission is generated locally. The same security concept becomes a fresh,
  age-appropriate mission each time — something a static list of scavenger hunts
  can't do. The missions are generated once and baked into the page so it runs
  with no model server and no internet.
- **Voice — [ElevenLabs](https://elevenlabs.io).** Narration is pre-generated and
  embedded in the page, so it plays offline once loaded. Voice isn't decoration
  here: requiring a child to *read* generated instructions would undermine the
  whole premise. The interface needed to disappear.
- **The page** is a single self-contained HTML file. No build step, no framework.

See [`prompts/`](prompts/) for the exact prompt template and concept lines used
to generate the missions — including the safety constraints that keep generated
output appropriate for children.

## Why open innovation matters

- **It runs offline.** On a trail, in a backyard, anywhere with no signal.
- **No child's data leaves the device.** A kids' tool built on a cloud API would
  send a child's inputs to someone else's server. Running the model locally means
  it never has to. For a tool aimed at children, that isn't a convenience — it's
  the reason it can be trusted.
- **It costs nothing to run**, so any family or classroom can use it.

## Safety

Every mission is observation-only. The model is explicitly constrained to never
tell a child to touch, taste, chase, approach anything unfamiliar, enter unsafe
areas, identify or eat plants, or leave their adult's area. The constraint is
part of the project's identity, shown on every mission as **Trail Rules: Look.
Listen. Notice.**

## Run it

Open `index.html` in any browser. That's it — no install, no server.

To regenerate or extend the missions, install [Ollama](https://ollama.com),
pull a Gemma model (`ollama pull gemma2:2b`), and feed it the template in
[`prompts/mission-template.txt`](prompts/mission-template.txt).

## Status

v1, built for Hacktoberfest 2026. Field-tested outdoors with a kid in the target
age range (it worked — and it got us outside). Next: real voice across all three
age tiers, not just 8–10.

---

Made with 💜 by [DataSec Chronicles](https://www.datasecchronicles.com) ·
*The tool changes, the question doesn't.*
