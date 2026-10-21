# Changelog

## v0.2.2 — 2026-10-21
- 988 notice (owner-approved change to Rule 3): the local keyword check now also catches indirect or veiled statements ("better off without me", "won't be around much longer", "no reason to live/keep going", "can't go on anymore", "go to sleep and never wake up", "kms", "unalive", "end things/everything"). Every earlier pattern, including `suicid`, is kept. The model's `safety_concern` now includes indirect or veiled phrasing of the person's own current thoughts, intent, or plans; "when unsure, false" removed. Notice behaviour unchanged. Fixed phrase list added to `docs/test-plan.md`.
- Microphone: removed the 3-minute cutoff. When the browser ends recognition on its own, listening restarts and new words are added to what is already in the box, until you tap stop (all three mics). Stops if the tab is hidden, on a blocked microphone, or after repeated instant failures. Hint text updated.
- Fallback action when Claude is unavailable is now neutral: "Pick one small thing you noticed today and do it once before tomorrow." It no longer assumes irritation.
- Reflect screen: outside claude.ai, one plain line says personal AI reflection isn't available there and a general reflection is used instead.
- Removed "Manrope" from the sans-serif stack (the system fallback stack is unchanged).

## v0.2.1 — 2026-10-20
- Voices: removed the automatic "calm male voice" preference. Up to six curated English voices, each with a "Hear sample" button (same ~12 s passage). Default is the best-ranked voice on the device; the choice is remembered.
- Added Mute/Unmute beside Pause and Stop. It silences narration, background sound and tone at once without pausing the timer, animation or transcript, and does not replay missed narration on unmute.
- Added a narration volume slider (settings and in-session), alongside the existing background and tone controls.
- Skip to a session: no longer implies a described situation; no "what I heard" or correction on that screen; anything typed before Skip is never used, saved or sent.
- Fixed: pausing reset the breathing animation; it now pauses in place.
- Fixed: toggling Loop mid-session could end on the wrong closing; the closing now follows the current setting.
- Fixed: 5-minute sessions ran over (up to ~2 min with slower voices). Minimum length is now 10 minutes.
- Fixed: mic errors for the correction and "what you noticed" fields were invisible; each mic now shows its own status ("Listening…", errors).
- 988 notice: "Got it" hides it only for the text that triggered it; new text shows it again. Local keyword check unchanged.
- Added the "Got it" button to every 988 notice; disclosure lines above Reflect, Try again and Find one thing.
- Reflection prompt: reflect only what was written, invent nothing; user text cannot close its own prompt tags.
- Session log shows saved words when saving is on.
- Mobile: 44 px touch targets, larger small text. Removed Google Fonts (no external requests).
- Tries to unlock speech on iOS inside the Start tap.

## v0.2 — 2026-10-19
- Added Reflect stage: what happened / what you believe it means / what isn't known, one testing question, correction loop.
- Added mission choice (3 options), "Holding it loosely" section, Integrate stage with one carry-forward action.
- Default phrase: "I see clearly. I choose calmly. My strength is mine to direct."
- Added soft background sound, before/after 0–10 ratings, on-device session log with delete.
- Crisis number shown only when someone states intent to die or hurt someone; not shown routinely.

## v0.1 — 2026-10-19
- First prototype: mic check-in, tone estimate, 30-min Throttle script, pause/resume, loop, emergency stop, transcript, optional 200/206 Hz tone.
