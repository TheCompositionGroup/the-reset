# Fancy Ape — The Reset

A free, private, sound-only web app. Turn the dial, choose a time, press play, listen.

**Live prototype:** open `index.html` in a browser, or enable GitHub Pages (Settings → Pages → Deploy from branch → `main` / root).

## What it does
1. **Turn the dial** to one of eight stops: Mend, Ground, Flow, Power, Heart, Voice, Vision, Stillness (285 to 963 Hz). Each shows its frequency and, except Mend, a chakra name.
2. **Set your time** on the wheel beside Play: 5, 10, 20 or 30 minutes (default 10).
3. **Press play.** Press again to stop; stopping ends the session and resets the clock.
   - **Intensity** is the short arc at the bottom of the dial: low is steady, high is a deeper slow swell and fuller atmosphere. Loudness is your device volume.
   - **Sound** switches between *Tone* (a soft sine) and *Atmosphere* (a soft layered drone).
   - One fact about the current frequency sits under Play and changes slowly while playing. Tap it for more: this frequency, measured sound science, and where the frequencies come from. All text is in one `COPY` block in `index.html`.
   - **How it works** opens the usage notes.
4. **At a timed finish**, a short closing line, then **Begin again** or **Done**. A small *Share feedback* link opens the optional question "How do you feel now?" (Better, Same, Worse), a link to suggest a change, and your saved answers. Your answers are a rough self-report, not proof that a frequency does anything.

You can turn the dial while playing; the sound crossfades over 2 seconds and the timer keeps running. Sound fades in over 5 seconds and out over 8 at a timed end; Stop and Escape end at once with a short fade.

## Where the frequencies come from
- 396, 417, 528, 639, 741, and 852 Hz are the modern Solfeggio set popularised by Joseph Puleo and Leonard Horowitz in *Healing Codes for the Biological Apocalypse* (1999). 963 Hz is a later addition to that set. Some later lists also add 174 and 285 Hz; the app includes 285 Hz as Mend and labels the tissue-repair claim attached to it as an untested wellness claim. Nothing in this app claims these tones do what that book says.
- Pairing each frequency with a chakra is modern. Traditional sources attach bija (seed) sounds to the chakras, not hertz.
- The U.S. National Center for Complementary and Integrative Health, [Music and Health: What the Science Says](https://www.nccih.nih.gov/health/providers/digest/music-and-health-science), reviews research on music in general (for example for relaxation and mood), and describes that evidence as preliminary and mixed. It does not show frequency-specific effects.

## Requirements
- A modern browser with Web Audio. Works offline once loaded.
- Sound may stop when a phone screen locks. The app asks the browser to keep the screen on while playing, where supported.
- Android phones give a light tap on each dial stop and each in-breath; iPhone does not vibrate.

## Privacy
- No network calls, no accounts, no analytics, no text input, no microphone.
- Your last stop, time, sound and intensity are remembered in this browser. If you answer the question, the stop, minutes, answer, and date and time are saved here too, and nothing else. If Worse is your answer on 3 or more of your last 12 sessions, a quiet notice suggests pausing. *Delete all* removes them.

## Feedback
Use [GitHub Issues](https://github.com/TheCompositionGroup/the-reset/issues): what did you try, and what would you change? The same link is in the app under *Share feedback*.

## Contributors
- The Composition Group LLC · Fancy Ape
- Built with [Claude Code](https://claude.com/claude-code)
- Add your name here with your first accepted suggestion or pull request.

## What this is not
A sound experience. Not therapy or medical care. The frequency and chakra pairings are modern wellness associations, not proven effects. Nothing is promised.

## Status
Prototype v0.5.0 (unreleased) · FA-RESET-001. See `docs/` and `HAPTICS.md`. The earlier voice-and-reflection version (v0.2.x) is in the git history.

## License
Code: MIT (see `LICENSE`). Documents in `docs/`: CC BY-SA 4.0.

The Composition Group LLC · Fancy Ape
