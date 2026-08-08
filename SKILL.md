---
name: impeccable
description: Agency-grade frontend design and UI review. Use when the user wants to design, redesign, review, critique, audit, polish, distill, harden, adapt, animate, colorize, typeset, clarify, or otherwise improve an interface. Covers landing pages, marketing sites, dashboards, product UI, app shells, components, forms, onboarding, empty states, and error states. Handles visual hierarchy, information architecture, cognitive load, accessibility, responsive behavior, performance, theming, typography, spacing, color, motion, micro-interactions, UX copy, and design tokens. Trigger on "review this UI", "design review", "make this look better", "why does this look AI-generated", "polish this page", "make it bolder", "tone this down", "fix the spacing", "improve the typography", "audit accessibility", or any request to raise the craft level of a frontend surface. Not for backend-only or non-UI work.
---

# Impeccable (SV Academy edition)

Design and review frontend interfaces at agency standard. Real code, committed choices, no hedging.

> This is the Silicon Valley Academy edition, adapted from Impeccable by Paul Bakaus and modified. See NOTICE.md for what changed.

## How to run it

1. Read the setup gates below and pass them.
2. Route the request to a command (or handle it as a general design task).
3. Apply the design laws to everything you write or judge.
4. Report using the output contract at the bottom.

## Setup gates

Do not touch a single file before these pass. Skipping them is how you get output that looks like it was written for a different product.

**Gate 1: context.** Look for `PRODUCT.md` and `DESIGN.md` at the project root (case insensitive). Read both if they exist.

* `PRODUCT.md` carries who the users are, the brand voice, what the product refuses to be, and any anti references. If it is missing, empty, or still full of `[TODO]`, run `teach` first, then come back to the original request.
* `DESIGN.md` carries the existing color, type, elevation, and component decisions. If it is missing, say once that `document` will generate it from the code, then continue without it.

Never invent `PRODUCT.md` from the user's prompt alone. A one line request is not a product brief.

**Gate 2: reality.** If there is no `PRODUCT.md` and no `DESIGN.md`, read the actual code before opining: the root layout, the global stylesheet or theme config, and two or three representative components. Design review from imagination is worthless.

**Gate 3: register.** Decide whether this is a brand surface or a product surface before designing. Details below.

**Gate 4: shape.** For anything larger than a single component, write a short shape brief and get a yes from the user before implementing. The brief names the register, the color strategy, the theme with its reason, the type pairing, and the one thing this surface must make the visitor feel or do. Summarizing your own assumptions is not a confirmed brief.

State the gate result in one line before editing, so the user can catch a bad read early:

```text
IMPECCABLE: context=pass|teach-first register=brand|product shape=confirmed|not-required
```

## Register

Every surface is one of two things, and they follow different rules.

**Brand.** Marketing pages, landing pages, campaigns, long form content, portfolios. Design is the product. The visitor decides in two seconds whether you are serious. Take real positions: an opinionated type pairing, a color strategy that commits, scale that is genuinely large where it matters. Safe is the failure mode.

**Product.** App UI, dashboards, admin tools, settings, internal tooling. Design serves a task the user already decided to do. Every pixel either speeds up that task or gets out of the way. Decoration that slows a daily user down is a bug. Blandness is not the failure mode here, friction is.

Pick by, in order: an explicit cue in the request ("landing page" vs "settings screen"), then the surface actually in focus, then the `register` field in `PRODUCT.md`. First match wins. If you had to infer, say so in one line and move on.

## Design laws

These apply to both registers. Match the code's complexity to the aesthetic: maximalism needs elaborate implementation, minimalism needs precision. Vary your choices across projects. If your last three designs converged on the same palette and the same type stack, you are pattern matching, not designing.

### Color

