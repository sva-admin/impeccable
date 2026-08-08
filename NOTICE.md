# NOTICE

This work is a derivative of a third-party project and is distributed under the terms of that project's license.

## Original work

**Impeccable**, by Paul Bakaus.

* Source: https://github.com/pbakaus/impeccable
* Project site: https://impeccable.style
* License: Apache License, Version 2.0
* Copyright 2025 Paul Bakaus

The full, unmodified Apache 2.0 license text ships in [LICENSE](LICENSE).

## This derivative

Copyright 2026 Silicon Valley Academy, for the modifications described below. The modifications are released under the same Apache License, Version 2.0.

This repository is the **Silicon Valley Academy edition** of Impeccable. It is not the original project, it is not maintained by the original author, and it should not be reported to him as if it were his. For the full upstream product, with its CLI, browser extension, live variant mode, and multi-harness plugin packaging, go to the original.

## Changes made in this edition

1. **Rebuilt as a single self-contained SKILL.md.** The upstream skill loads a command reference file per command and relies on Node scripts in a `.agents/skills/impeccable/scripts/` tree. This edition inlines a condensed version of that guidance into one file with no scripts, no external reference directory, and no install-time file layout requirement.
2. **Rewritten prose throughout.** Every section was reworded in Silicon Valley Academy's teaching voice for use alongside our free lessons. Structure, section order, and command grouping were reworked.
3. **Command set condensed.** The upstream command table was reduced to twenty one commands, each carrying a short inline instruction instead of a pointer to a reference file. The upstream `live` browser-iteration mode, `pin` and `unpin` management commands, and the Codex-specific preflight token were removed, as they depend on upstream tooling not shipped here.
4. **Gates rewritten.** The script-driven context loader gate was replaced with a plain read of `PRODUCT.md` and `DESIGN.md`, plus a code-reading fallback gate for projects that have neither. The image generation gate was dropped.
5. **Rules added.** Explicit contrast thresholds, motion duration ranges, a `prefers-reduced-motion` requirement, alignment and line-height rules, a ban on emoji used as interface icons, and an en dash ban alongside the upstream em dash ban.
6. **Output contract added.** A severity-ranked, file-and-line reporting format and a "done looks like" checklist, neither of which appear upstream in this form.

## Upstream third-party notices, retained

The original project's own NOTICE file records that its `skill/reference/ios.md` and `skill/reference/android.md` platform reference files are derived from `platform-design-skills` by ehmo (https://github.com/ehmo/platform-design-skills), licensed MIT. Those platform reference files are **not** included in this edition. The notice is retained here for the completeness of the attribution chain.
