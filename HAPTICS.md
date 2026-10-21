# Haptics (future exploration)

Not built. This note records what we know, so the idea can be picked up later.

## Idea
Pace the breath-length volume swell (4 s in, 6 s out) with a soft touch cue on the phone, so the rhythm can be felt as well as heard.

## Limits
- **Phone vibration motors cannot reproduce the tone frequencies.** The stops run from 396 to 963 Hz. Phone motors are built for short pulses and respond at roughly 50–250 Hz at best, so a vibration cannot carry or mirror the audio. Any haptic cue would be a slow pulse that follows the swell, not the tone.
- **iOS Safari does not support the web Vibration API** (`navigator.vibrate`). A web-only version would work on Android browsers and do nothing on iPhone. Real iPhone haptics need a native app.
- Android support varies by device and browser, and some phones ignore the lightest pulses.

## What exists today
On Android, the app already gives a 10 ms tap when the dial snaps to a stop and a 15 ms pulse at each in-breath (only when Intensity is above 15%, since a steady tone has no swell). Nothing happens on iPhone or desktop.

## If this is picked up
- Keep it optional and off by default, with its own toggle.
- Follow the volume swell only; never add counts, holds, or fast cycles.
- Keep it silent when the screen is off or the tab is hidden.
- Test on real Android and iPhone hardware before claiming anything works.
- Same copy rules as the rest of the app: no health claims.
