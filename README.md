# Fancy Ape — The Reset

A free, voice-first self-reflection and guided-relaxation web app. First session: **The Throttle** (30 min default).

**Live prototype:** open `index.html` in a browser, or enable GitHub Pages (Settings → Pages → Deploy from branch → `main` / root).

## What it does
1. **Speak** — talk or type about what's on your mind.
2. **Reflect** — the app sorts it into what happened, what you believe it means, and what isn't known, and asks one question that tests the story. You can correct it.
3. **Choose** — pick today's objective and edit your phrase.
4. **Listen** — a continuous spoken session: breathing, attention at the solar plexus, watching thoughts, holding the story loosely, your phrase, extended silence, gentle return.
5. **Integrate** — say what you noticed and leave with one small action.

Pause/resume, Mute, adjustable length (10–60 min), loop, emergency stop, live transcript. You choose the voice (up to six from your device, each with a sample), narration volume, optional soft background sound, and an optional 200/206 Hz tone pair (6 Hz difference, headphones).

## Requirements
- A modern browser. Voice input needs Chrome or Safari; typing works everywhere. In Chrome, voice input may be processed by the browser vendor; typing avoids this.
- Spoken guidance uses the device's built-in voices, so the choices differ between phones and computers. Better voices can often be added in your device's language or accessibility settings.
- **AI reflection runs only inside claude.ai** (it uses the Claude artifact runtime). Hosted elsewhere, including GitHub Pages, the app falls back to a general reflection and script. Everything else works.

## Privacy
- Words are sent to Claude only when you tap *Reflect it back*, *Try again*, or *Find one thing to carry forward* (claude.ai only). *Skip to a session* sends nothing and ignores anything typed.
- The session log (ratings, objective, action) is stored in your browser only. Your words are saved only if you turn that on. *Delete everything* wipes it.
- No accounts, no analytics, no server.

## What this is not
A guided self-reflection and relaxation exercise. Not therapy, not medical care, not a diagnostic tool. It can misread you. The tone is an optional sound preference; no effect is promised.

## Status
Prototype v0.2.2 · FA-RESET-001 · Gate B (prototype) → Gate C (founder testing). See `docs/`.

## License
Code: MIT (see `LICENSE`). Documents in `docs/`: CC BY-SA 4.0.

The Composition Group LLC · Fancy Ape
