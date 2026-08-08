<p align="center"><a href="https://loop.sv-academy.org"><img src="https://raw.githubusercontent.com/sva-admin/claude-skills/main/assets/sv-academy-512.png" width="96" alt="Silicon Valley Academy"/></a></p>

# impeccable

Agency-grade design review and frontend craft for your coding agent: it names what is wrong with your UI, at file and line, and then fixes it.

## Try it

Paste this into Claude Code:

```
Install the skill from https://github.com/sva-admin/impeccable, then run a full design review on my landing page and fix every blocker it finds.
```

More ways in:

```
impeccable review app/pricing/page.tsx
impeccable bolder our hero section, it is far too safe
impeccable audit the dashboard for accessibility and responsive behavior
impeccable typeset the blog post template
```

## Learn it free, step by step

[Agency-grade UI review](https://loop.sv-academy.org/articles/agency-grade-ui-review)

## What it actually does

Most AI design help returns a list of adjectives. This one returns findings you can act on.

* **It refuses to design blind.** It reads your `PRODUCT.md` and `DESIGN.md` first, or the real code if those do not exist yet. If it has no product context, it asks for it instead of inventing one.
* **It picks a register.** Marketing pages and product UI follow different rules. It decides which one you are on before it touches anything.
* **It commits.** Color strategy, dark or light, type pairing: each one is chosen out loud with a reason, not defaulted into.
* **It bans the tells.** Side stripe borders, gradient text, decorative glassmorphism, the hero metric template, the endless identical card grid. Match and refuse, every time.
* **It reports at file and line.** Blocker, major, minor, each with the fix. "The spacing feels off" is not a finding.

Twenty one commands across build, evaluate, refine, enhance, and fix. Full list in [SKILL.md](SKILL.md).

## Credit

Inspired by and adapted from [Impeccable](https://github.com/pbakaus/impeccable) by Paul Bakaus, licensed under Apache 2.0. Original project: [impeccable.style](https://impeccable.style).

This repository is the **Silicon Valley Academy edition**: a modified, self-contained single file version, rewritten in our voice for teaching. The design doctrine is adapted from the original work. See [NOTICE.md](NOTICE.md) for the list of changes and [LICENSE](LICENSE) for the terms.

## More from Silicon Valley Academy

* All of our published skills: [github.com/sva-admin/claude-skills](https://github.com/sva-admin/claude-skills)
* Courses and free lessons: [sv-academy.org](https://sv-academy.org)
