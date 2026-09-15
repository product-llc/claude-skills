# Claude skills by Alex Zapadenko

**UX audit skill for Claude** (`ux-audit`): A free Claude skill that does the findings pass of a UX audit: it inventories the codebase, walks the real flows in a browser, and writes an evidence-backed findings list. It does not pretend to prioritise.

Each one packages a method from [product.inc/notes](https://www.product.inc/notes) into a skill file you can run in Claude Code or claude.ai. Free, MIT, no gate.

| Skill | What it does | Page |
| --- | --- | --- |
| [`ux-audit`](ux-audit/SKILL.md) v1.1.0 | A free Claude skill that does the findings pass of a UX audit: it inventories the codebase, walks the real flows in a browser, and writes an evidence-backed findings list. It does not pretend to prioritise. | [product.inc/skills/ux-audit](https://www.product.inc/skills/ux-audit) |

## Install

**Claude Code** — from the root of the project you want it in:

```sh
mkdir -p .claude/skills/ux-audit && curl -fsSL https://www.product.inc/skills/ux-audit/SKILL.md -o .claude/skills/ux-audit/SKILL.md
```

Then ask for what the skill does, or invoke it as `/ux-audit`. Swap the slug for any other skill in the table.

**claude.ai** — download the zip from the skill's page and upload it under Settings → Capabilities → Skills.

**Skill Vault** — `sv install product-llc/<slug>`.

## Where the canonical file lives

Each skill's page on product.inc serves the same bytes as this repository (`https://www.product.inc/skills/<slug>/SKILL.md`). The site is the source; this repository mirrors it so the skill directories that index GitHub can find it, and it is updated by a script whenever a skill's version changes. Tags mark each published version.
