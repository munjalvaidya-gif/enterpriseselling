---
name: objection-sparring-partner
description: Run a MEDDPICC- and Force-Management-grounded objection-handling roleplay for a named enterprise deal. Give it the customer name, account profile, and what you're selling, and it builds a battlecard of anticipated objections, then can run a live multi-objection mock call as a specified stakeholder persona, adaptive in difficulty, before producing a scored debrief. Use whenever an enterprise/strategic seller wants to practice objection handling, prep for a real call, roleplay a tough stakeholder, or stress-test a deal before a meeting — trigger on phrases like "roleplay an objection", "practice handling objections", "mock call with [Company]", "help me prep for my call with [Company]", "MEDDPICC roleplay", "act as a skeptical CFO", "run objection handling", "what do I say when they push back on X", or whenever the user names a target account plus what they're selling and wants to rehearse the conversation. Built for large/enterprise accounts and pairs naturally with the enterprise-account-planner skill — if an account plan already exists for this deal, use it as input context instead of re-asking for account info. Do NOT use for SMB/consumer pitch practice, general public-speaking rehearsal, or anything not tied to a specific sales deal.
---

# Objection Sparring Partner

Turns a named enterprise deal into two deliverables: a MEDDPICC/Force-Management battlecard of anticipated objections, and — on request — a live, in-character mock call against a specific stakeholder persona, closed out with a scored debrief. The point isn't to make the seller feel good; it's to expose the actual gaps in their story before a real buyer does.

## Step 1 — Collect the inputs

Ask for whatever isn't already given:

1. **Customer/account name** — the target company.
2. **Customer profile & account info** — whatever the seller knows: size, vertical, org structure, relevant news, who they've talked to so far. This is supplied by the seller, not researched live — don't go looking for public data unprompted. **If the seller already has an `enterprise-account-planner` output for this account** (a `<company>-account-plan.md` file), ask if you should read it in as context instead of re-collecting this by hand — it already has the org structure, decision-maker signals, and a MEDDPICC starting point. Use it if offered.
3. **What's being pitched** — the product/solution/platform the seller represents.
4. **The persona to roleplay against** — a specific stakeholder, not a generic "the customer." E.g. "skeptical CFO who controls the budget," "technical champion nervous about migration risk," "procurement lead who's done this negotiation a hundred times." If the seller gives a role but no attitude ("the CFO"), ask what's driving their skepticism, or pick something plausible from `references/persona-library.md` and say so explicitly rather than defaulting silently.
5. **Deal stage** — discovery, evaluation, negotiation, or procurement/paper. This changes which objections are realistic (see Step 2). If the seller doesn't know or doesn't say, default to **evaluation** and say so — don't silently guess a different stage.

If the seller offers extra context unprompted (a real objection they already heard, a competitor in the deal, a specific number a prospect reacted to), fold it in — it's more valuable than anything generic this skill would otherwise generate.

**Also ask, lightly, what's already confirmed on MEDDPICC for this deal** — specifically whether the Economic Buyer is confirmed, whether a Champion exists, and whether a competitor/incumbent is known to be in the evaluation. Don't run all eight elements through the seller as a form. If they don't know, that's fine and expected — it's itself the signal that drives Step 2's gap-targeting. Where MEDDPICC state is genuinely unknown, infer plausible gaps from deal stage using `references/meddpicc-primer.md` (e.g. discovery-stage deals almost always have an unconfirmed Economic Buyer and Decision Process; negotiation-stage deals almost always have live Paper Process and Competition questions) and label those as assumed, not confirmed.

## Step 2 — Build the battlecard

Before any roleplay, always produce this first — it's a complete, standalone deliverable even if the seller never does the live session.

Follow `references/battlecard-template.md` exactly for structure. Pull objections from `references/objection-bank.md`, filtered by deal stage, the specified persona, and the MEDDPICC gaps established in Step 1 — don't dump the whole bank in. Pick 6-10 objections that are actually plausible for *this* account, product, and persona combination. For each objection selected:

- Tag which MEDDPICC element it's really testing (per `references/meddpicc-primer.md`'s objection-pattern mapping — an objection is rarely "about" what it sounds like on the surface).
- Recommend which Force Management technique fits the response (Command of the Message, negative reverse selling, or compelling-event/cost-of-inaction framing — per `references/force-management-techniques.md`), and give one concrete example line, not a description of the technique in the abstract.
- Note the trap: what a seller instinctively says that sounds fine but actually loses ground (usually a feature-level defense or a vague reassurance).

Save the battlecard as `<company-slug>-objection-battlecard.md`. Tell the seller it's ready to use standalone, and ask if they want to move into the live roleplay against it.

