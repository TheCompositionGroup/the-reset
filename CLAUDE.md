# CLAUDE.md

THE RESET (Fancy Ape, FA-RESET-001) is a private, sound-only app: turn a dial to one of seven frequency stops, pick a time, press play, listen. It is a prototype, not clinically validated. v0.3.0 replaced the earlier voice-first reflection app; `docs/concept-paper.md` describes that earlier version and is not current. Test protocol: `docs/test-plan.md`.

These rules apply to every change to `index.html`, `README.md`, and `docs/`. If a request conflicts with a rule, say so and ask before proceeding.

## Rules

### 1. No medical or "reprogramming" claims
- The app is a sound experience. It is not therapy, diagnosis, treatment, or a crisis line.
- Never write or generate: heal, cure, treat, therapy/therapeutic effect, reprogram, rewire, subconscious, "brain frequency", "healing frequency", "balance your chakra", "open your chakra", "activate your chakra", or any promised outcome. This covers UI copy, README, changelog, and anything else shown to a person. The one allowed use of "therapy" is the footer disclaimer ("Not therapy or medical care").
- The frequencies and chakra names are modern wellness associations, not proven effects. The ring words (Ground, Flow, Power, Heart, Voice, Vision, Stillness) are names for the stops, not claims about what they do. Never write that a stop causes, improves, or helps anything.
- The footer must stay visible on every screen, word for word: "A sound experience. Not therapy or medical care. Frequency and chakra pairings are modern wellness associations, not proven effects. Nothing is promised."
- Better / Same / Worse is a person's own tap, not evidence. No public effectiveness claims until independent review (Gate D).

### 2. Gentle sound, no forced breathing
- The volume swell (in 4 s, out 6 s) and the glow are a quiet pacing cue only. Never add breath counts, holds, hyperventilation, rapid or forced cycles, or any instruction to push past discomfort.
- Volume starts at 25% on first visit (the person's level is remembered after). Master gain never exceeds 0.6 at 100% on the slider. No sudden peaks, bells, or alarms.
- Fades only: 5 s in on Play, 8 s out at natural end, 0.3 s on Stop and Escape. Stop and Escape always work immediately. Pause holds in place.
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
- One screen: dial, readout, time, sound type, volume, Play. Copy stays minimal. The end screen appears only after a natural completion, never after an early Stop.
- The answer counts are shown as they are. Never hide or soften a "Worse" count.
- Stop signal: when 3 or more of the last 12 saved sessions are "Worse", a quiet notice shows on the dial screen and the end screen. It has no dismiss button and is never softened or hidden. Only answered sessions are saved, so only they count.

## Known limits (v0.3.0)
- Audio, haptics, and wake lock have been tested in headless Chromium only. Real phone speakers, headphones, and iOS/Android behavior need a person on a device.
- Sound may stop when a phone screen locks; the screen wake lock helps but is not guaranteed.
- Phone speakers reproduce little below about 200 Hz, so the Atmosphere octave-below layer may be inaudible there.

## Editing checklist
- Grep user-facing text for the banned terms in Rule 1 before committing.
- Confirm no `http(s)://`, `fetch`, XHR, WebSocket, external `src`/`href` in `index.html`.
- Confirm nothing but stop, time, sound, volume, and the answer log is stored.
- Update `CHANGELOG.md` for any behavior change.
- Test sound, fades, and haptics on a real phone before merging anything that touches audio.
