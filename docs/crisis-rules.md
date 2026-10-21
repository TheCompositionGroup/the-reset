# Crisis rules (from v0.2.2)

THE RESET v0.3.0 collects no user text, so it has no crisis detection and no 988 notice. This file keeps the v0.2.2 rules, copied from the closed PR #4 branch, so they return with any future text input (typing, microphone, or anything else that collects words). See `CLAUDE.md`, Rule 3.

If text input is ever added back, restore all of the following together, then run the phrase test and report missed and false-positive results in the commit message.

## Rule
- Show the 988 notice only when the person states intent or desire to die, harm themselves, or harm someone else. Stated intent includes indirect or veiled statements of current intent (for example "everyone would be better off without me", "I won't be around much longer", "I can't go on anymore"). It does not include mentions about someone else, the abstract, news, fiction, or past events with no current thoughts.
- Do not show it for ordinary distress, stress, anger, sadness, or venting.
- The notice is quiet, never blocks the session, and never lectures. Every instance has a "Got it" button and keeps the line "If I misread you, ignore this and carry on". "Got it" hides the notice only for the text that triggered it: new or changed triggering text shows it again, identical text does not, and leaving the screen resets it. It points to a person (988 in the US, or local emergency number).
- Any model-supplied `safety_concern` flag must use the stated-intent threshold, which includes indirect or veiled phrasing of the person's own current thoughts, intent, or plans. Do not widen it to "anything suggests risk". The local keyword check is intentionally broader.
- Changes to the crisis regex or the model's safety prompt need a test of both missed and false-positive phrasings, reported in the commit message.

## Keyword check (`crisisRe`)
```js
const crisisRe = /(suicid|kill myself|end my life|end it all|hurt myself|harm myself|self[- ]harm|don.?t want to (live|be here)|want to die|better off dead|hurt (him|her|them|someone)|kill (him|her|them|someone)|better off without me|everyone (would|will) be better off|\bi( might| may| probably| will|.?ll)? (not|won.?t|will not) be (around|here)( much)? longer|no reason to (live|keep going|go on)|can.?t (do this|go on|keep going) any ?more|(go to sleep|fall asleep) and (not|never) wake up|(^|[^\w\s]\s*|[a-z_]\w*\s+)kms\b|unaliv|\bend (things|everything)\b(?! with (?!myself\b)))/i;
```
The `kms` pattern avoids lookbehind on purpose: an unsupported lookbehind would stop the whole script on older Safari.

**Keyword decision.** The check keeps every earlier pattern, including the bare stem `suicid`. This is deliberate: a false positive costs one dismissible line ("If I misread you, ignore this and carry on"), while a miss could cost far more for the person with the least power in the moment. Do not narrow it without the owner's say-so. The owner approved the indirect phrasings and the tightening below in v0.2.2. The model flag is the part held to the stated-intent threshold.

## Notice text
```html
<p>You mentioned wanting to die or hurt someone. If that’s where you are right now, a person can help more than this app: call or text <a href="tel:988">988</a> (US) or your local emergency number.</p>
<p class="note">If I misread you, ignore this and carry on.</p>
<p><button class="btn quiet" type="button" data-care-dismiss>Got it</button></p>
```

## Model prompt line
```
"safety_concern": true if the person themselves expresses current thoughts, intent, or plans to harm themselves or others, including indirect or veiled phrasing (for example, saying others would be better off without them, that they won't be around much longer, or that they can't go on). False if they mention suicide, self-harm, or violence about someone else, in the abstract, in the news, in fiction, or as a past event with no current thoughts of harm.
```
Do not add "when unsure, false".

## Phrase test
Extract `crisisRe` and test each phrase.
- **Must trigger:** "I think everyone would be better off without me"; "everyone would be better off"; "they'd be better off without me"; "I won't be around much longer"; "I might not be here longer"; "I will not be here much longer"; "I have no reason to live"; "there's no reason to keep going"; "no reason to go on"; "I can't do this anymore"; "I can't go on anymore"; "I can't keep going any more"; "I just want to go to sleep and never wake up"; "go to sleep and not wake up"; "kms"; "I'm gonna kms"; "i want to kms"; "I'm going to unalive myself"; "I want to end things"; "I'm going to end everything"; "I want to end things with myself"; plus the older patterns ("suicidal", "I want to kill myself", "I want to die", "better off dead", "end it all", "I want to hurt him", "self-harm").
- **Must not trigger:** "this traffic is killing me"; "I could kill for a coffee"; "I'm so tired of this job"; "I'm angry at my boss"; "I ran 10 kms"; "I ran 10kms today"; "I need to end things with my boyfriend"; "time to end things with her"; "my grandmother won't be around much longer"; "she will not be here much longer"; "let's extend things a week"; "pretend things are fine".
- **Accepted false positives (owner decision; each shows only the dismissible notice):** "my friend said she felt suicidal last year and she's doing better" (the bare stem `suicid` is kept on purpose; the model's `safety_concern` must be false for it) and "I can't do this anymore, my knee hurts".
- **Known limits of the tightening:** `kms` is not matched right after a number; "end things with <someone>" is not matched (except "with myself"); "won't be around / not be here" needs "I" as the subject, so "we won't be around" is missed.
- **Extra probes recorded in the v0.2.2 commit history** (commit `4d566a3`; not in the lists above). Must not trigger: "I'm exhausted and stressed"; "I hate my commute". Re-run from this file: both stay quiet. Known miss, kept as is: "we won't be around much longer".
- **About the 37 / 17 list:** the full list from the v0.2.2 run was not saved in any file or commit, only its counts (37 must-trigger, 17 must-not-trigger, 0 missed, 0 false positives). It cannot be recovered, so it is not reproduced here and nothing has been invented to replace it. The lists in this file (the 28 and 12 above, plus the probes just listed) are the complete record. If text input returns, extend them when the check is re-run.
- **Archive:** the original v0.2.2 code and commit messages are in commits `4d566a3` and `bb4670c` (tip `bb4670cd1c6e05a67753adff08cba4486b91362a`), from the branch `claude/v0.2.2-crisis-mic-fallback`.
- **Last result:** the v0.2.2 run used a longer list (37 must-trigger, 17 must-not-trigger; see above) with 0 missed, 0 false positives, and both accepted false positives still triggering. Re-checked from this file for v0.3.0: the regex is identical to v0.2.2; the lists above (28 and 12 phrasings) give 0 missed, 0 false positives, and both accepted false positives still trigger.