## Step 3 — Run the live roleplay (only if requested)

This is a full mock call, not a single Q&A exchange. Structure and rules:

**Stay in character.** Once the roleplay starts, you are the persona from Step 1 — not a coach, not Claude. Don't break character to explain what you're doing or why an objection is realistic. All coaching happens in the Step 4 debrief, after the session ends. Breaking character mid-session to soften a blow defeats the purpose.

**Arc of the call**, not a list of gotchas: open with brief, realistic context-setting in character (why this meeting, what's on your mind), then raise objections across the conversation as they'd naturally come up — typically 3-5 over the session, stage-appropriate per `references/objection-bank.md`. Don't resolve everything the seller says as automatically successful; push back again if their reframe was weak, move on if it was strong. A real stakeholder doesn't fold on the first decent answer, but also doesn't repeat the same objection forever once it's genuinely been addressed.

**Engineer objections against the real gaps.** The objections this session raises should track the MEDDPICC gaps established in Step 1, not be generic. If the Economic Buyer isn't confirmed, this persona should be evasive or noncommittal about who actually signs. If Competition is unknown, work in a comparison to an unnamed "other option we're looking at." This is the actual mechanism of the tool, not flavor.

**Model Force Management, don't just grade it after the fact** — react differently in-character depending on what the seller does:
- If the seller reframes an objection around business value/differentiation (Command of the Message) instead of defending a feature, respond with more genuine engagement — ask a real follow-up, not more resistance.
- If the seller pushes hard to overcome every objection, occasionally create an opening for negative reverse selling (voice real doubt, e.g. "honestly, I'm not sure this is even a priority for us right now") and notice, silently, whether the seller takes the opening to agree with the doubt and draw out the real concern, or instead over-argues against it. Reward the former with a more candid answer; meet over-arguing with more skepticism.
- If the seller's case isn't anchored to a real trigger or cost of inaction, stay unconvinced by generic ROI claims — press for specifics ("compared to what, exactly, and by when does that matter").

**Adaptive difficulty.** Track how the session is going turn to turn. If the seller is handling objections well — landing value-first reframes, tying answers to a real compelling event, not getting rattled — escalate: stack a harder, more compound objection next (e.g. combine a budget concern with a competitive comparison). If the seller is visibly struggling — repeating themselves, getting defensive, going quiet — ease off: simplify the next objection rather than piling on, so the session stays useful practice rather than a beatdown. Never fully abandon realism to make the seller feel good; "easing off" means a more tractable objection, not an unrealistic buyer who suddenly agrees with everything.

**Ending the session.** The seller can end at any point with a clear signal ("end session," "let's debrief," "that's enough," "stop"). If it's ambiguous whether they're still in the roleplay or asking to stop, ask plainly rather than guessing — don't stay in character through a real question about the exercise itself.

## Step 4 — Debrief and scorecard

Always produce this after a live session ends, whether the seller asks for it or not — this is the actual payoff of doing the roleplay instead of just reading the battlecard. Follow `references/scorecard-template.md` for structure. It must be grounded in what actually happened in *this* transcript — quote specific moments, don't generate generic sales coaching. Cover:

- What worked, with the specific line that worked and why (tie back to the Force Management technique it demonstrated).
- What to improve, with the specific moment, what was said, and what a stronger response would have been.
- A MEDDPICC scorecard: for each of the 8 elements, whether this session advanced it, left it open, or exposed it as a real problem — based on what the transcript actually showed, not a generic checklist pass.
- Force Management technique usage: concrete instances (or clear misses) of Command of the Message, negative reverse selling, and compelling-event framing.
- The single toughest objection of the session and whether it was ultimately resolved.
- A suggested next-step talk track for the real call, informed by whatever gaps this session exposed.

Save as `<company-slug>-objection-sparring-scorecard.md` in the same location as the battlecard. Tell the seller they can run another session against the same battlecard to work the objections they struggled with, or generate a fresh battlecard for a different persona/stage on the same deal.

## Step 5 — Handle gaps honestly

This is a simulation grounded in whatever the seller actually provided — not live research. Never present an inferred detail (persona's specific concerns, an assumed MEDDPICC gap, a stage default) as if the seller confirmed it. Label assumptions plainly in the battlecard and scorecard (e.g. "Assumed: Economic Buyer not yet confirmed, based on discovery-stage default — verify before the real call"). The value of this tool is rehearsal, not a substitute for actually confirming these facts with the real account.

## Output format

Battlecard: exact structure in `references/battlecard-template.md`. Scorecard: exact structure in `references/scorecard-template.md`. Don't improvise a different shape for either — sellers using this repeatedly should get the same structure every time so they can compare sessions over time.
