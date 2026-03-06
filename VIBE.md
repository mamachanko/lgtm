# LGTM

## What this is

A game about staring at code and knowing something is wrong.

You’ve seen it before. You’ll see it again. The off-by-one. The unchecked null. The SQL injection hiding in plain sight inside a string template that somebody called “just a quick fix.” You are the last set of eyes before this ships to production, and nobody else is coming.

LGTM is a game for people who already write software. It’s not trying to teach you. It respects that you’ve been here. It’s trying to make you *feel* something — the satisfaction of catching the bug, the dread of knowing you almost didn’t, and the dark comedy of an industry that runs the entire world on vibes, duct tape, and deploys at 4:47pm on a Friday.

## Who it’s for

Software engineers. Not beginners. Not people who want to learn to code. People who have mass-closed Jira tickets on a Friday afternoon. People who have read a stack trace at 2am and felt nothing. People who have written `// TODO: fix this later` and meant it, truly meant it, and never gone back.

The game should feel like it *knows* you. Like it’s been sitting in the same standup. Like it’s read the same postmortems. Not gatekeeping — just speaking the language. If you’ve ever felt the particular despair of a green CI pipeline that you don’t trust, this game is for you.

## The feeling

There’s a specific emotional register here. It’s not mean. It’s not elitist. It’s the gallows humor of people who care deeply about craft but work inside systems that make caring difficult. It’s the joy of a beautiful solution and the exhaustion of knowing it’ll get refactored into something worse by next quarter. It’s solidarity through shared suffering.

Think: the developer who writes meticulous code and also hasn’t updated their dependencies in eight months. The architect who draws perfect system diagrams and also once shipped a `console.log("here")` to production. We contain multitudes.

The tone is:

- **Snarky but kind.** We’re laughing with you, always. The sarcasm is aimed at the systems, the processes, the industry — never at the player.
- **Jaded but loving.** Deep cynicism about enterprise software coexists with genuine admiration for elegant solutions. Both are real. Both matter.
- **2026 and exhausted.** The AI discourse. The layoffs. The “we’re a family” companies. The six rounds of interviews for a job that pays less than last year. The game lives in this moment without being preachy about it. It just… knows.
- **Laconic.** Short sentences. Lowercase. The game doesn’t over-explain. It says something once, dry, and moves on. If you get it, you get it. If you don’t, it doesn’t care. (It does care. It just won’t show it.)

Some reference points for vibe, not for imitation: Gary Bernhardt’s “Wat.” The existential dread of a Sentry notification at 11pm. The calm resignation of `git push --force`. Readme files that just say “good luck.” Commit messages that are just a period.

## The aesthetic

A CRT monitor in a dark room.

Green phosphor on black. Scanlines. A vignette that darkens the edges. An errant horizontal line that drifts slowly down the screen every few seconds. Occasional flicker — not enough to annoy, just enough to remind you that nothing is stable. The faintest bloom on the text, like the characters are burning themselves into the glass.

One font. Monospace. Beautiful but utilitarian. JetBrains Mono or something with similar character — legible at small sizes, distinctive at large ones. No serif anywhere. No decoration. The typography does all the work.

The color palette is almost entirely monochrome. Green-on-black to start, like an old VT100. As you progress, the phosphor shifts — amber, maybe, then cooler tones. The world of the game changes color so slowly you don’t notice until you look back.

And then, sometimes, for a few seconds — *color*. Full syntax highlighting. Warm tones. The CRT filter drops away. Everything is crisp and readable and calm. Maybe there’s a faint ambient sound, like distant rain or a coffee shop. It’s a power-up, mechanically. But emotionally it’s a reward. A breath. A reminder of what programming feels like when it’s good. And then it’s gone, and you’re back in the green dark, and you keep going.

No menus. No settings screens. No hamburger icons. The game reveals itself through play. The first thing you see is text and a blinking suggestion to begin. Every interaction after that teaches you the next one. If you need a tutorial, the game has failed.

## The texture

The flavor text between levels is where the voice lives. It’s commit messages. Jira ticket titles. Slack messages from PMs. Postmortem action items. Deploy logs. The game never breaks character. Every piece of text that isn’t code is a fragment from the world of software work, and every fragment is slightly, quietly absurd in the way that real ones are.

> ticket #4091 — “login is broken idk” — priority: CRITICAL — assignee: you, apparently

> commit message: “refactored some stuff, tests pass locally”

> incident postmortem: “root cause: human error” — action items: “be more careful next time”

> PR description: (empty) — reviewer comment from 3 weeks ago: “nit: add description” — status: approved

These aren’t jokes. They’re *real*. That’s what makes them funny and what makes them hurt a little. The game doesn’t have to try to be funny because the source material is inherently, beautifully absurd.

Transition screens between levels are loading messages from the void:

> npm install hope

> git blame: it was you.

> deploying to staging… jk, that’s prod.

> running tests… 0 found.

## What it is not

It is not educational software with a punk skin. The game never explains anything unless you’ve already answered. Even then, it gives you one line — dry, knowing — and moves on. If you want to learn *why* `typeof null === "object"`, that’s your journey. The game just confirms that you found it, or that you didn’t, and either way the deploy pipeline doesn’t care about your feelings.

It is not a coding tutorial. It is not leetcode with vibes. It is not for impressing recruiters or padding a resume. There’s no certificate. There’s no LinkedIn badge. There’s a streak counter that resets when you’re wrong, because that’s how production works.

It is not mean. This is important. The internet has enough contempt for people who are learning or struggling. This game is for people who already know what they’re doing and still get it wrong sometimes, because that’s the whole thing, that’s the entire profession — knowing and still getting it wrong, forever, until you retire or mass-close your tickets one last time.

## The feeling when you get it right

A green line on the correct answer. A one-liner that makes you exhale through your nose. Your streak goes up. The game acknowledges you with the minimum possible ceremony and moves on. You feel competent. You feel seen. You feel like maybe, despite everything, you’re good at this.

## The feeling when you get it wrong

A red line. A different one-liner that’s sympathetic but not soft. Your streak resets. The game shows you the answer after a beat, and the explanation is the same dry voice, and it’s never condescending, it’s just: *yeah. this one gets everyone.* Or: *the bug ships. the pager goes off. the cycle continues.* And then you move on, because that’s what you do. That’s what you’ve always done.

## Why

Because there’s something beautiful about reading code carefully and understanding it deeply and catching the thing that everyone else missed. And because there’s something funny and sad and human about the fact that we build the most complex systems in human history and also mass-close Jira tickets on Friday afternoon because we’re tired and nothing means anything and also everything means everything and we just want to write good software but first we have to sit through this retro.

That’s the vibe.
