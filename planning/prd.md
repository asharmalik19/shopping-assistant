---
doc: prd
status: draft
---
<!-- Partial draft saved mid-interview (last updated 2026-11-09). Sections marked OPEN are still being decided. -->

# Shopping Assistant — Product Requirements

A phone-friendly helper for anyone who doesn't think about clothes: it learns your body and style once, then gives a plain-language verdict on each item you photograph in a store.
Source: `scope.md > The Unique Kernel`, `scope.md > The Core Loop`.

## The Core Journey
1. **Welcome:** a first-time user sees bullet points of what building a profile involves, and a **Build my profile** button.
2. **Build profile, step by step** (one screen per step):
   - Body photos (faceless)
   - A photo of your skin that shows your skin color
   - Height (free text)
   - Style preferences (see Style step below)
3. **Profile summary:** the helper shows what it worked out about you. If something is wrong, you redo that step.
4. **Home:** a **Go shopping** button starts a shopping trip.
5. **Check an item:** opens the phone camera. Take a photo of a shirt, pant, shoes, etc.
6. **Verdict:** the item is judged against your profile and everything already bought on this trip. 
7. **Mark as bought:** if you buy it, it's added to the trip. Repeat steps 5–7.
8. **Done shopping:** ends the trip.

## Features and Behavior

### Building a Profile
Source: `scope.md > The POC Boundary`.
- Whatever can be worked out from photos is; the user only types what a photo can't show (e.g. height).
- **Style step:** picture cards with captions ("this is minimal style", …). The user taps the ones they like. A free-text field covers anything the pictures miss. The cards don't need to be exhaustive. Their reactions, the free text, and the summary check together are enough.

### Profile Summary
- After setup, the helper shows the profile it built (body, skin tone, style) so the user can check it.
- If something is wrong, the user redoes that step.

### Shopping Trip
Source: `scope.md > The Core Loop` steps 2–4.
- **Go shopping** starts a trip; **Done shopping** ends it.
- Items marked **bought** are remembered for the rest of the trip, and each later verdict takes them into account.
- **Go shopping** asks an optional "anything specific today?" If the user skips it, the goal is versatile clothes.
- The trip (including bought items) survives closing the app; only **Done shopping** clears it.

### The Verdict
Source: `scope.md > The Unique Kernel`.
- Three outcomes: skip it / close (e.g. "look for it in navy or olive") / buy it.
- Plain language; unfamiliar terms are shown visually, not just named.
- Layout: big Yes / No / Close at the top; a few plain sentences of reasoning (body shape, color vs skin, style, items bought this trip); Close says what to get instead.
- Visuals only for unfamiliar terms: color swatches or small reference pictures, not generated images.
- A bad photo (blurry, dark, not clothing) gets "Bad photo, try again."

## Product Decisions
- Name: "Shopping Assistant" for now.
- Style choice by pictures with captions, plus free text: the learner can't pick a style from words alone.
- Correcting the profile means redoing the step.
- The user ends a trip by tapping **Done shopping**.
- No try-on images (pictures of the user wearing the item): not essential, costly, and they raise privacy issues.
- Designed for a phone screen first (vertical, one-handed, used standing in a store); desktop is not a target for the proof of concept. Whether it's a mobile web app or a native app is decided in `4-spec`; the design is the same either way.
- The phone camera is opened from a web page (exact method is decided in `4-spec`).

## Open Questions
- **Look and feel (in progress; resume here).** The learner said they're "clueless" about design and want to explore and learn rather than answer quickly. Four sample directions for the verdict screen are in `planning/look-samples.html`: A calm & clean, B warm & friendly, C bold & confident, D boutique/magazine. Waiting on: which one feels right, and anything to mix in from the others. The learner has since added a design MCP server (Banani) and may want to use it here.
- After look and feel: write the full PRD (fill in Screens and Layout, States and Boundaries, What We're Building, Deferred, Non-Goals), then do the HTML review (`planning/prd.html`).
