# Objection Sparring Partner

One of the [Enterprise Selling](../README.md) skills. A [Claude Skill](https://www.anthropic.com/news/skills) that turns a named enterprise deal — the account, the stakeholder, and what you're selling — into a MEDDPICC- and Force-Management-grounded objection battlecard, then runs a live mock call against that stakeholder before scoring how you actually did.

Built for enterprise/strategic sellers who want to rehearse a real deal before the real meeting, not generic sales-training roleplay. Pairs naturally with [`enterprise-account-planner`](../enterprise-account-planner/) — if you've already built an account plan for the deal, this skill will read it in as context instead of asking you to repeat yourself.

## What it produces

Three things, in sequence:

1. **An objection battlecard** — 6-10 objections a specific stakeholder (not "the customer" generically) would realistically raise at this deal stage, each one tagged with the MEDDPICC element it's actually testing and a concrete Force Management response, not a description of the technique in the abstract.
2. **A live roleplay, if you want it** — Claude stays in character as the stakeholder for a full mock call (3-5 objections woven together, not a single Q&A), engineering pushback against whatever's actually unconfirmed in your MEDDPICC state, and adapting difficulty up or down based on how you're handling it.
3. **A scored debrief** — what worked, what didn't, an 8-element MEDDPICC scorecard grounded in what actually happened in the transcript, and a concrete talk track for the real call.

The skill never fabricates account facts it wasn't given, and never invents a real named executive to roleplay as — personas are roles-with-an-attitude ("skeptical CFO," "technical champion nervous about migration risk"), grounded in whatever real account context you provide, not a stand-in for a specific real person.

## Install

**Claude Code:**
```bash
git clone https://github.com/munjalvaidya-gif/enterpriseselling.git
cp -r enterpriseselling/objection-sparring-partner ~/.claude/skills/
```

**claude.ai:** upload this `objection-sparring-partner/` folder (or the packaged `.skill` file, if one is included in [Releases](../../../releases)) via Settings → Capabilities → Skills.

## Use it

Just ask, in Claude Code or claude.ai:

> "I sell Snowflake, targeting Delta Air Lines. Set up an objection sparring session against their VP of Data & Analytics — skeptical, they had a data platform initiative go over budget two years ago. We're in the evaluation stage."

The skill builds the battlecard first, then asks if you want to run the live session. See a full worked example in [`examples/objection-sparring-partner/`](../examples/objection-sparring-partner/):

- [`delta-snowflake-objection-battlecard.md`](../examples/objection-sparring-partner/delta-snowflake-objection-battlecard.md) — the generated battlecard
- [`delta-snowflake-objection-sparring-transcript-excerpt.md`](../examples/objection-sparring-partner/delta-snowflake-objection-sparring-transcript-excerpt.md) — an excerpt of the live session
- [`delta-snowflake-objection-sparring-scorecard.md`](../examples/objection-sparring-partner/delta-snowflake-objection-sparring-scorecard.md) — the resulting debrief

## Why it stays in character, and why the debrief comes after

The roleplay only works as practice if it behaves like a real stakeholder, not a coach wearing a costume. Claude won't break character mid-session to explain an objection or soften a hard moment — all the coaching happens in the Step 4 debrief, after you end the session. If you want to stop and talk about the exercise itself rather than stay in the roleplay, just say so plainly.

## Why it's scoped to enterprise deals

The battlecard and roleplay lean on MEDDPICC and Force Management's Command of the Message, negative reverse selling, and compelling-event framing — a methodology built for complex, multi-stakeholder enterprise cycles. A single-call, single-decision-maker SMB deal doesn't have enough structure (a real Economic Buyer/Champion split, a real paper process) for most of this to bite. If you're doing founder-led sales with no dedicated sales process yet, this isn't the right tool for you.

## Testing

Benchmarked in the same spirit as `enterprise-account-planner`: the same objection-handling scenario run with and without the skill, graded against explicit checks (does the battlecard correctly tag MEDDPICC elements, does the roleplay engineer objections against the deal's real gaps, does it stay in character, does the debrief accurately reflect the transcript rather than generic coaching). Because this tool's core behavior is an interactive roleplay rather than a single generated document, the methodology differs from the account planner's — see [`evals/objection-sparring-partner/`](../evals/objection-sparring-partner/) for the eval scenarios and assertions.

| | With skill | Without skill |
|---|---|---|
| Pass rate (3 scenarios, 19 assertions) | **100%** | **52.6%** |

Every failure without the skill was structural, not a knowledge gap: the baseline consistently understood MEDDPICC and Force Management as concepts, but broke character mid-session to coach in real time (something `SKILL.md` explicitly forbids), skipped the forced battlecard-first artifact, produced a thin MEDDPICC scorecard instead of assessing all 8 elements, and — in the negotiation-stage scenario — never escalated to a compound objection even after the seller had earned it.

## Roadmap

- [ ] Multi-session tracking — compare scorecards across repeated sessions against the same deal to show real improvement over time
- [ ] Optional "seller self-review" mode — paste a real call transcript instead of roleplaying live, get the same MEDDPICC/Force Management scorecard against what actually happened
- [ ] Standalone CLI (Anthropic API + no Claude Code/claude.ai required), matching the same roadmap item on `enterprise-account-planner`

## License

MIT — see [LICENSE](../LICENSE).