* Work in OKLCH. Pull chroma down as lightness approaches either extreme, high chroma near black or white reads as garish.
* Never ship `#000` or `#fff`. Tint every neutral toward the brand hue. Chroma of 0.005 to 0.01 is plenty and it is the difference between "clean" and "unfinished".
* Choose a color strategy before choosing colors. Four levels of commitment:
  * **Restrained.** Tinted neutrals plus one accent at 10 percent or less of the surface. The product default.
  * **Committed.** One saturated color carries 30 to 60 percent of the surface. The brand default when identity matters.
  * **Full palette.** Three or four named roles, each with a job. Campaigns, and data visualization in product.
  * **Drenched.** The surface is the color. Hero sections, campaign pages.
* The "one accent at 10 percent" ceiling belongs to Restrained only. The other three break it deliberately. Do not collapse every design back to Restrained out of reflex.
* Contrast is not optional: 4.5:1 for body text, 3:1 for large text and for the boundary of any control a user has to find.

### Theme

Dark or light is a decision, never a default. Not dark because tools look serious dark. Not light to play it safe.

Before you choose, write one sentence describing the physical scene: who is looking at this, where, in what ambient light, in what mood. If the sentence does not force an answer, it is not specific enough yet.

"Analytics dashboard" forces nothing. "A founder checking yesterday's signups on a laptop in a bright cafe at 9am" forces an answer. Run the scene, not the category.

### Typography

* Body measure caps at 65 to 75 characters. Longer and the eye loses the line return.
* Build hierarchy from scale and weight together, with at least a 1.25 ratio between steps. A flat scale reads as an unstyled document.
* Two families is usually the ceiling. Three needs a reason you can say out loud.
* Line height moves inversely with size: loose for body, tight for display.

### Layout

* Vary spacing to create rhythm. Identical padding on every block is monotony, not consistency.
* Cards are the lazy answer. Use one only when the content genuinely is a separable object. Nested cards are always wrong.
* Not everything needs a container. Most things do not.
* Align to something real. If an element's left edge matches nothing else on the page, it is noise.

### Motion

* Never animate layout properties. Transform and opacity, or nothing.
* Ease out on exponential curves, quart, quint, or expo. No bounce, no elastic, no spring on a button.
* 150 to 250ms for state changes, up to 400ms for anything entering or leaving. Slower than that and the interface feels sedated.
* Honor `prefers-reduced-motion` on every animation you add.

### Copy

* Every word earns its place. No heading restated in the paragraph below it, no introduction that repeats the title.
* Error messages say what happened and what to do next. "Something went wrong" is not a message.
* No em dashes and no en dashes anywhere in UI copy. Use commas, colons, semicolons, periods, or parentheses. Also not a double hyphen standing in for one.

### Absolute bans

Match and refuse. If you are about to write one of these, stop and restructure the element instead.

* **Side stripe borders.** A `border-left` or `border-right` thicker than 1px used as a colored accent on a card, list item, callout, or alert. Replace with a full border, a background tint, a leading icon or number, or nothing.
* **Gradient text.** `background-clip: text` over a gradient. Decorative, never meaningful. Use one solid color and carry emphasis with weight or size.
* **Glassmorphism by default.** Blur and glass used as decoration. Rare and purposeful, or absent.
* **The hero metric template.** Giant number, small label, three supporting stats, gradient accent. The single most recognizable SaaS cliche.
* **Identical card grids.** The same card, icon over heading over two lines of text, repeated six times.
* **Modal as the first idea.** Modals are usually avoidance. Exhaust inline and progressive alternatives first.
* **Emoji as interface icons.** Ship a real icon set.

### The slop test

If a stranger could look at this screen and say "an AI made that" without hesitating, it failed. The bans above are the cross register version.

Then run the category reflex check. If someone could guess your theme and palette from the product category alone, observability to dark blue, healthcare to white and teal, fintech to navy and gold, crypto to neon on black, you reached for the training data average. Rewrite the scene sentence and the color strategy until the answer stops being predictable from the domain.

## Commands

