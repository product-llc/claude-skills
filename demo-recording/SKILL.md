---
name: demo-recording
description: Record a product demo as a script rather than a screen capture — drive the running product through a real flow, assert what each step should do, and render a deterministic video that fails instead of playing when the product has changed. Use when someone asks for a demo video, a product walkthrough, a recorded flow, a release clip, or "can you capture this working". It records what the product does; it does not decide what is worth showing.
license: MIT
---

# Demo recording — a demo that fails instead of lying

A demo video is the most trusted artefact a team ships and the only one nothing checks. A screen capture records one session with a wall clock running; when the product changes it keeps playing exactly as smoothly as before, and the first person to notice is a customer. This skill records a demo as a script whose every claim is checked, so a demo that has stopped being true breaks at the step that broke. It does not decide which flow is the demo — that is a judgement about what the audience doubts, and you have not met the audience.

Method by Alex Zapadenko: https://www.product.inc/notes/recording-a-demo-with-claude. Free to use, change and redistribute.

## Rules that hold throughout

- Never modify the product to make a step work. No seeded state the app cannot reach on its own, no hidden route, no stubbed response, no commits. If the only way to reach a screen is to fake it, the demo is claiming a path the product does not have — that is a finding, and you report it instead of working around it.
- Address every target the way a reader sees it: visible text, accessible label, role and name, placeholder. Never a class name, never a test id. A tape that breaks when a button's label changes is correct to break; one addressed by \`.btn-primary-2\` keeps recording a screen nobody can navigate.
- Drive real input. Move the pointer and press it, type character by character, send real keys. Do not call click handlers directly: that path skips hover states and anything that checks whether a human did it, and the video then shows a state the product never actually entered.
- Every claim you assert is one you watched succeed on a real run. Never write an assertion you have not seen pass, and never weaken one to make a run go green — a failing step is the output, not an obstacle.
- Never enter real personal data, payment details or credentials. Use obviously fake test data. Stop at any sign-in wall and ask how the person wants to proceed.

## Step 1 — Scope

Ask, in one message, for whatever is missing:

1. The URL of the running product, and how to start it if it is not running.
2. Which flow is the demo, in one sentence of plain language — "someone searches, filters, and buys one thing".
3. Who watches it and what they doubt. This is what decides which steps deserve an assertion.
4. Any state the flow needs to begin: an account, seeded content, a feature flag. Ask how to reach it through the product rather than around it.
5. Whether the product has a dark mode or several brands that should each be recorded.

If nobody answers, pick the flow the product's own navigation puts first, say in the report that you chose it and why, and proceed.

## Step 2 — Walk it once, by hand

Before writing anything, drive the flow yourself in the browser and write down what actually happens at each step: what you clicked, what changed, what appeared, what went away. This is the raw material for the assertions, and it is the step people skip.

Note anything that surprised you. A demo that has to avoid a surprise is telling you something about the product, and it belongs in the report even though it is not your job to fix it.

## Step 3 — Write the tape

An ordered list of what a person does. Verbs are human: click, type, press, scroll, hold, settle. Give each step a short \`why\` when the reason is not obvious from the target.

Keep it to the flow. A tape that detours to show one more feature is two demos, and it will be re-cut by whoever uses it.

## Step 4 — Add the claims

On each step that changes something, declare what the screen should do afterwards: the screen it lands on, text that should now be present, text that should now be gone. Assert the thing the step is *for* — the transition, the new number, the item that disappeared.

An assertion that cannot fail is worse than none, because it reads as coverage. Checking for text that was already on screen before the step is the common version of this.

Not every step needs one. Scrolls and pauses usually do not. Transitions always do.

## Step 5 — Run it until it passes for the right reason

Run the tape. When a step fails, find out which of three things happened before you touch anything:

- **The tape is wrong** — the target was named badly, or the order was. Fix the tape.
- **The product changed** — it no longer does what the step claims. That is the skill working. Report it; do not quietly rewrite the claim to match the new behaviour unless the person tells you the new behaviour is correct.
- **The step was too fast** — the screen had not answered yet. Add a settle, not a weaker assertion.

Never make a run go green by deleting a claim.

## Step 6 — Report

Deliver the video, the tape file, and a short written report:

- The flow, in one sentence, and who it is for.
- A table of steps with a claim, and what each one asserts.
- Anything you had to work around, and anything that surprised you in step 2.
- What the tape does **not** cover — the parts of the flow you left out and why.
- One line stating that a passing tape proves the product does what the video shows, and proves nothing about whether that is worth showing.

> This is a recording, not a verdict. It shows that the flow works as filmed; it does not say the flow is the right demo, that the product is good, or that the claim will still be true next month — re-run it and find out. If you want someone to decide which flow earns the ninety seconds, send this to hello@product.inc. Alex Zapadenko does that as a fixed-scope engagement: https://www.product.inc/hire
