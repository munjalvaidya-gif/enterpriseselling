# Enterprise Account Planner

A [Claude Skill](https://www.anthropic.com/news/skills) that turns three inputs — a target account, its vertical, and what you sell — into a full Force Management-style account plan with MEDDPICC baked in.

Built for enterprise/strategic sellers targeting large, well-documented accounts: Fortune 500, Global 2000, or roughly **$300M+ in annual revenue**, where public research (financials, leadership, tech stack signals) is realistically findable.

## What it produces

A single, clean Markdown file you can paste straight into Notion or Google Docs, covering:

1. **Customer information** — overview, HQ, size, revenue, ownership
2. **Funding & financial position** — funding rounds (private) or earnings/M&A highlights (public)
3. **Organization structure & recent changes** — leadership, reorgs, layoffs, hires
4. **Decision-maker signals** — named people, their signals, sources, and why they matter
5. **Tech stack** — what's in place today, what's adjacent/competitive, and the whitespace
6. **Entry points & persona to pitch** — the right buyer, the right champion, and the trigger event that makes now the moment to reach out, mapped specifically to what *you* sell
7. **Account penetration & expansion strategy** — the smallest viable wedge to land, and where it grows from there
8. **Key events & industry touchpoints** — conferences, summits, and other places to get a warmer entry point than a cold email
9. **Discovery question guide** — a persona-tagged question set for the first stakeholder meeting, prioritized around whatever the research couldn't confirm

...plus a **MEDDPICC snapshot** (Metrics, Economic Buyer, Decision Criteria, Decision Process, Paper Process, Identify Pain, Champion, Competition) woven from the research above, not bolted on separately.

The skill never invents facts. Where public data can't be found, it says so plainly ("No public data found") instead of guessing — and clearly labels anything it infers rather than confirms.

## Install

**Claude Code:**
```bash
git clone https://github.com/munjalvaidya-gif/enterpriseselling.git
cp -r enterpriseselling/enterprise-account-planner ~/.claude/skills/
```

**claude.ai:** upload the `enterprise-account-planner/` folder (or the packaged `.skill` file, if one is included in [Releases](../../releases)) via Settings → Capabilities → Skills.

## Use it

Just ask, in Claude Code or claude.ai:

> "Build me an account plan for Delta Air Lines, in the airline vertical — I sell Snowflake."

The skill will ask for anything missing, tell you whether it's running live web research or generating a research template (depends on whether your session has browsing tools available), and write the finished plan to `<company>-account-plan.md`.

## Why it's scoped to large accounts

Smaller and private companies simply don't have enough public footprint (org charts, press coverage, job postings, financial disclosures) for most of these sections to be worth much — the plan would be mostly "No public data found." This tool is tuned for the accounts where that research actually exists.

## Example output

Two full, real generated plans (live web research, no fabricated facts) are in [`examples/`](examples/):

- [`nike-workday-account-plan.md`](examples/nike-workday-account-plan.md) — a Workday seller targeting Nike (net-new land motion)
- [`marriott-salesforce-account-plan.md`](examples/marriott-salesforce-account-plan.md) — a Salesforce seller targeting Marriott International (existing-customer expansion motion)

## Testing

This skill was validated with a formal benchmark, not just eyeballed: the same task was run with and without the skill across 4 real Fortune 500 accounts (different verticals and platform categories, including one platform — an AI coding agent — deliberately not covered by the persona playbook, to test the fallback reasoning), graded against objective checks (real cited executives, all 8 MEDDPICC elements present, persona correctly mapped to the seller's platform, no fabricated facts).

| | With skill | Without skill (same model, no skill) |
|---|---|---|
| Pass rate | **100%** | 80.2% |

The gap was almost entirely one thing: without the skill, the model consistently skipped building a real MEDDPICC breakdown — good research, but missing the sales-methodology structure that's the actual point of this tool.

## Roadmap

- [ ] Standalone CLI (no Claude Code/claude.ai required) using the Anthropic API + web search, for sellers who want to run this outside a Claude session
- [ ] Optional PDF/slide export helper script

## Contributing

Issues and PRs welcome — this is an open-source showcase, built to be genuinely useful to other sellers, not just a demo.

## License

MIT — see [LICENSE](LICENSE).
