# Time-up, Pausing, Hand-off and Resuming

Read this when the planned time is up before Phase 5 is finished, when the participant asks to pause or stop, when the session is interrupted, when the participant asks for the erm skill to complete the register, or when the user asks to continue an earlier session.

## When the planned time is up
If the planned duration has been used (by your time tracking, or because the user says so) and Phase 5 is not finished, **stop and ask once**: "We have reached our planned time and are not finished yet. Would you like to (1) continue for up to 15 more minutes while I focus on wrapping up the most important parts, or (2) end here and continue another time? I will save our progress either way."
- **Continue for 15 minutes.** This is a one time extension of at most 15 minutes, so do not ask again. Wrap up quickly, in this order of priority, and drop everything else (the coverage sweep, extra probing, controls beyond what is already known):
  1. Make sure 3 to 5 candidate risks are sharpened enough to write down (title, one sentence description, causes, effects). Do no new elicitation unless fewer than 3 candidates exist.
  2. Rank them by perceived criticality.
  3. Rate them only if about one minute per risk plus one remains after ranking, otherwise stay in rank only mode. If rating is cut short, leave the rating columns empty and record the ratings given so far in the summary.
  4. Use the last 3 minutes for the read back and writing the files.

  End the session within the 15 minutes. If the list is still not complete, finish as Paused with a clear next step.
- **End and continue later.** Write the files with Status Paused (see below). Explain that the next session starts from those files and runs as if it were a new session, for up to 60 minutes if the user asks, or 30 minutes by default.

Record the choice in the summary as the "Time-up decision".

## Pausing or ending early
The participant can pause or stop at any time ("pause", "stop", "I have to go"), and a session can also end because time runs out. Never push to continue. When the session stops before Phase 5 is finished:
1. Confirm briefly what you have, asking one last quick question only if the participant is still willing.
2. Write the files straight away with **Status: Paused**.
3. **Register the break in the summary**, in the section "Session Progress and Resume Point": the reason it ended (ended by the participant, out of time, or interrupted), the phase reached, the phases completed, the approximate time used, what has been done, the **specific next step**, and any pending items (candidates not yet sharpened, ratings given so far, open questions).
4. Tell the user how to continue: start a new session and give you both files.

### Register for a paused session
Include every risk sharpened into a full statement so far (possibly more than 5, since the top 3 to 5 are chosen on completion), in ranked order if ranking was done and otherwise in the order sharpened. Leave the rating columns empty unless every risk in the register was rated. If no risk has been sharpened yet, write the summary only and no register. In the summary, put the provisional risks under "Top Risks" with the line "Provisional, session not complete", and mark the other raw risks as (candidate) if not yet sharpened or (parked) if set aside.

## Handing over to the erm skill
Triggered when the participant asks for the erm skill (https://github.com/wai-kwan/enterprise-risk-management) to complete the register before the session is finished, for example "use erm to finish this".
1. **Confirm in one sentence** what will happen: erm fills the fields still open (causes, effects, ratings, controls) as AI proposals, and the participant's own content is kept as given. Do not try to talk them out of it.
2. **Save the participant's own register first** as `<session-id>_risk_register.csv`. Include every candidate risk the participant has agreed, even if not yet sharpened: a title and one sentence description drafted from their words, and only the causes, effects and controls they actually named. Order the rows by their ranking if one was given, otherwise in the order agreed. Leave the rating columns empty unless the participant rated every risk.
3. **Check that erm is available** among the session's skills or in the usual skill folders. If it is not, say so, give its link, and finish as a normal paused session.
4. **Invoke erm** on that register to complete the open fields. erm saves `risk_register.csv`, so run it in a scratch directory or direct its output there, and save the result as `<session-id>_erm_risk_register.csv`. Never overwrite the participant's register, and delete any scratch files afterwards.
5. **Write the summary** with Status Paused and Reason for ending "Handed over to erm". In the Top Risks table, mark every value erm proposed (for example with an asterisk and a note), say whether the order is the participant's ranking or erm's scores, and set Rated to "erm proposed" in the Consolidation Data. Name both registers in the summary.
6. **Next step** in the resume point: resume at Phase 3 using the erm register as a draft, so the participant confirms or edits each risk, then ranks and rates in Phase 4. Participant ratings replace erm's.

## Resuming
Triggered when the user asks to continue or resume, or supplies a previous register and summary. If the session was handed over to erm, treat the erm register as a draft: read every erm proposed field back for the participant to confirm or change, and do not accept it silently.
1. **Locate both files** (given paths, uploads, or the workspace by session ID). Read the register with a CSV parser and the summary's "Session Progress and Resume Point". Treat the files as the source of truth, including any edits the user made since. If only one file is available, proceed from it and say what is missing. Without the register, ask again for the causes, effects and controls of the risks the summary lists.
2. **Recap** in a few sentences: the context and objective, what has been covered, the risks so far, and the next step. Ask only for corrections. If the context or objective has changed materially, ask whether to continue this session or start a new one.
3. **Set the duration of this part** as if it were a new session (default 30, maximum 60 minutes per part) and spread it over the **remaining phases only**. Do not repeat completed phases.
4. **Continue from the recorded phase and next step.** Carry forward the earlier context, risks and discussion points and add the new ones. Risk IDs may change when the list is re-ordered.
5. If the earlier session was **Complete**, ask what the user wants (for example rate risks that were only ranked, add or replace risks, or sharpen one further) and do only that. A rank only session can be resumed straight into rating.
6. Finish as normal. The new register is **cumulative** (earlier risks carried forward), so the latest part's files replace earlier parts when consolidating. Add a row to the Session History table in the summary.

### File naming for continued sessions
A continued session keeps the Session ID of part 1 and names its files `<session-id>_part2_risk_register.csv` and `<session-id>_part2_summary.md` (part 3, 4 and so on likewise). Never overwrite files from an earlier part.

## Checks for paused, extended and resumed sessions
- If the planned time ran out before completion, the user was asked once whether to extend by 15 minutes or end, and the choice is recorded as the Time-up decision.
- Paused session: the summary records the status, reason, phase reached, phases completed, time used and a specific next step, and a register exists only if at least one risk was sharpened.
- Handed over to erm: the participant's own register was saved first and left untouched, the erm result is a separate `_erm_` file, every erm proposed value is marked in the summary, and no scratch files remain.
- Resumed session: earlier files were left untouched, the new files carry the part suffix, the register is cumulative, completed phases were not repeated, and the Session History has a new row.
