# Fancy Ape — The Reset

A free, private, sound-only web app. Turn the dial, choose a time, press play, listen.

**Live prototype:** open `index.html` in a browser, or enable GitHub Pages (Settings → Pages → Deploy from branch → `main` / root).

## What it does
1. **Turn the dial** to one of seven stops: Ground, Flow, Power, Heart, Voice, Vision, Stillness. Each stop shows its frequency (396 to 963 Hz) and a chakra name.
2. **Choose a time:** 5, 10, 15, or 20 minutes, or ∞ to play until you press Pause or Stop (the clock counts up).
3. **Choose a sound:** *Tone* (a soft sine at the stop's frequency) or *Atmosphere* (a soft layered drone built around it).
4. **Press play.** The volume swells slowly in and out and the glow follows. **Intensity** sets how deep that pulse is and how full the atmosphere is: low is smooth and steady, high is a deeper pulse. Loudness is your device volume. Pause, Stop, Intensity, and Mute are on the same screen.
   - **+5 min** adds five minutes at any time without interrupting the sound. In the last minute a quiet "Extend? +5" appears and goes away if ignored.
   - A faint line of text fades in and out every 20 to 30 seconds (the physics of frequency, how modern chakra charts pair the tone, or a short invitation). **Facts on/off** turns it off. The wording is in one `COPY` block at the top of the script in `index.html`.
5. **At a timed finish** (or after stopping ∞ at 5 minutes or more), a short closing line, then **Begin again** or **Done**. A small *Share feedback* link opens the optional question "How do you feel now?" (Better, Same, Worse), a link to suggest a change, and your saved answers. Your answers are a rough self-report, not proof that a frequency does anything.

You can turn the dial while playing; the sound crossfades to the new stop over 2 seconds and the timer keeps running. Sound fades in over 5 seconds and out over 8. Stop on a timed session and Escape end it at once with a short fade; Stop on ∞ fades over 8 seconds. The glow takes the color of the active stop.

## Where the frequencies come from
- 396, 417, 528, 639, 741, and 852 Hz are the modern Solfeggio set popularised by Joseph Puleo and Leonard Horowitz in *Healing Codes for the Biological Apocalypse* (1999). 963 Hz is a later addition to that set. Nothing in this app claims these tones do what that book says.
- Pairing each frequency with a chakra is modern. Traditional sources attach bija (seed) sounds to the chakras, not hertz.
- The U.S. National Center for Complementary and Integrative Health, [Music and Health: What the Science Says](https://www.nccih.nih.gov/health/providers/digest/music-and-health-science), reviews research on music in general (for example for relaxation and mood), and describes that evidence as preliminary and mixed. It does not show frequency-specific effects.

## Requirements
- A modern browser with Web Audio. Works offline once loaded.
- Sound may stop when a phone screen locks. The app asks the browser to keep the screen on while playing, where supported.
- Android phones give a light tap on each dial stop and each in-breath; iPhone does not vibrate.

## Privacy
- No network calls, no accounts, no analytics, no text input, no microphone.
- Your last stop, time, sound, intensity, and facts on/off are remembered in this browser. If you answer the question, the stop, minutes, answer, and date and time are saved here too, and nothing else. If Worse is your answer on 3 or more of your last 12 sessions, a quiet notice suggests pausing. *Delete all* removes them.

## Feedback
Use [GitHub Issues](https://github.com/TheCompositionGroup/the-reset/issues): what did you try, and what would you change? The same link is in the app under *Share feedback*.

## Contributors
- The Composition Group LLC · Fancy Ape
- Built with [Claude Code](https://claude.com/claude-code)
- Add your name here with your first accepted suggestion or pull request.

## What this is not
A sound experience. Not therapy or medical care. The frequency and chakra pairings are modern wellness associations, not proven effects. Nothing is promised.

## Status
Prototype v0.4.0 (v-next) · FA-RESET-001. See `docs/` and `HAPTICS.md`. The earlier voice-and-reflection version (v0.2.x) is in the git history.

## License
Code: MIT (see `LICENSE`). Documents in `docs/`: CC BY-SA 4.0.

The Composition Group LLC · Fancy Ape
