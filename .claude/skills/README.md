# Marketing Skills

The skill folders in this directory are installed from
[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills)
(v2.11.0, upstream commit d4ff28a) via the `skills` CLI. Claude Code loads them
automatically from `.claude/skills/`.

`product-marketing` is the foundation skill: the others read the product
marketing context file (`.agents/product-marketing.md`) first, so run that skill
once to describe the product, audience, and positioning.

## Updating

```bash
npx skills add coreyhaines31/marketingskills -a claude-code -y
```

`skills-lock.json` at the repo root records the installed source and hashes so
`npx skills update` can pick up upstream changes.
