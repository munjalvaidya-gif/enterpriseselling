---
name: enterprise-account-planner
description: Build a Force Management-style enterprise account plan using the MEDDPICC framework for a named target account. Use this whenever an enterprise/strategic seller wants to plan, prospect, or strategize on a specific company — trigger on phrases like "account plan", "build me an account plan for [Company]", "MEDDPICC", "MEDDIC", "who's the economic buyer at [Company]", "help me plan my approach to [Company]", "territory plan", "strategic account review", "pre-call research on [Company]", or whenever the user names a target company plus the vertical it's in and what they're selling and wants research, decision-maker signals, tech stack intel, entry points, or a pitch strategy. Built and tuned for large, well-documented accounts — Fortune 500, Global 2000, or roughly $300M+ in annual revenue — where public information (financials, leadership, tech stack signals) is realistically findable. Do NOT use for SMB/consumer prospecting, personal shopping research, or generic company lookups with no sales motion behind them.
---

# Enterprise Account Planner

Produces a single Markdown account plan for an enterprise seller targeting a named company, structured the way Force Management trains reps to think (MEDDPICC woven throughout) and grounded in real, sourced research rather than generic filler.

## Step 1 — Collect the three required inputs

Ask for whatever the user hasn't already given you:

1. **Account/company name** — the target customer
2. **Vertical** — the industry the customer operates in
3. **What the seller sells** — the platform, product, or company the seller represents (e.g. "Snowflake," "Salesforce," "CrowdStrike"). This drives Step 4's persona/entry-point work — don't skip it.

If the user offers extra context unprompted (an existing contact, a deal stage, a specific competitor they're up against), fold it in — it's valuable and doesn't need to be asked for separately.

## Step 2 — Set expectations on scope

This plan is built for accounts large enough to have a real public footprint: Fortune 500, Global 2000, or roughly **$300M+ in annual revenue**. If the named company is clearly smaller, private, or early-stage, say so plainly before you start ("heads up — this is tuned for large enterprise accounts, so expect thinner public data here") and then proceed with what's findable. Never refuse; just set the right expectation.

## Step 3 — Research the account

Check whether your current session has web research tools available (e.g. `WebSearch`/`WebFetch` in Claude Code, or equivalent browsing in claude.ai).

**If research tools are available — use them.** Actively research, don't just reason from training data (it will be stale on leadership, funding, and reorgs). Run enough searches to cover, at minimum:
- Company overview: HQ, employee count, revenue/market cap, business lines
- Financial position: for private/PE-backed companies, funding rounds and investors; for public companies, recent earnings highlights, stock trajectory, M&A activity
- Leadership and organizational news: exec team, recent hires/departures, reorgs, layoffs — search news and press releases, not just a bio page
- Tech stack signals: job postings mentioning specific tools, engineering blog posts, conference talks, case studies published by vendors about this customer
- Recent strategic signals: earnings call priorities, press releases, product launches, stated initiatives

Prefer primary sources (company newsroom, SEC filings, earnings transcripts, LinkedIn posts from named executives) over aggregator sites. Track where each fact came from — sources get cited at the bottom of the plan.

**If no research tools are available**, don't fabricate facts to fill the template. Instead produce the full plan structure with clearly marked research prompts in place of content, e.g.:

> 🔍 **Research needed:** Search "[Company] CFO" and recent earnings calls to identify the economic buyer for a [category] purchase.

This is still a complete, usable deliverable — just one the seller (or another LLM session with browsing) finishes filling in.

Tell the user up front which mode you're using.

## Step 4 — Build the plan

Follow `references/account-plan-template.md` exactly for structure and section order — don't improvise a different shape.

Weave MEDDPICC into the plan rather than bolting it on as an afterthought; `references/meddpicc-primer.md` explains each element and which part of the research it maps to.

For **Section 6 (Entry Points & Persona to Pitch)**, use `references/platform-persona-playbook.md` to map the seller's platform to the right economic buyer, champion profile, and trigger event. If the seller's platform doesn't match a listed category, use the playbook's fallback reasoning method rather than skipping the section.

For **Section 9 (Discovery Question Guide)**, use `references/discovery-question-bank.md` to select 6-8 questions tailored to whichever stakeholder the seller is meeting first. Don't dump the whole bank in — pick questions that target whatever MEDDPICC elements ended up marked "inferred" or "No public data found," since that's genuinely useful triage, not just a template fill.

## Step 5 — Handle gaps honestly

This is a hard rule, not a style preference: **never invent facts** — no invented executive names, funding amounts, or tech stack tools. When something can't be found, write "No public data found" (live-research mode) or leave the research prompt in place (template mode). Where you're inferring something rather than stating a confirmed fact (e.g. estimating headcount trend from LinkedIn growth, or guessing stage from hiring patterns), label it explicitly as inferred so the seller knows what to verify before repeating it in a meeting.

## Step 6 — Save and hand off

Save the finished plan as `<company-slug>-account-plan.md`. If there's an obvious working directory or project already in play, save it there without asking. Otherwise — including the common case of a brand-new session with no other context — explicitly ask the user where they'd like the file saved rather than guessing at a default location; don't treat "current working directory" as self-evident when it isn't. Tell the user it's clean Markdown meant to paste directly into Notion or Google Docs, and that they can ask you to turn it into a PDF or slide deck next — that's a separate, on-request step, not something to do automatically.

## Output format

Always use the exact structure in `references/account-plan-template.md`. Don't add sections, don't remove sections, don't reorder them — sellers using this repeatedly will come to expect the same shape every time.
