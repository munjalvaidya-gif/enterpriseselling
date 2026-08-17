# Enterprise Selling

A growing collection of [Claude Skills](https://www.anthropic.com/news/skills) for enterprise/strategic B2B sellers, built on real Force Management sales methodology — MEDDPICC woven throughout, not bolted on as an afterthought. Each skill is validated with a formal benchmark (with-skill vs. without-skill, graded against objective checks), not just eyeballed.

Built and maintained by [Munjal Vaidya](https://munjalvaidya.com) — 18+ years of enterprise B2B sales (Databricks, GCP, TIBCO, DoiT).

## Skills in this repo

| Skill | What it does |
|---|---|
| [`enterprise-account-planner`](enterprise-account-planner/) | Turns a target account + vertical + what you sell into a full Force Management-style account plan with MEDDPICC baked in. Research-grounded, never fabricates facts. |
| [`objection-sparring-partner`](objection-sparring-partner/) | Turns a named deal + stakeholder + what you're selling into a MEDDPICC/Force-Management objection battlecard, then a live in-character mock call, then a scored debrief. |

The two are designed to chain together: build the account plan first, then use it as context for the objection sparring session on the same deal — no need to re-describe the account twice.

## Install

Both skills live in this one repo — clone once, then install whichever you want:

```bash
git clone https://github.com/munjalvaidya-gif/enterpriseselling.git
cp -r enterpriseselling/enterprise-account-planner ~/.claude/skills/
cp -r enterpriseselling/objection-sparring-partner ~/.claude/skills/
```

Or install just one by copying only that folder. For claude.ai, upload the individual skill folder (or its packaged `.skill` file, if one is included in [Releases](../../releases)) via Settings → Capabilities → Skills.

Each skill has its own README with detailed usage, examples, and testing results — see the table above.

## Why enterprise-scoped

Every skill here leans on methodology built for complex, multi-stakeholder B2B cycles: a real Economic Buyer/Champion split, a real decision and paper process, research-worthy public footprint. That's a deliberate scope choice, not a limitation to work around — these tools are tuned for Fortune 500/Global 2000-style accounts (or roughly $300M+ in annual revenue) where that structure genuinely exists. If you're doing founder-led sales with no dedicated process yet, this isn't the right collection for you.

## Repo layout

```
enterpriseselling/
├── enterprise-account-planner/     # skill: SKILL.md + references/
├── objection-sparring-partner/     # skill: SKILL.md + references/
├── examples/<skill-name>/          # real generated outputs per skill
└── evals/<skill-name>/             # eval scenarios + assertions per skill
```

Each skill folder is self-contained and install-clean — `cp -r` it and nothing else comes along. Examples and evals live at the repo root, namespaced per skill, so they stay out of your installed skills folder.

## Contributing

Issues and PRs welcome — this is an open-source showcase, built to be genuinely useful to other sellers, not just a demo.

## License

MIT — see [LICENSE](LICENSE).
