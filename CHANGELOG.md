# Changelog

## v0.7.1 (unreleased)
- New: a small "Fancy Ape Home" link above the title, opening https://fancyape.com in a new tab (44 px tap target, no animation). Nothing else on the screen changes.

## v0.7.0 (unreleased)
- Changed: **the centre button is Play / Pause.** Idle it is Play; while playing it is Pause (two bars); while paused it is Play and resumes ("Play", "Pause", "Resume" for screen readers). Pause fades out over about 0.45 s, then the audio clock is suspended so the time left freezes; the screen wake lock is released and the rolling facts and glow stop (the glow holds dim). Resume restarts the clock, fades in over about 1 s, retakes the wake lock, and applies any dial or sound change made while paused.
- New: **End session**, a small text button under the time, shown only while paused. It ends the session with the 0.3 s fade: after at least 60 s played it shows the ending with the minutes actually played; under 60 s it returns to the dial. Escape does the same, whether playing or paused.
- Changed: a phone-side interruption (screen lock, a call) uses the same paused state, so Resume and End session work after it too.
- Unchanged: the 8 s fade at a timed end; the 5 s fade in on Play.
- Changed: the "How it works" Play line, README step 3 and the test plan describe this.

## v0.6.2 (unreleased)
- Changed: **Stop or Escape after at least 60 seconds of play now shows the ending**, the same screen as a timed finish, instead of going straight back to the dial. The 0.3 s fade is unchanged. Under 60 seconds still returns to the dial with no ending.
- Changed: the minutes saved with an answer are the minutes actually played (rounded, at least 1), not the timer setting. Time while the browser has the sound suspended (screen lock, a call) is not counted. A timed finish still saves the timer setting.
- Changed: the "How it works" Play line describes this.

## v0.6.0 (unreleased)
- Changed: **the end of a session is simpler.** The end screen reads "That's enough for now." with the rotating closing line under it (new first line: "Take the good with you. Leave the rest."). One primary button, Begin again; Done is gone. A small "Leave a banana 🍌" button opens the banana view. The stop-signal notice is unchanged.
- Changed: **feedback is now "Leave a banana."** The view has a "Send a banana" link that opens the person's email app (mailto:bananas@fancyape.com; no account, nothing sent by the page) and one optional "How do you feel?" row (Better / Same / Worse). Same saving logic and log format; after a tap it shows "Thanks." (after Worse: "Thanks. Try a different stop or a shorter time, or stop for today.") A Back link and Escape return to the end screen.
- Removed: the GitHub "Suggest a change" link and the counts table from the in-app feedback view. The GitHub Issues link stays in the README.
- New: **Your answers** in "How it works" holds the counts table and Delete all, with the line "Better / Same / Worse answers stay on this device. Three Worse answers in your last 12 sessions shows a pause notice."
- Fixed: feedback address is bananas@fancyape.com.
- Unchanged: the log format, the stop signal (3 Worse of the last 12), and storage keys.

## v0.5.3 (unreleased)
- Changed: Play/Stop takes the selected stop's colour, darkened 30% toward ink; the icon contrast is at least 3.6:1 on every stop (lowest is 528 Hz at 3.68:1). The colour changes instantly when the dial turns, because the app animates only opacity and transform.
- Fixed: tapping Play no longer leaves a focus ring; keyboard focus still shows.

## v0.5.2 (unreleased)
- Changed: the small dot beside the dial pointer is gone; the highlighted tick and pointer mark the stop. The intensity knob is a short line like the dial pointer. Intensity starts at 50% (the middle of the arc) for new visitors; a saved value is kept.
- Changed: the Sound button keeps one fixed width (7.75rem) in both modes. A small waveform replaces the "Sound" caption: one wave for Tone, three layered waves for Atmosphere. The screen-reader label is unchanged.

