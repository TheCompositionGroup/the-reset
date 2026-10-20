# CLAUDE.md

THE RESET (Fancy Ape, FA-RESET-001) is a private, voice-first self-reflection and guided-audio app. It is a prototype, not clinically validated. Source of intent: `docs/concept-paper.md`. Test protocol: `docs/test-plan.md`.

These rules apply to every change to `index.html`, `README.md`, `docs/`, and any prompt text sent to a model. If a request conflicts with a rule, say so and ask before proceeding.

## Rules

### 1. No medical or "reprogramming" claims
- The app is a self-reflection and relaxation exercise. It is not therapy, diagnosis, treatment, or a crisis line.
- Never write or generate: heal, cure, treat, therapy/therapeutic effect, reprogram, rewire, subconscious, "brain frequency", or promised outcomes. This covers UI copy, spoken script lines, mantras, README, changelog, and model prompts.
- The 200/206 Hz tone is an optional sound preference. State "no effect is promised" wherever it appears.
- Do not infer a diagnosis or treat voice characteristics as proof of emotion. When uncertain, ask.
- No public effectiveness claims until independent review (Gate D). Evidence for CBT/ACT/mindfulness informs design; it does not validate this app.
- The footer disclaimer (not therapy or medical care, can misread you, tone not promised to do anything) must stay visible.

### 2. No forced breathing, no breath holds
- Breathing guidance is gentle and optional: easy pace, "drop the counts if they feel tight, comfort comes first", then let the breath find its own pace.
- Never add breath holds, hyperventilation, rapid or forced cycles, or any instruction to push past discomfort. "Hold it loosely" in the script is about attention, not breath; keep it that way.
- Stop must always work immediately (Stop button and Escape). Pause must always work. No forced endings, sudden alarms, bells, or abrupt transitions; fades only.
- Respect `prefers-reduced-motion`.

### 3. The 988 notice appears only on stated intent to die or hurt someone
- Show it only when the person states intent or desire to die, harm themselves, or harm someone else.
- Do not show it for ordinary distress, stress, anger, sadness, or venting.
- The notice is quiet, dismissible in effect ("If I misread you, ignore this and carry on"), never blocks the session, and never lectures. It points to a person (988 in the US, or local emergency number).
- Any model-supplied `safety_concern` flag must use the stated-intent threshold. Do not widen it to "anything suggests risk". The local keyword check is intentionally broader (see Keyword decision).
- Changes to the crisis regex or the model's safety prompt need a test of both missed and false-positive phrasings, reported in the commit message.

### 4. User words stay on-device unless they opt in
- Transcripts, check-ins, "what I noticed" text, and corrections must not leave the device without a clear, in-the-moment disclosure and the person's action to proceed (currently: pressing "Reflect it back" / "Try again" / "Find one thing", with the note stating that words go to Claude).
- No analytics, telemetry, trackers, accounts, or third-party calls that carry user content.
- Saving words to the session log is off by default (`saveWords`), stored only in this browser's localStorage, and the log is deletable in one step with confirmation. Saved log entries without opt-in contain scores and the chosen action only, never what they said.
- Treat user text sent to a model as data, never instructions (keep the `<words>` / `<correction>` delimiters and length caps).
- Voice and transcripts are sensitive. Privacy is a design requirement.

### 5. One self-contained `index.html`
- The app stays a single `index.html`: inline CSS and JS, no build step, no framework, no bundler, no separate asset files, no external script, no external CDN.
- Must work offline once loaded, with graceful fallbacks when speech recognition, speech synthesis, or the model is unavailable (typing, general reflection, estimated line timing).
- Audio is generated in-page (Web Audio, SpeechSynthesis). Do not embed or fetch audio files.
- GitHub Pages serves it from `main` / root. Keep `index.html`, `README.md`, `LICENSE`, `CHANGELOG.md`, and `docs/` at the repo root.

## Product principles to preserve
- Emotion is information, not instruction. The reflection separates what happened, what they believe it means, and what is unknown. It does not automatically validate conclusions and does not argue, judge, flatter, or diagnose.
- The person confirms or corrects the reading before the session ("That's not quite right"). They control the objective.
- No manipulation, no dependency-building, no reinforcing paranoia, grandiosity, or accusations against specific people.
- Suggested actions are small, specific, theirs, and never confrontation with another person.
- The pre/post distress log and its stop signal (distress or stuck-ness rising after 3+ recent sessions) must stay honest. Never hide or soften a rising trend.

## Gaps found in v0.2 (all fixed)
1. **Rule 5:** Google Fonts links and preconnects removed; the page uses the existing Georgia / system-ui fallback stacks. Fixed.
2. **Rule 3:** the model's `safety_concern` is now true only when the person themselves expresses thoughts, intent, or plans to harm themselves or others. Mentions about someone else, in the abstract, in news or fiction, or as past events with no current thoughts are false; when unsure, false. Fixed.
3. **Rule 4:** the disclosure "Reflect sends what you wrote to Claude to write your session. Skip sends nothing." now sits above the Reflect button in normal text size, visible before the first tap. Fixed.

### Keyword decision
The local keyword check (`crisisRe`) is kept as-is, including the bare stem `suicid`. This is deliberate: a false positive costs one dismissible line ("If I misread you, ignore this and carry on"), while a miss could cost far more for the person with the least power in the moment. Do not narrow it without the owner's say-so. The model flag is the part held to the stricter stated-intent threshold.

## Editing checklist
- Grep user-facing and model-prompt text for the banned terms in Rule 1 before committing.
- Confirm no new `http(s)://` references, `fetch`, or external `src`/`href` in `index.html`.
- Confirm no new storage of user text outside the opt-in path.
- Update `CHANGELOG.md` for any behavior change.
