# CLAUDE.md

THE RESET (Fancy Ape, FA-RESET-001) is a private, sound-only app: turn a dial to one of seven frequency stops, pick a time, press play, listen. It is a prototype, not clinically validated. v0.3.0 replaced the earlier voice-first reflection app; `docs/concept-paper.md` describes that earlier version and is not current. Test protocol: `docs/test-plan.md`.

These rules apply to every change to `index.html`, `README.md`, and `docs/`. If a request conflicts with a rule, say so and ask before proceeding.

## Rules

### 1. No medical or "reprogramming" claims
- The app is a sound experience. It is not therapy, diagnosis, treatment, or a crisis line.
- Never write or generate: heal, cure, treat, therapy/therapeutic effect, reprogram, rewire, subconscious, "brain frequency", "healing frequency", "balance your chakra", "open your chakra", "activate your chakra", or any promised outcome. This covers UI copy, README, changelog, and anything else shown to a person. The only allowed uses are the footer disclaimer ("Not therapy or medical care") and the cited book title in "Where the frequencies come from".
- The frequencies and chakra names are modern wellness associations, not proven effects. The ring words (Ground, Flow, Power, Heart, Voice, Vision, Stillness) are names for the stops, not claims about what they do. Never write that a stop causes, improves, or helps anything.
- Never describe a frequency as the natural resonance of a body part or organ. Never call a frequency "healing", "balancing", or "activating".
- Each stop is three separate things, and copy must keep them apart: **acoustics** (the real frequency in Hz, a fact about the sound), **symbolism** (the modern chakra pairing, a cultural association), and **intention** (the ring word, an interpretive theme, not an effect).
- The footer must stay visible on every screen, word for word: "A sound experience. Not therapy or medical care. Frequency and chakra pairings are modern wellness associations, not proven effects. Nothing is promised."
- Better / Same / Worse is a person's own tap, not evidence. No public effectiveness claims until independent review (Gate D).

### 2. Gentle sound, no forced breathing
- The volume swell (up 4 s, down 6 s) and the glow are a rhythm, not a breathing technique or treatment. Never add breath counts, holds, hyperventilation, rapid or forced cycles, or any instruction to push past discomfort.
- Volume starts at 25% on first visit (the person's level is remembered after). Master gain never exceeds 0.6 at 100% on the slider. No sudden peaks, bells, or alarms.
- Fades only: 5 s in on Play, 8 s out at a timed end, 0.3 s on Stop (timed) and Escape, about 0.45 s on Pause, 8 s on Stop for ∞. Stop and Escape always work immediately; a second Stop press during the ∞ fade ends it at once. Pause holds in place.
- Don't assume every device reproduces every frequency or harmonic equally.
- Respect `prefers-reduced-motion`: the glow stays still and the needle does not animate. Only visuals stop; sound and the Android breath pulses are unchanged.

### 3. No user text, so no crisis detection
- The app collects no user text: no typing, no microphone, no transcripts. Therefore there is no crisis detection and no 988 notice.
- If any text input is ever added back, the v0.2.2 crisis rules return with it, all together: the `crisisRe` keyword check (including the bare `suicid` stem and the indirect phrasings), the stated-intent threshold for any model flag, the quiet dismissible 988 notice, and the fixed phrase test. The full rules, regex, notice text, prompt line, and phrase list are in `docs/crisis-rules.md`.

### 4. Nothing leaves the device
- No network calls at all: no `fetch`, XHR, WebSocket, beacons, web fonts, CDN, analytics, telemetry, trackers, or accounts.
- Storage is `localStorage` on this device only, under `reset3:` keys: stop, time, sound, volume, and the answer log. Each log entry is ordered and dated: the stop, the minutes, Better/Same/Worse, and the date and time. Nothing else is saved, and there is no text field to save from.
- Delete all (with confirmation) removes the log, including any data left by v0.2 under `reset:` keys. Never delete a person's data silently.

### 5. One self-contained `index.html`
- The app stays a single `index.html`: inline CSS and JS, no build step, no framework, no bundler, no separate asset files, no external script, no external CDN.
- Must work offline once loaded. If Web Audio is unavailable, say so plainly and disable Play.
- Audio is generated in-page with Web Audio. Do not embed or fetch audio files.
- GitHub Pages serves it from `main` / root. Keep `index.html`, `README.md`, `LICENSE`, `CHANGELOG.md`, and `docs/` at the repo root.

### 6. Readable and reachable
- Minimum text size 13 px everywhere, including the footer. Every control has a tap target of at least 44 px, including each ring label.
- The dial is `role="slider"` with `aria-valuetext` such as "528 hertz, solar plexus, power", and works with arrow keys, Home, End, drag, and tapping a ring label. Check layouts at 320, 360, and 390 px.

## Product principles to preserve
- Calm instrument panel: thin tick marks, a needle, a soft glow when active. No steampunk, fake wear, or gimmicks.
- One screen: dial, readout, time, sound type, volume, Play. Copy stays minimal. The end screen appears only after a timed completion, or after stopping ∞ at 5 minutes or more, never after an early Stop on a timed session or Escape. ∞ plays until Pause or Stop and counts up; the log keeps the actual minutes played.
- Animate only opacity and transform. No animated blur, shadow, filter, or stroke, so cheap phones stay smooth. The glow takes the active stop's color.
- The answer counts are shown as they are. Never hide or soften a "Worse" count.
- Stop signal: when 3 or more of the last 12 saved sessions are "Worse", a quiet notice shows on the dial screen and the end screen. It has no dismiss button and is never softened or hidden. Only answered sessions are saved, so only they count.

## Where the frequencies come from
- 396, 417, 528, 639, 741, and 852 Hz are the modern Solfeggio set popularised by Joseph Puleo and Leonard Horowitz in *Healing Codes for the Biological Apocalypse* (1999). 963 Hz is a later addition. Nothing in this app claims these tones do what that book says.
- Hz-to-chakra pairings are modern. Traditional sources use bija (seed) sounds, not hertz.
- NCCIH, "Music and Health: What the Science Says", reviews research on music in general (for example relaxation and mood; the evidence is described as preliminary and mixed). It does not show frequency-specific effects. Better / Same / Worse in this app is a rough self-report and is never presented as proof that a frequency works.

## Known limits (v0.3.0)
- Audio, haptics, and wake lock have been tested in headless Chromium only. Real phone speakers, headphones, and iOS/Android behavior need a person on a device.
- Sound may stop when a phone screen locks; the screen wake lock helps but is not guaranteed.
- Phone speakers reproduce little below about 200 Hz, so the Atmosphere octave-below layer may be inaudible there, and quiet harmonics may be uneven on other devices.

## Editing checklist
- Grep user-facing text for the banned terms in Rule 1 before committing (the cited book title is the one allowed hit for "healing").
- Confirm no `http(s)://`, `fetch`, XHR, WebSocket, external `src`/`href` in `index.html`.
- Confirm nothing but stop, time, sound, volume, and the answer log is stored.
- Update `CHANGELOG.md` for any behavior change.
- Test sound, fades, and haptics on a real phone before merging anything that touches audio.