## v0.5.1 (unreleased)
- Fixed: tapping or dragging the intensity arc no longer moves keyboard focus to it, so the rectangular focus outline no longer appears over the dial. With the keyboard, focus on intensity now shows as a thicker brass arc instead of a rectangle.
- Changed: Play/Stop is in the centre of the dial. Each ring label shows its Hz under the name; the large centre Hz is gone. Tapping the dial no longer shows a focus ring (keyboard focus still does).

## v0.5.0 — fewer controls (unreleased)
- Changed: **one Play/Stop button.** Play starts; the same button (now a square) stops. Stopping ends the session with a 0.3 s fade and resets the clock; there is no Pause. The separate Stop button is gone. If the phone suspends the sound (screen lock, a call), the button shows Play and continues where it left off.
- Removed: **+5 min** and the "Extend? +5" prompt.
- Changed: **time** is 5, 10, 20 or 30 minutes, chosen on the wheel before playback (default 10). 15, 45, 60 and ∞ are gone; a saved older value maps to the nearest kept one (∞, 45 and 60 become 30; 15 becomes 10).
- Changed: **intensity** is a short arc in the empty wedge at the bottom of the dial (low at lower left, high at lower right) instead of a slider row. A press within 38° of straight down sets intensity; anywhere else on the dial sets frequency. The choice is made at the press and kept for the whole drag, so one gesture never changes both (covered by automated pointer tests). Keyboard: its own `role="slider"` (Intensity, 0–100) after the dial in tab order; arrows ±5, Page Up/Down ±10, Home/End.
- Removed: the **Mute** button (device volume does this) and the **Facts on/off** toggle.
- Changed: **Tone / Atmosphere** is one button labelled "Sound" showing the current mode; press to switch.
- New: **285 Hz — Mend**, the lowest stop. Eight stops now span the same 270° arc (38.6° apart). It has no chakra pairing; the readout says "NO CHAKRA PAIRING". The tissue-repair claim some later lists attach to 285 Hz appears only as a labelled wellness claim with "No study shows that a tone repairs tissue."
- Changed: the saved stop is now its Hz (was an index), and new answers also save the Hz, so 285 Hz doesn't shift older data; older answers are still counted under the right stop.
- Changed: **facts.** One fact for the current frequency shows under Play at all times (wavelength in air). While playing it changes every 20–30 s. Tapping it opens "More about the sound": this frequency (cycle time, wavelength, nearest piano key, computed in the page), measured sound science, and where the frequencies come from, kept separate. Rolling lines draw only on this frequency and measured physics, plus the invitations.
- Changed: the 285 Hz tissue-repair note (`COPY.stop.notes`) shows only in the expanded "More about the sound" panel. `rollingLines()` uses only `COPY.stop.lines`, the paired/unpaired line, physics and invitations.
- Changed: header reads "Turn the dial. Set your time. Press play." Usage notes (headphones, screen lock, what each control does) moved into an expandable **How it works**.
- Storage: drops facts on/off (removed on load). Keeps stop, time, sound, intensity, closing-line position and the answer log.

