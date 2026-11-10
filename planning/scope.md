---
doc: scope
status: approved
---

# Shopping Assistant (working name)

An in-store helper for people who don't think about clothes: photograph an item and it tells you, in plain language, whether to buy it, skip it, or look for a variation.

## The Unique Kernel
A clear verdict that's personal and easy to understand. The helper already knows your body, skin tone, height, style, and what you're shopping for, so it gives one of three answers: **skip it**, **close: look for it in X or Y color**, or **buy it**. It explains why without fashion jargon, and when it has to use a term (a color name, a collar style) it **shows** you what that means instead of just naming it.

## Who It's For
Anyone with this problem, starting with the learner. Nothing is hard-coded to one person: each user gives the helper their own context, and it works from that. The typical user is someone who doesn't think about clothes and can't tell which shirt is better, which suits their style, or which looks good on them. Today they wander a store for hours, try many items, and leave with nothing or buy something just to buy something. They tried photographing clothes and asking a general AI "should I buy this?", but it was too vague, used jargon, and named colors and styles they didn't recognize.

"If it can work for me, why wouldn't it work for others if they have the same problem as mine?"

## The Core Loop
1. **Once:** set up a profile with faceless body photos, height, and style preferences (e.g. "minimal but stylish, not over the top, not old-fashioned").
2. **Each trip (optional detail):** usually the goal is just "good clothes I can wear for many occasions," not one specific event. That's the default. When there *is* a specific need, you can say so, e.g. "semi-formal for conferences, dates, office parties: a couple of shirts, a pant, shoes."
3. **In the store, item by item:** take a photo, get the verdict and a plain explanation, and check visual examples of anything unfamiliar.
4. **During the trip:** the helper remembers what you've bought, so later verdicts account for it (e.g. "this pant works with the shirt you bought earlier").

## Inspiration & Identity
Plain, direct, no jargon. It should feel like a friend who knows clothes and is honest: "skip this one" is said clearly. Explain things as if the user knows nothing about fashion, and show rather than name.

## Why This Matters to the Learner
"I just want to solve this problem… Build a solution, build an effective solution, whatever that might be." It's their own recurring frustration, and they want it to work "for me and for the others as well."

## What "Working" Looks Like
The assistant helps them decide whether to buy something. With a profile set up, they photograph an item and get a verdict they understand and trust: skip it, buy it, or "this would work in navy instead." Any unfamiliar term comes with a visual. A later item's verdict takes the earlier purchase into account.

## The POC Boundary
- Works for any user: each person sets up their own profile, and nothing is tailored to one individual. A friend can set up their own profile and get verdicts about their body and style.
- Usable on a phone in the store: take a photo, read the verdict
- One-time personal profile: faceless body photos, height, style preferences
- A flexible goal for each trip: defaults to "versatile clothes for many occasions," with an optional specific occasion or item list
- Photo of an item → skip / close-with-change / buy verdict and a plain-language explanation
- Visual explanation of jargon (colors, cuts, collar styles, etc.)
- Memory of items bought during the current trip only, used in later verdicts

## Later
- **Knowing your wardrobe:** what's already in your cupboard. Valuable, but it needs a full catalog up front and adds a second matching system before the core is proven. (The learner owns only a few items right now anyway.)
- **Privacy and sign-up for the public:** accounts, private and separated storage of each person's body photos, hosting for strangers. Important, but a problem for later.
- **How to distribute it:** a hosted web app vs. open source that people clone and run themselves (which helps with privacy). Decide once the core works.

## Explicitly Cut
- Nothing cut outright yet. Everything outside the boundary is under **Later**.
