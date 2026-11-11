---
doc: prd
status: draft
---

# Shopping Assistant — Product Requirements

A phone-friendly helper for anyone who doesn't think about clothes: it learns your body and style once, then gives a plain-language verdict on each item you photograph in a store.
Source: `scope.md > The Unique Kernel`, `scope.md > The Core Loop`.

## The Core Journey
1. **Welcome:** a first-time user sees bullet points of what building a profile involves, and a **Build my profile** button.
2. **Build profile, step by step** (one screen per step):
   - Your name (free text)
   - Body photos (faceless)
   - A photo of your skin that shows your skin color
   - Height (free text)
   - Style preferences (see `Building a Profile` below)
3. **Profile summary:** the helper shows what it worked out about you. If something is wrong, you redo that step.
4. **Home:** "Hi [name]" and a **Go shopping** button.
5. **Go shopping:** an optional "anything specific today?" If skipped, the goal is versatile clothes. The trip starts.
6. **Check an item:** opens the phone camera. Take a photo of a shirt, pant, shoes, etc.
7. **Verdict:** the item is judged against your profile and everything already bought on this trip.
8. **Act on the verdict:** mark it **bought**, or, on a Close verdict, **keep it** to look for in another store. Back to Home. Repeat steps 6–8.
9. **Done shopping:** ends the trip and clears it.

## Screens and Layout
Source: `scope.md > The POC Boundary` (usable on a phone in the store).

All screens are vertical, one-handed, phone-first.

- **Welcome:** what building a profile involves (bullets) and **Build my profile**.
- **Profile steps:** one screen each for name, body photos, skin photo, height, style.
- **Profile summary:** body, skin tone, style as worked out by the helper; each with a way to redo that step.
- **Home, between trips:** "Hi [name]" and **Go shopping**.
- **Trip goal prompt:** "anything specific today?" with a free-text answer and a way to skip.
- **Home, during a trip:**
  - "Hi [name]"
  - **Check an item** (big, opens the camera)
  - **Done shopping**
  - **Bought items** — only shown once something is bought. Each entry: picture, short name (e.g. "Navy chinos"), and a one-line note on how it fits the trip (e.g. "Pairs with the oxford"). Each can be deleted.
  - **Still looking for** — only shown once something is kept. Each entry: the item and what to look for (e.g. "Oxford shirt — in navy or olive"), with **Found it**.
- **Camera:** take the item photo.
- **Verdict:** see `The Verdict`.
- **Delete confirmation:** "Remove [item] from bought items?" with confirm and cancel.

`planning/home-mockup.html` shows the in-trip Home roughly, but predates these decisions: it still has Recent verdicts, trip details, a profile card and tab, and the old styling. It is a reference, not the spec.

## Look and Feel
- **Direction: B · Warm & friendly** (sample in `planning/look-samples.html`), chosen for now and open to revisiting.
- Cream background, terracotta accent, rounded letters, soft rounded cards, pill-shaped buttons.
- Encouraging and casual, like a friend cheering you on, while still saying "skip this one" plainly (`scope.md > Inspiration & Identity`).
- Avoid: fashion jargon, generic AI-app styling.

## Features and Behavior

### Building a Profile
Source: `scope.md > The POC Boundary`.
- Whatever can be worked out from photos is; the user only types what a photo can't show (name, height).
- **Style step:** picture cards with captions ("this is minimal style", …). The user taps the ones they like. A free-text field covers anything the pictures miss. The cards don't need to be exhaustive. Their reactions, the free text, and the summary check together are enough.
  - [ ] Completing every step leads to the profile summary.
  - [ ] Tapping style cards visibly marks them selected; the free text is kept.

### Profile Summary
- After setup, the helper shows the profile it built (body, skin tone, style) so the user can check it.
- If something is wrong, the user redoes that step.
  - [ ] The summary reflects the photos and answers given (e.g. a skin tone and style that match them).
  - [ ] Redoing a step changes the summary.

### Home
- Greets the user by the name from their profile.
- Between trips: **Go shopping** only.
- During a trip: **Check an item**, **Done shopping**, **Bought items**, **Still looking for**, as in `Screens and Layout`.
  - [ ] "Hi [name]" shows the name typed during setup.
  - [ ] With no trip, Home shows only the greeting and **Go shopping**.
  - [ ] The Bought items and Still looking for sections don't appear until they have something in them.

### Shopping Trip
Source: `scope.md > The Core Loop` steps 2–4.
- **Go shopping** starts a trip; **Done shopping** ends it.
- **Go shopping** asks an optional "anything specific today?" If the user skips it, the goal is versatile clothes.
- Items marked **bought** are remembered for the rest of the trip, and each later verdict takes them into account.
- The trip (bought and kept items included) survives closing the app; only **Done shopping** clears it.
  - [ ] After buying a shirt, a later verdict on a pant mentions whether it goes with that shirt.
  - [ ] Closing and reopening the app mid-trip shows the same Home, bought and kept items intact.
  - [ ] After **Done shopping**, Home is back to **Go shopping** with nothing carried over.

