# Session Summary Template

Use this structure for `<date>_<context-slug>_summary.md`. Fill every section from what the participant said. Write plain, specific prose, never attribute anything to individuals (everyone present is treated as one voice), and leave a section's heading in place with "None" if there is nothing to report. Do not add risks, ratings or facts the participant did not give.

```markdown
# Risk Session Summary: <short session title>

## Session Details
| Item | Detail |
|---|---|
| Session ID | <date>_<context-slug> |
| Date | <YYYY-MM-DD> |
| Participants | <as the user described them, for example "operations leadership team", treated as one voice> |
| Session part | <1 for a new session, 2 or more for a continued one> |
| Status | Complete or Paused |
| Planned duration | <minutes of this part, maximum 60> |
| Assessment mode | Rated (likelihood and impact), Rank only (perceived criticality) or erm proposed (handed over to erm, pending participant review) |
| Context type | Company operations, Project, Scenario, Department or Strategic planning |
| Scope | <what is in and out of scope> |
| Time horizon | <for example next 12 months> |

## Session History
| Part | Date | Planned duration | Phases covered | How it ended |
|---|---|---|---|---|
| 1 | <YYYY-MM-DD> | <minutes> | 0 to 2 | Paused (ended by participant) |

One row per part. Show an extension in the duration column (for example "30 minutes plus 15 minute extension"). A continued session adds a row and keeps the Session ID of part 1.

## Context and Objective
<A concrete paragraph of three to five sentences: what the organisation, project or scenario is and is trying to achieve, what it depends on, what has recently changed, what this session is for (its objective), and what loss would be unacceptable.>

## Top Risks
In a paused session this heading holds the risks sharpened so far and is provisional. Add the line "Provisional, session not complete" under it.

Rated mode:
| Rank | ID | Risk title | Category | L | I | Score | Criticality |
|---|---|---|---|---|---|---|---|
| 1 | R1 | ... | ... | 3 | 5 | 15 | HIGH |

Rank only mode (ratings not assessed):
| Rank | ID | Risk title | Category |
|---|---|---|---|
| 1 | R1 | ... | ... |

One short paragraph per risk, in the same order, saying in plain words what could happen, why the participant worries about it, and the main causes and consequences.

## Key Discussion Points
<Five to eight bullets: themes that came up repeatedly, assumptions made, anything that surprised the participant, and conflicting views with how they were settled.>

## Other Risks Raised (not in the top list)
<Numbered list of the remaining raw risks, one line each. In a paused session mark each as (candidate) if not yet sharpened or (parked) if set aside.>

## Ranking and Rating Notes
<How the final order was set. In rated mode: any score that reordered the perceived ranking, and every rating marked "facilitator proposed". In rank only mode: say that likelihood and impact were not assessed and why (time). List every risk labelled "facilitator suggestion, confirmed" and any disagreement recorded with the higher view.>

## Controls Mentioned
<For each top risk: existing controls, planned or proposed controls, and whether each is preventive or reductive. Say "none mentioned" where applicable.>

## Open Questions and Follow Ups
<Information to find, owners to confirm, decisions needed, risks to revisit, and, in rank only mode, a note that the risks still need rating.>

## Session Progress and Resume Point
Complete this section in every summary. For a complete session it can say "Session complete, nothing pending" (or, for a rank only session, that the risks still need rating).

| Item | Detail |
|---|---|
| Status | Complete or Paused |
| Reason for ending | Completed as planned, Ended by participant, Out of time, Interrupted or Handed over to erm |
| Time-up decision | Extended by 15 minutes, Ended to continue later, or Not applicable (finished or stopped before the planned time was up) |
| Phase reached | <number and name, for example 3 Sharpen> |
| Phases completed | <for example 0, 1, 2> |
| Time used | <approximate minutes of the planned duration> |
| Assessment mode so far | Not yet decided, Rated or Rank only |
| Next step | <specific, for example "Continue Phase 3 with the data migration risk, still to ask about consequences and existing controls"> |
| Pending items | <candidates not yet sharpened, ratings given so far, open questions> |

## Consolidation Data
Set Rated to Yes, No or erm proposed.

| Session ID | Risk ID | Risk title | Category | Rank | Likelihood | Impact | Score | Rated | Status | Context type |
|---|---|---|---|---|---|---|---|---|---|---|
```