Invoke as `impeccable <command> [target]`. With no command, show this list and ask what they want. If the first word is not a command, treat the whole request as a general design task under the laws above.

**Build**

| Command | What it does |
|---|---|
| `teach` | Interview the user and write `PRODUCT.md`: users, jobs, brand voice, register, anti references, what this product refuses to be. Ask, do not assume. |
| `document` | Read the existing code and write `DESIGN.md`: real color values in OKLCH, the type scale, spacing steps, elevation, component inventory. Document what is there, including the inconsistencies. |
| `shape` | Plan before code. Output the shape brief: register, color strategy, theme plus its scene sentence, type pairing, layout skeleton, the one job of this surface. Stop and wait for a yes. |
| `craft` | Shape, get confirmation, then build the feature end to end in real code. No lorem, no placeholder, no "TODO: style this". |
| `extract` | Pull the repeated values and components out into tokens and shared primitives, then update the callers. |

**Evaluate**

| Command | What it does |
|---|---|
| `review` | The full pass: heuristics, hierarchy, cognitive load, accessibility, responsive behavior, and the slop test. Findings only, no edits, unless the user asks you to fix them. |
| `audit` | The technical half alone: contrast ratios, focus order and visible focus, target sizes, semantics and landmarks, layout shift, bundle and image weight, behavior from 320px to 1920px. |

**Refine**

| Command | What it does |
|---|---|
| `polish` | The last pass before shipping. Alignment, optical spacing, hover and focus and active and disabled states, loading and empty and error states, copy. |
| `bolder` | The design is safe. Raise the contrast in scale, weight, and color commitment until it takes a position. |
| `quieter` | The design is shouting. Remove competing emphasis until one thing is clearly loudest. |
| `distill` | Cut. Remove elements, states, and options until only what earns its place remains. |
| `harden` | Make it survive reality: long strings, empty lists, failed requests, slow networks, right to left, translated copy that runs 40 percent longer. |
| `onboard` | Design the first run: empty states that teach, the shortest path to first value, no tour that nobody reads. |

**Enhance**

| Command | What it does |
|---|---|
| `animate` | Add motion that carries meaning: origin, continuity, feedback. Under the motion laws. |
| `colorize` | Introduce strategic color into a monochrome UI. Pick the strategy first, then apply it. |
| `typeset` | Fix the type: pairing, scale ratio, weights, measure, line height, optical alignment. |
| `layout` | Fix the space: rhythm, grouping, alignment, hierarchy, density. |
| `delight` | Add the one detail people screenshot. One, not five. |

**Fix**

| Command | What it does |
|---|---|
| `clarify` | Rewrite labels, help text, empty states, and error messages so they say something. |
| `adapt` | Make it work on the screens it does not work on yet, touch targets and thumb reach included. |
| `optimize` | Diagnose and fix interface performance: render cost, layout thrash, image weight, font loading, animation jank. |

## Output contract

**For a review or audit,** report findings ordered by severity, never a wall of undifferentiated notes:

```text
BLOCKER   <file>:<line>  <what is wrong>  ->  <the fix>
MAJOR     <file>:<line>  <what is wrong>  ->  <the fix>
MINOR     <file>:<line>  <what is wrong>  ->  <the fix>
```

Then a two or three sentence verdict: does this ship, and what is the single highest leverage change. Every finding names a file and a line. "The spacing feels off" is not a finding.

**For build and refine commands,** report what you changed and why in a handful of lines, then name the design decision a reviewer is most likely to push back on. Do not paste the diff into chat.

## Done looks like

* Every design choice traces to the product context or to a law above. If your only reason is "it looks better", you have not finished thinking.
* Color strategy, theme, and register were chosen out loud, not defaulted into.
* Zero absolute bans present in the code you touched.
* Contrast, focus, and target sizes verified on the real markup, not assumed.
* The slop test and the category reflex check both pass.
* No placeholder text, no dead controls, no state you did not design.
