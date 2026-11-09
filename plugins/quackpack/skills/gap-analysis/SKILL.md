---
name: gap-analysis
description: Surface unresolved product decisions in a requirement before writing a user story. Sorts input into confirmed/assumed/unknown, keeps a decision record, prioritises gaps into stakeholder questions, and only drafts acceptance criteria from confirmed decisions. Use when asked to write, refine, or review a user story, epic, or requirement, or to prep for refinement / Three Amigos / Example Mapping.
---

# Gap Analysis

Don't produce a polished user story first. A fluent story hides "confident gaps": holes the model filled with rules nobody decided. Use AI to find the open decisions and turn them into questions. Write the story last.

Based on Thoughtworks, ["Don't ask AI to write the user story yet"](https://www.thoughtworks.com/insights/blog/generative-ai/dont-ask-ai-to-write-the-user-story-yet).

## Hard rules
- **Do not invent business rules.** Work only from the evidence the user supplied (the request, notes, tickets, transcripts, code). If it isn't in the evidence, it's Assumed or Unknown.
- Specific doesn't mean validated. Flag any precise-sounding detail (thresholds, dedup rules, date fields, permissions) that has no source.
- Keep enhancements and nice-to-haves in their own list. They must not quietly expand the scope.
- The human owns the questions and the draft. Present your output as input to refinement, not as the result.

## Phase 1: Gap analysis (default)
1. **Gather inputs.** Get the user task, the desired outcome, confirmed rules, and source notes. If the outcome or user is missing, ask before you continue.
2. **Sort every statement into three piles:**
   - **Confirmed:** each item cites its source.
   - **Assumed:** implied or presumed, but not validated.
   - **Unknown:** a decision the requirement needs that the evidence doesn't cover.
3. **Build the decision record**, one row per rule or question:

   | # | Rule / question | Status (confirmed/assumed/unknown) | Decision owner | Source | Still open |
   |---|---|---|---|---|---|

4. **Triage.** For each Assumed or Unknown item, ask three questions. Could it change the scope? Could it change who can do what? Could it change what the data or outcome means? Any yes makes it **high priority**. Explain the consequence of leaving it undecided, and propose one concrete stakeholder question. Put a concrete example in the question so the edge case is visible (e.g. "the export matches 50k rows but only 20 show on screen: do we export all 50k?").
5. **Output:**
   - The decision record.
   - Prioritised questions (high first), each with an owner. Keep the list short; it's fine to drop low-value ones.
   - A separate list of optional enhancements.
   - Optional: suggest taking the high-priority questions into Three Amigos / Example Mapping.

Stop here. Don't write the story until the user says the key decisions are confirmed.

## Phase 2: Draft the story (only after decisions are confirmed)
- Update the decision record with the answers.
- Draft the story and acceptance criteria **only from Confirmed decisions**. Link each criterion to its decision # in the record.
- List any criteria still blocked by open decisions as unresolved dependencies. Don't fill them in.

## Notes
- The decision record usually outlives the story. When requirements change, use it to revisit the decision instead of guessing. Offer to save it next to the ticket or spec.
- When trying this for the first time, pilot it on one requirement. Note which questions helped, which were noise, and how long review took.
