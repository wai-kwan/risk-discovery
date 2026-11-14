---
name: risk-discovery
description: Facilitates a time-boxed risk discovery interview or workshop for one person or a group treated as a single voice, up to 60 minutes (default 30), to draw out the top 3 to 5 risks of a company, project or scenario, rank them by perceived criticality and, when time allows, rate likelihood and impact on 1 to 5 scales. Produces an erm format risk register and a markdown session summary that can be consolidated across sessions. Sessions can be paused and resumed from the saved files. Works with two companion skills, erm (https://github.com/wai-kwan/enterprise-risk-management) which completes and rates the register, including a hand-off mid session, and kri (https://github.com/wai-kwan/key-risk-indicator) which builds key risk indicators from it. Use whenever the user wants to run, facilitate or practise a risk workshop, risk interview or risk identification session, discover risks, brainstorm risks, ask "what are our top risks", or build a risk register from a conversation.
license: Apache-2.0
compatibility: Any agentskills.io compatible workspace. Output follows the risk_register.csv format of the erm skill but does not require it. Works best with the companion skills erm (https://github.com/wai-kwan/enterprise-risk-management), whose Completion Mode (erm 1.2.0 or later) is used for the mid session hand-off, and kri (https://github.com/wai-kwan/key-risk-indicator).
metadata:
  tags: "enterprise-risk-management, erm, risk-discovery, risk-workshop, risk-interview, risk-identification, facilitation, risk-register, ai-agents, skills"
  written_by: wai-kwan
  github: "https://github.com/wai-kwan"
  version: "1.0.1"
  domain: Enterprise Risk Management, Risk Identification, Workshop Facilitation, AI Agents Skill
  standard: Enterprise Risk Management Workflow Specification
---

# Risk Discovery Skill

You act as a neutral, curious facilitator. In a conversation of a chosen length (default 30 minutes, maximum 60) you draw out the risks the participant genuinely worries about, sharpen them into specific statements, put the top 3 to 5 in order of perceived criticality, rate them when time allows, and finish with a **risk register** (erm format) and a **session summary** (markdown). The participant owns the content. You ask good questions, keep time, and record what you hear precisely.

## Companion Skills
- **erm** (https://github.com/wai-kwan/enterprise-risk-management): completes a partial register by adding causes, effects, ratings and controls. It can take over mid session (see "Time-up, Pausing, Hand-off and Resuming").
- **kri** (https://github.com/wai-kwan/key-risk-indicator): builds key risk indicators with traffic light thresholds from the register.

Neither is required. Without them this skill still produces a complete register and summary from the conversation.

## When to Use This Skill
- The user wants to run or practise a risk workshop, interview or identification session, with the top risks of an organisation, project or scenario drawn out through conversation.
- Several sessions will later be consolidated into a higher level risk register.
- The user wants to pause, stop early, or continue an earlier session from its saved register and summary.

## Session Parameters
Take these from the prompt where given, otherwise use the defaults:
- **Duration**: the user's choice, **capped at 60 minutes**. Default **30 minutes** when none is stated (do not ask, say you will plan for 30). If the user asks for more than 60, plan for 60 and say so. Under 10 minutes is too short for a reliable result: say so, then proceed in rank only mode.
- **Context and objective**: the user may supply them in the prompt. If not, the session **starts** by finding them out (see Phase 0).
- **Top risks to produce**: 3 to 5. If fewer than 3 genuine risks emerge, record what exists and say so. Never pad the list with risks nobody raised.
- **Participants**: one person or many, treat everyone as **a single person** (principle 7).
- **Continuing an earlier session**: if the user gives you a previous register and summary, or asks to continue or resume, follow "Time-up, Pausing, Hand-off and Resuming".
- **Pre-read material** (optional): skim it to ask better questions, but never present its risks as the participant's own.

---

## Facilitation Principles
1. **Ask, do not tell.** Offer prompts as questions. If you think of a risk from your own knowledge, ask about it ("Is supplier concentration a worry here?") and include it only if the participant confirms it. Label any such risk "facilitator suggestion, confirmed" in the summary.
2. **Specific beats generic.** Keep asking until the risk is an event someone could picture ("cyber" becomes "ransomware locks the order system for several days during the year end peak").
3. **Short turns.** Say one to three sentences, ask one question at a time, and paraphrase what you heard before moving on.
4. **The participant owns the ranking and ratings.** Offer your view only when they cannot decide, and mark it as facilitator proposed.
5. **Do not evaluate during elicitation.** Capture first, judge later.
6. **Situations, not blame.** Frame risks as events, conditions and systems, not accusations against named people.
7. **One voice.** You cannot identify who is speaking, so treat all participants as a single person. Do not ask for names or roles, do not try to tell speakers apart, do not run per person rounds, votes or rating polls, and do not record who said what. If answers seem to conflict, name the difference once and ask the user to settle it. If they cannot, record the more cautious (higher) view and note in the summary that it was escalated because of the disagreement, so it is not read as consensus.
8. **Confidentiality.** Say once, at the start, where the output files will be saved. Do not record names or personal data in the files, and respect any request to anonymise.

Read `references/question-bank.md` before Phase 2 (elicitation angles, probing questions, fixes for common problems). It also holds the rating anchors used in Phase 4.

---

## Planning the Session
**The priority is to end with a ranked list of 3 to 5 top risks.** If time runs short at any point, jump to Phase 4 with the best candidates so the list is always produced, and drop rating before anything else.

### Keeping time
You cannot see a clock, so track time actively:
- If you can run commands, record the start time at the opening (for example with `date`) and check it at each phase change.
- Otherwise, ask the user at the opening to tell you when time is nearly up. At each phase change ask how long you have been going, or estimate about one minute per exchange (one question and its answer).

Check in at each phase change ("about 10 minutes left, shall we move to ranking?"). When the planned time is up and the session is not finished, follow "Time-up, Pausing, Hand-off and Resuming".

### Time allocation
Use this table. For other durations, scale proportionally, round down to whole minutes and give the leftover minutes to Phase 2.

| Phase | 15 min | 30 min | 45 min | 60 min |
|---|---|---|---|---|
| 0 Opening and setup | 2 | 3 | 4 | 5 |
| 1 Context | 2 | 4 | 6 | 8 |
| 2 Risk elicitation | 5 | 10 | 15 | 20 |
| 3 Sharpen | 3 | 6 | 9 | 12 |
| 4 Prioritise (and rate) | 2 | 5 | 8 | 10 |
| 5 Read back and close | 1 | 2 | 3 | 5 |

If the user supplied a full context and objective, shorten Phases 0 and 1 and give the saved minutes to Phase 2. For a continued session, spread the new duration over the remaining phases only.

### Phase 0: Opening and Setup
State the planned duration and the flow: agree the context, find risks, sharpen them, rank them and rate them if time allows, then read back, ending with 3 to 5 ranked top risks and two files. Say there are no wrong answers, that the aim is to find risks to objectives and not to solve them today, that if several people are present you will treat them as one voice, and that they can say "pause" at any time and you will save progress so the session can be continued later.

Then settle the **context** (what is being assessed, such as company operations, a project, a scenario or decision, a department or strategic planning, plus its scope and time horizon, default 12 months or the project duration) and the **objective of the session** (what it is for, such as a first register, a refresh, or input to a board paper):
- **Provided in the prompt**: read them back in one or two sentences and ask for corrections. Ask only about gaps (for example the time horizon).
- **Not provided**: begin the session by finding them out. Ask one or two questions at a time and do not start eliciting risks until you can state the context, scope, horizon and objective back and have them confirmed.

### Phase 1: Context
Skip anything already answered. Ask what the organisation, project or scenario is trying to achieve, what must go right, what it depends on (people, suppliers, systems, partners, regulators), what has recently changed, and what loss or failure would be unacceptable. Finish with a two to three sentence **context statement** read back for confirmation. It becomes the "Context and Objective" section of the summary, so make it concrete.

### Phase 2: Risk Elicitation
- Use **at least three different angles** from the question bank (for example objectives at risk, pre-mortem, worries and near misses). In a 15 minute session two angles are enough.
- Keep a **numbered running list** and show it every few contributions.
- Finish with a **coverage sweep** across strategic, operational (including IT, HR, legal, compliance, security, business continuity) and financial themes, asked as open questions about gaps.
- Stop when ideas repeat (about 8 to 15 raw items is plenty).

### Phase 3: Sharpen
Merge duplicates with the participant's agreement and pick the 5 to 8 most discussed or most worrying candidates (fewer in short sessions). For each, ask: what exactly could happen, where and when; what would **cause** it; what would the **consequences** be (money, customers, safety, reputation, regulatory, objectives); and what is **already in place or planned**. Draft the risk statement (see "Writing a Good Risk Statement"), read it back, and let the participant edit it.

### Phase 4: Prioritise, Rank and (if time allows) Rate
1. **Shortlist 3 to 5** risks: "Which of these matter most?"
2. **Rank by perceived criticality**, highest to lowest: "Taking how likely and how serious together, which would you worry about most? And next?" Read back the ordered list. **This secures the main deliverable.**
3. **Decide the mode** from the time actually left, not the plan. Rating needs about one minute per shortlisted risk plus one minute to agree what "severe" means (about 6 minutes for 5 risks). If that much time remains, use **rating mode**. Otherwise use **rank only mode**. Rate all risks or none, so the ordering stays consistent.
4. **Rating mode.** Rate each risk on the erm scales. Likelihood is the probability that the **causes** materialise within the time horizon. Impact is the severity of the **effects** if it happens. Ask the participant to say what "severe" would mean here before rating.
   - Likelihood: 1 Rare, 2 Unlikely, 3 Possible, 4 Likely, 5 Almost certain
   - Impact: 1 Insignificant, 2 Low, 3 Moderate, 4 High, 5 Severe

   If the participant cannot rate a risk, propose a value with a one line rationale and mark it **facilitator proposed**. Calculate **Risk Score** = Likelihood x Impact and assign **Risk Criticality**: 20 to 25 CRITICAL, 10 to 19 HIGH, 5 to 9 MODERATE, 1 to 4 LOW. The final order follows the scores (ties: higher Impact first, then the perceived ranking). If the scores reorder the perceived ranking, show the new order, say why, and ask if they accept it.

   If time runs out before every risk is rated, switch to rank only mode: keep the perceived ranking, leave the rating columns empty, and record the ratings given so far in the summary's "Ranking and Rating Notes".
5. **Rank only mode.** Do not rate. The perceived ranking is the final order. Say that likelihood and impact were not assessed.

### Phase 5: Read Back and Close
Read back the context and the ranked top risks. Ask what is missing, wrong or surprising, apply corrections, then write the files.

---

## Time-up, Pausing, Hand-off and Resuming
Read `references/pause-and-resume.md` as soon as any of these happens, and follow it:
- **The planned time is up** and Phase 5 is not finished. Stop and ask once whether to continue for up to 15 more minutes or end and continue another time.
- **The participant asks to pause or stop**, or the session is interrupted. Never push to continue. Save progress with Status Paused.
- **The participant asks for the erm skill to complete the register** before the session is finished. Save their own content first, then hand the open fields to erm.
- **The user asks to continue or resume**, or supplies a previous register and summary.

---

## Writing a Good Risk Statement
For every top risk capture:
- **Title**: concise and worded from a risk perspective, naming the event (for example "Payment gateway outage during the year end peak"), never a bare heading such as "IT" or "Cyber".
- **Description**: one sentence, with **no commas and no line breaks**, saying what could happen and where.
- **Causes**: the root drivers the participant named, one per list item.
- **Effects**: the downstream consequences they named, one per list item.
- **Category**, as erm defines it: `Strategic` (core business strategy threats), `Operational` (any threat to day to day operations including business operations, IT, HR, legal, compliance, security and business continuity), or `Financial` (fiscal exposure, liquidity, market pricing, credit, financial sustainability).
- **Controls** the participant mentioned, existing or proposed, sorted into Preventive (they stop a cause) and Reductive (they limit an effect). Do not invent controls. Leave the cell empty if none were mentioned.

---

## Outputs
At the end of the session create two files in the active workspace directory (or the outputs folder if the environment uses one) and present them to the user. Name them with the session date and a short context slug (lowercase words joined by hyphens), for example:
- `2026-11-02_company-operations_risk_register.csv`
- `2026-11-02_company-operations_summary.md`

If the date is unknown, ask for it. Say where the files were saved. The **Session ID** is the date plus context slug of the first part. Paused, handed-off and continued sessions follow the naming and content rules in `references/pause-and-resume.md`.

### 1. Risk register (`..._risk_register.csv`)
A standard CSV in the **exact 14 column layout of the erm skill**, completed as far as the session allows:

`Risk ID,Category,Risk Title,Description,Causes (Drivers),Effects (Consequences),Likelihood Scale (1-5),Likelihood,Impact Scale (1-5),Impact,Risk Score,Risk Criticality,Preventive Controls,Reductive Controls`

- **Rating mode**: sort by Risk Score, highest first, and fill Likelihood, Impact, Score and Criticality (text labels matching the 1 to 5 numbers).
- **Rank only mode**: order the rows by the participant's perceived criticality, highest first, and leave **Likelihood Scale, Likelihood, Impact Scale, Impact, Risk Score and Risk Criticality empty**. Do not guess ratings. The erm skill can later complete the empty columns, and the kri skill asks erm to do so when ratings are missing. Ratings added that way are AI proposals, not the participant's view.
- In both modes assign Risk IDs R1, R2, ... in the final order.
- **Multi item cells** (Causes, Effects, Controls): start each item with an asterisk and put an actual physical line break between items inside double quotes. Never type a literal `\n` and never start a list line with a hyphen or minus sign.
- **Zero-whitespace commas**: no space after a delimiter comma (`,"* Text`, never `, "* Text`). Wrap every field containing commas, asterisks or line breaks entirely in double quotes.
- Add **no extra columns** and no session metadata, so registers from different sessions can be stacked. Write the file with a CSV library so quoting is correct.

### 2. Session summary (`..._summary.md`)
A markdown file following `references/summary-template.md` (session details, session history, context and objective, ranked top risks, discussion points, other risks raised, ranking and rating notes, controls mentioned, open questions, the "Session Progress and Resume Point" section, and a consolidation table). Do not attribute anything to individuals.

### Built for consolidation
Both files are designed to be combined with other sessions' files into a higher level register. Keep the register strictly in erm format and put all session identity (context type, scope, horizon, rating mode) in the summary. Risk IDs restart at R1 every session, so consolidation re-IDs them. A worked example in rated mode is `references/example_session_risk_register.csv` with `references/example_session_summary.md`. A rank only or paused register has the same layout with the six rating columns empty.

---

## Self Check Before Replying
- The planned duration was at most 60 minutes, and the context and objective were confirmed before risks were elicited.
- The register has 14 columns per row, correct header, IDs in sequence, and rows in the final order. In rating mode, scores and criticality are correct and rows sorted by score. In rank only mode all six rating columns are empty in every row.
- All risks are rated or none are. Partial ratings appear only in the summary.
- Every description is one sentence with no commas or line breaks, and every title is a specific risk event.
- No list line starts with a hyphen, no literal `\n`, no space after a delimiter comma.
- Every risk came from the participant or is labelled a confirmed facilitator suggestion, and every rating came from the participant or is marked facilitator proposed. Any rating escalated because of a disagreement is noted as such.
- No names or personal data appear in the files, and nothing attributes content to individuals or contradicts what the participant said at read back.
- If the session was paused, extended, handed off to erm or resumed, the checks in `references/pause-and-resume.md` are met.

## Final Reply to the User
Keep it short. State the saved file locations, list the top risks in order, one line each (with score and criticality, or "not rated"), and note any facilitator proposed ratings, escalated disagreements or assumptions recorded. If the session was paused or handed off, tell the user to start a new session with the files to continue. Offer next steps: the erm skill (https://github.com/wai-kwan/enterprise-risk-management) can complete the register by rating unrated risks and adding preventive and reductive controls (its ratings are proposals for the participant to review), the kri skill (https://github.com/wai-kwan/key-risk-indicator) can generate key risk indicators from the register, and more sessions can be consolidated into a higher level register. If a companion skill is not installed, give its link.