### The Verdict
Source: `scope.md > The Unique Kernel`.
- Three outcomes: skip it / close (e.g. "look for it in navy or olive") / buy it.
- Plain language; unfamiliar terms are shown visually, not just named.
- Layout: big Yes / No / Close at the top; a few plain sentences of reasoning (body shape, color vs skin, style, items bought this trip); Close says what to get instead.
- Visuals only for unfamiliar terms: color swatches or small reference pictures, not generated images.
- Actions: **Mark bought**; on a Close verdict also **Keep looking** (save it to Still looking for); and a way back to check another item.
- A bad photo (blurry, dark, not clothing) gets "Bad photo, try again."
  - [ ] Every verdict shows exactly one of the three outcomes, at the top.
  - [ ] Any color or style term in the reasoning has a swatch or small picture beside it.
  - [ ] A Close verdict says what to look for instead.
  - [ ] A photo of something that isn't clothing gets "Bad photo, try again", not a verdict.

### Bought Items
- **Mark bought** adds the item to Bought items with a picture, short name, and one-line note.
- An item can be deleted from Bought items after a confirmation. A deleted item is forgotten: later verdicts no longer take it into account.
  - [ ] Deleting asks for confirmation first; cancel leaves it in place.
  - [ ] After deleting a shirt, a later verdict no longer mentions it.

### Still Looking For
Source: `scope.md > The Core Loop` step 3 (the "close: look for it in X" verdict).
- On a Close verdict, the user can choose **Keep looking** when they really like an item but something is missing (usually the color), so they can look for it in other stores. Nothing is kept automatically; Skip verdicts are never kept.
- Each kept item shows what to look for.
- **Found it** moves the item into Bought items, showing the variation that was looked for (e.g. "Oxford shirt, navy"), and it then counts in later verdicts like any bought item.
- Kept items last only for the trip; **Done shopping** clears them.
  - [ ] Only Close verdicts offer **Keep looking**.
  - [ ] A kept item appears under Still looking for with what to look for.
  - [ ] **Found it** removes it from Still looking for and adds it to Bought items.

## States and Boundaries
- **First use (no profile):** the app opens on Welcome.
- **Between trips:** Home with "Hi [name]" and **Go shopping**.
- **Trip in progress:** Home with the trip controls; empty sections stay hidden.
- **Bad photo:** "Bad photo, try again"; nothing is added to the trip.
- **What persists:** the profile, and the current trip (bought and kept items) across closing the app.
- **What disappears:** everything in a trip on **Done shopping**; a bought item on confirmed delete; checked items that weren't bought or kept.
- **Who it's for:** anyone sets up their own profile; nothing is tailored to one person (`scope.md > The POC Boundary`).

## Product Decisions
- Name: "Shopping Assistant" for now.
- Style choice by pictures with captions, plus free text: the learner can't pick a style from words alone.
- Correcting the profile means redoing the step.
- The user ends a trip by tapping **Done shopping**.
- No try-on images (pictures of the user wearing the item): not essential, costly, and they raise privacy issues.
- Designed for a phone screen first (vertical, one-handed, used standing in a store); desktop is not a target for the proof of concept. Whether it's a mobile web app or a native app is decided in `4-spec`; the design is the same either way.
- The phone camera is opened from a web page (exact method is decided in `4-spec`).
- **Look and feel: B · Warm & friendly**, for now — see `Look and Feel`.
- **Greet by name** ("Hi [name]"), so setup asks for a name.
- **No list of past verdicts.** Bought items speak for themselves; items not bought are dropped unless kept.
- **Keep looking, by choice:** only Close items the user really likes get kept, so the list stays short and is useful across stores.
- **Found it is a tap, not automatic matching:** one extra tap, but never wrong (the app doesn't have to guess two similar items are the same).
- **Deleting a bought item needs confirmation and makes it forgotten,** for a mis-tap or an item put back at the till.
- **Left off Home for now:** trip start time and goal tag; a profile card and Profile tab.

## What We're Building
- Welcome and the step-by-step profile (name, body photos, skin photo, height, style cards + free text).
- Profile summary with redo per step.
- Home in its two states, greeting by name.
- Starting a trip with the optional goal; ending it with **Done shopping**.
- Camera → verdict (skip / close / buy) with plain reasoning, visuals for unfamiliar terms, and the bad-photo message.
- Bought items (add, delete with confirmation, counted in later verdicts).
- Still looking for (keep on Close, **Found it**, cleared at trip end).
- The trip surviving the app being closed.
- Warm & friendly styling, phone-first.

## Deferred From the POC
- **Knowing your wardrobe** (what's already at home): needs a full catalog first and a second matching system (`scope.md > Later`).
- **Accounts, privacy, and hosting for the public:** private, separated storage of each person's body photos (`scope.md > Later`).
- **How it's distributed** (hosted web app vs. open source to run yourself): decide once the core works (`scope.md > Later`).
- **Editing the profile any time** (profile card / tab): for now you correct it from the summary during setup.
- **A history of every verdict on a trip:** dropped in favor of Bought items + Still looking for.

## Possible Later Enhancements
- Trip details on Home (when it started, the goal).
- Automatically recognizing that a newly checked item is one you were looking for.
- Removing a kept item mid-trip without finding it.

## Non-Goals
- Try-on images of the user wearing the item: costly, privacy issues, not needed to decide.
- Generated images: visuals are swatches and small reference pictures.
- Desktop layout: the PoC is for a phone in a store.
- Fashion vocabulary without explanation: the whole point is plain language.

## Open Questions
- **Camera button label:** "Check an item" (current) vs. "shop item" (the learner's phrasing). Can wait for the build.
- **Assumption — Mark bought on every verdict:** the user can mark a Skip item bought (it's their choice). Can wait; confirm at review.
- **Assumption — kept items can't be removed mid-trip** except by **Found it**; they clear at **Done shopping**. Can wait.