## v0.4.0 — v-next (unreleased)
Builds on v0.3.0 (the dial).
- Changed (v-next.3, layout): the header is one line, "Turn the dial. Choose how long. Press play." The center-to-edge needle is now a short knob-style pointer on the dial's rim, so the center is clear, and the Hz value ("417 Hz") is shown large in the center of the dial and updates as the dial turns. Under the dial there is one line, "SACRAL · ASSOCIATION" (the large mode name is gone; it is the bold label on the dial). The bottom row is now [time wheel] [Play] [Tone / Atmosphere stacked], all centered on Play with 44 px toggles; on screens narrower than 360 px the toggles sit under Play instead. **Stop** moved to the row under Play (Stop, +5 min, Facts) while playing, so the toggles can stay in place. The dial's `aria-valuetext` is now "Flow, 417 hertz, sacral association" (matches the visible readout).
- New: tab icon. Three inline PNG icon links (32×32, 16×16, apple-touch 180×180, as `data:` URLs, so nothing is fetched and there are no asset files) and `theme-color` for light (#EEF0EC) and dark (#141B1E), matching the page background.
- Changed (v-next.2, time wheel): the "Minutes" label and the 5/10/15/20/∞ pill row are gone. A vertical time wheel (iOS-picker style) sits left of Play: 5, 10, 15, 20, 30, 45, 60, ∞; default 15 (a saved time is kept). The selected value is centered and bold with a small "min" beside it (hidden on ∞), with one faded value above and below. It snaps to each value and takes touch drag, mouse wheel or trackpad, a click on the faded value, and arrow keys (standard spinbutton keys: Up/Right/PageUp increase, Down/Left/PageDown decrease, Home = 5, End = ∞). `role="spinbutton"` with `aria-valuetext` such as "15 minutes" and a visible focus ring. While playing, the wheel locks and the same box shows the live mm:s countdown (h:mm:ss counting up for ∞); `role="timer"`. +5 min still updates it; +5 min and Facts now sit below Play so nothing above it moves. When stopped, the wheel shows the last chosen value. Spacing tightened. Each side of the wheel is a 44 px touch target (12 px of invisible padding above and below the visible wheel), and the footer credit now reads "A Fancy Ape® project · The Composition Group".
- Changed (v-next.1, copy and layout): new header line "No instructions to follow. Nothing to achieve. Just listen." above the existing instruction line. The readout label reads "ROOT · ASSOCIATION" (and so on for every stop), smaller and lighter. A small "Minutes" label sits above the time pills. Two small lines under Play: "Best with headphones." and "Sound may pause if your screen locks." Footer keeps its required disclaimer and adds "A Fancy Ape project · The Composition Group" with a link to fancyape.com (a second tap-only external link). The footer now sits right after the content instead of at the bottom of the window, and the compact layout applies up to 860 px tall so Play stays in view. The speaker button was already a mute-only toggle (crossed-out when muted, aria-label Mute / Unmute); unchanged.
- Changed: the volume slider is now **Intensity**. Device volume is the only volume control (output level is fixed). Low is a smooth, steady sound. High is a deeper pulse (the 10 s swell goes from steady up to about 90% deep) with a fuller atmosphere (octave below, upper harmonics and noise bed are raised in Atmosphere; Tone stays a pure sine and changes only its pulse). Changes ramp over about 0.15 s, so there are no clicks. Remembered between visits (default 40%). Mute stays. The glow and the Android in-breath tap follow the pulse depth.
- New: **+5 min** during a timed session. Each tap adds 5 minutes with no pause or restart, and the tone keeps running. The 8 s end fade moves back with the new end time; if it had already started, the sound eases back up. In the final minute a quiet "Extend? +5" appears for 20 s and goes away if ignored. Not shown for ∞.
- New: **rolling fact line** under Play, one line at a time, 3 s fade in and out, every 20–30 s, with a Facts on/off toggle (remembered). Three kinds only: physics, tradition (modern chakra charts; sources disagree), and invitation. All text is in one `COPY` block at the top of the script in `index.html`, along with the closing lines.
- Changed: while playing, the time pills are replaced by +5 min and Facts.
- Changed: **end screen** is one closing line (rotating "Drink water. Be nice to people." / "Pass it forward." / "Enjoy your day."), **Begin again** (back to the dial, last settings kept) and **Done**, plus a small "Share feedback" link. That opens the optional Better / Same / Worse buttons, a "Suggest a change" link to the repo's GitHub Issues page, the answers table and Delete all. A Back button returns to the end screen; Escape also works.
- Changed: a timed session's logged minutes include any +5 min added.
- New: issue template ("What did you try? What would you change?"), Contributors section in the README, `HAPTICS.md`.
- Storage: adds intensity, facts on/off, and the closing-line position (none of it personal). The old volume value is no longer used.
- The "Suggest a change" link is the only external link and only opens when tapped; the app still makes no network calls.

## v0.3.0 — 2026-10-21
Rebuilt as a sound-only experience on one screen.
- New: a rotary dial with seven snap stops on a 270° clockwise arc (gap at the bottom): Ground 396 Hz, Flow 417, Power 528, Heart 639, Voice 741, Vision 852, Stillness 963. Drag anywhere on the face, tap a ring label, or use the arrow keys; thin tick marks, a needle, and a notch highlight on each snap. `role="slider"` with spoken values like "528 hertz, solar plexus, power". Android: a 10 ms tap on each snap.
- New: timer pills (5, 10, 15, 20, ∞) and a Tone | Atmosphere toggle (default Atmosphere). Tone is a soft sine at the stop's frequency. Atmosphere is a layered drone: octave below, two slightly detuned fundamentals, quiet harmonics, and a filtered noise bed.
- New: breath pacing. The volume swells in over 4 s and out over 6 s, and the glow follows. Android: a light pulse at each in-breath, kept on under reduced motion (only visuals stop). No counts, no holds.
- New: 5 s fade-in, 8 s fade-out at the natural end, 0.3 s fade on Stop and Escape. Pause holds in place. Turning the dial (or changing the sound) while playing crossfades over 2 s; the timer keeps running.
- New: volume slider (starts at 25% on first visit, then remembered) and a Mute button. Master gain tops out at 0.6, with a gentle compressor as a safety net.
- New: the AudioContext is created in the Play tap; a screen wake lock is requested while playing and released on Pause, Stop, and end; silent fallback if unsupported.
- New: the last stop, time, sound, and volume are remembered in this browser.
- New: ∞ plays until Pause or Stop and counts up (h:mm:ss). Stop on ∞ fades over 8 s, then shows the end screen if it ran 5 minutes or more; the log keeps the actual minutes played. Escape is always a fast stop with no prompt.
- New: the glow takes the active stop's color. Only opacity and transform are animated (no blur, no animated shadow or stroke); the notch feedback is a small marker that scales in.
- New: end screen after a timed completion (or an ∞ Stop at 5+ minutes) only: "How do you feel now?" Better / Same / Worse (optional). Saves one ordered, dated entry (stop, minutes, answer, date and time) and nothing else, with a count per stop and a Delete all button (with confirmation). "Worse" shows: "Noted. Try a different stop or a shorter time, or stop for today." An early Stop goes straight back to the dial.
- New: footer disclaimer on every screen (in normal flow, not sticky); minimum text size 13 px; 44 px tap targets. On short screens the dial and spacing shrink so Play is in view without scrolling at 320×640 and 360×740.
- Removed: narration and the voice picker, speech synthesis, microphone and transcription, AI reflection and every Claude call, the typed check-in, missions, the phrase, the carry-forward action, the transcript, the 0–10 before/after ratings, the 988 notice and `crisisRe` (no text is collected any more), the 200/206 Hz tone pair, the background-sound and loop settings, and the settings area.
- Stop signal restored: when 3 or more of the last 12 saved sessions are "Worse", a quiet notice shows on the dial screen and the end screen. It has no dismiss button.
- Measure changed: the 0–10 distress and stuck-ness ratings are replaced by one optional Better / Same / Worse tap (see `docs/test-plan.md`).
- Data note: v0.2 saved its log under `reset:` keys. v0.3.0 does not read or delete them; *Delete all* removes them.
- Docs: README and `CLAUDE.md` gain "Where the frequencies come from"; `CLAUDE.md` separates acoustics, symbolism, and intention for each stop and bans describing a frequency as a body part's natural resonance.
- Rewrote `CLAUDE.md` for the new app. The v0.2.2 crisis-detection rules are kept in `docs/crisis-rules.md`, to return if text input is ever added back.

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
