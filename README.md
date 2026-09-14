# Claude skills by Alex Zapadenko

Skill files that package a method from [product.inc/notes](https://www.product.inc/notes) into something you can run in Claude Code or claude.ai. Free, MIT, no gate.

| Skill | What it does | Page |
| --- | --- | --- |
| [`ux-audit`](ux-audit/SKILL.md) | The findings pass of a UX audit: inventories a codebase, walks the real flows in a browser, and writes an evidence-backed findings list. It delivers findings, not priorities. | [product.inc/skills/ux-audit](https://www.product.inc/skills/ux-audit) |

## Install

**Claude Code** — from the root of the project you want audited:

```sh
mkdir -p .claude/skills/ux-audit && curl -fsSL https://www.product.inc/skills/ux-audit/SKILL.md -o .claude/skills/ux-audit/SKILL.md
```

Then ask for a UX audit in that project, or invoke it as `/ux-audit`.

**claude.ai** — download the zip from the [skill page](https://www.product.inc/skills/ux-audit) and upload it under Settings → Capabilities → Skills.

## Where the canonical file lives

Each skill's page on product.inc serves the same bytes as this repository (`https://www.product.inc/skills/<slug>/SKILL.md`). The site is the source; this repository mirrors it so skill directories that index GitHub can find it. Versions are in each file's page.

## Why the skill stops where it does

A UX audit is two jobs: finding what is wrong, and deciding what to fix first. The skill does the first thoroughly and does not pretend to do the second — priorities depend on what the business is trying to do. The reasoning is in [How I run a UX audit with Claude](https://www.product.inc/notes/ux-audit-with-claude).
