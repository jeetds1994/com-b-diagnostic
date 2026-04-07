# Prioritization Framework

## What this framework is

When a COM-B analysis surfaces multiple behaviors, multiple actors, and multiple blockers, everything looks important. This framework provides a structured method for deciding **what to work on first** by scoring interventions across five dimensions.

Use this after completing the analysis template (Steps 1-8) and before committing to an implementation plan.

---

## The Five Scoring Dimensions

### 1. Impact

How many actors and behaviors does this intervention affect?

| Score | Meaning |
|-------|---------|
| 3 | Affects 3+ actors or 3+ behaviors |
| 2 | Affects 2 actors or 2 behaviors |
| 1 | Affects 1 actor and 1 behavior |

**Tip:** Interventions that target a shared interface (e.g., Observer -> Forecaster handoff) often score higher than interventions that optimize a single actor's workflow.

### 2. Frequency

How often does the targeted behavior occur?

| Score | Meaning |
|-------|---------|
| 3 | Multiple times per day (e.g., submitting observations during field season) |
| 2 | Daily or several times per week (e.g., consuming observations for forecasting) |
| 1 | Weekly or less (e.g., calibrating observer quality across the network) |

**Tip:** High-frequency behaviors compound — even small friction reductions at high frequency produce large aggregate gains.

### 3. Blocker Concentration

Does this intervention address the COM-B code that appears most frequently across your analysis?

| Score | Meaning |
|-------|---------|
| 3 | Targets the #1 most frequent COM-B blocker across the system |
| 2 | Targets the #2 or #3 most frequent blocker |
| 1 | Targets a blocker that appears in only 1 behavior |

**How to calculate:** In Step 6 of the analysis template, you counted how many behaviors each COM-B code blocks. The code with the highest count is the dominant blocker. Interventions that address this code get a 3.

### 4. Interface Leverage

Does this intervention fix a handoff failure that cascades downstream?

| Score | Meaning |
|-------|---------|
| 3 | Fixes a handoff whose failure breaks the system outcome (e.g., observations never reaching forecasters) |
| 2 | Fixes a handoff whose failure degrades quality but doesn't break the system |
| 1 | Does not target a handoff (actor-internal improvement) |
| 0 | Not applicable (no interface component) |

**Tip:** A single interface fix often resolves problems that would otherwise require separate interventions on both sides of the handoff.

### 5. Feasibility

Is this intervention within the tool's sphere of influence, or does it require organizational, cultural, or policy change?

| Score | Meaning |
|-------|---------|
| 3 | Fully within tool design scope (UI change, workflow automation, data feature) |
| 2 | Requires some coordination beyond the tool (training program, process agreement, API integration) |
| 1 | Requires organizational or cultural change that the tool cannot drive alone |

**Tip:** Score feasibility honestly. An intervention with high impact but low feasibility may need to be broken into phases — start with the tool-addressable component, then build toward the organizational component.

---

## Scoring Table

For each candidate intervention, score all five dimensions and compute the total.

| # | Intervention | Impact (1-3) | Freq (1-3) | Blocker (1-3) | Interface (0-3) | Feasibility (1-3) | Total (/15) |
|---|-------------|-------------|-----------|--------------|----------------|-------------------|-------------|
| 1 | | | | | | | |
| 2 | | | | | | | |
| 3 | | | | | | | |

**Interpretation:**
- **12-15:** High priority — do this first
- **9-11:** Medium priority — do after high-priority items
- **5-8:** Lower priority — consider deferring or bundling with related work
- **Below 5:** Likely not worth pursuing now

---

## Tiebreaking Rules

When two interventions score the same total:

1. **Prefer the one with higher Interface Leverage.** Interface fixes have compounding effects.
2. **Prefer the one with higher Feasibility.** Shipping an imperfect intervention beats planning a perfect one.
3. **Prefer the one that closes a feedback loop.** Feedback loops are self-reinforcing — once established, they improve the system without additional intervention.

---

## Worked Example: Avalanche Observation Reporting App

### Context

From the COM-B analysis of the observation reporting system, we identified five candidate interventions:

1. **Reduce submission friction** (offline-first mobile, GPS auto-capture, one-tap quick obs)
2. **Standardize interpretation** (observation summaries, danger aggregation, persona-specific cards)
3. **Enable cross-boundary sharing** (submit-once share-everywhere, organizational federation)
4. **Guide quality through design** (progressive forms, inline nudges, completeness scores)
5. **Close the feedback loop** (observer sees when their data was viewed, cited, or flagged)

### Blocker Concentration (from analysis)

| COM-B Code | Behaviors blocked |
|-----------|------------------|
| PO | 4 (submission, sharing, quality, interpretation) |
| PC | 3 (interpretation, quality, sharing) |
| AM | 3 (submission, sharing, quality) |
| SO | 2 (interpretation, quality) |
| RM | 2 (sharing, last-mile motivation) |

**Dominant blocker: PO (Physical Opportunity)**

### Scoring

| # | Intervention | Impact | Freq | Blocker | Interface | Feasibility | Total |
|---|-------------|--------|------|---------|-----------|-------------|-------|
| 1 | Reduce submission friction | 3 (Observer, Patrol, Guide, Recreationist) | 3 (multiple obs/day in season) | 3 (PO is dominant) | 3 (fixes Observer->Database handoff) | 3 (pure tool design) | **15** |
| 5 | Close feedback loop | 3 (all contributors) | 2 (daily feedback) | 2 (AM is #3 blocker) | 3 (fixes Observer<->Forecaster feedback gap) | 3 (tool feature) | **13** |
| 2 | Standardize interpretation | 3 (Forecaster, Patrol, Guide, Recreationist) | 2 (daily consumption) | 2 (PC is #2 blocker) | 2 (eases Database->Consumer handoff) | 2 (needs vocabulary agreement) | **11** |
| 4 | Guide quality through design | 2 (Observer, Patrol) | 3 (every submission) | 2 (PC+AM) | 2 (improves what Forecaster receives) | 3 (form design) | **12** |
| 3 | Enable cross-boundary sharing | 2 (all contributors, all consumers) | 2 (daily) | 3 (PO is dominant) | 2 (new interface creation) | 2 (needs org agreements) | **11** |

### Prioritized Order

| Priority | Intervention | Score | Rationale |
|----------|-------------|-------|-----------|
| 1 | Reduce submission friction | 15 | Maximum score — high frequency, dominant blocker, critical interface, fully feasible |
| 2 | Close feedback loop | 13 | Tiebreaker: feedback loops are self-reinforcing; highest interface leverage after #1 |
| 3 | Guide quality through design | 12 | High frequency (every submission) and fully feasible; improves Forecaster intake |
| 4 | Standardize interpretation | 11 | Tied with #5 but wins on impact breadth (4 actors) |
| 5 | Enable cross-boundary sharing | 11 | Lower feasibility (requires organizational agreements) drops it below #4 |

### Key Insight

The feedback loop (#2) scored second despite not targeting the dominant blocker (PO). This is because it has high interface leverage and satisfies the tiebreaking rule: feedback loops are self-reinforcing. Once observers see impact, submission quality and frequency improve without additional intervention — making it a force multiplier for intervention #1.

---

## When to Re-Prioritize

Re-score your intervention list when:
- A state transition occurs (behavior moves to a new state in the diagnostic cycle)
- The dominant COM-B blocker shifts (e.g., after fixing PO, PC may become dominant)
- New actors or interfaces are added to the system
- Feasibility changes (e.g., organizational agreement is reached, enabling a previously low-feasibility intervention)

Prioritization is not a one-time exercise. As interventions take effect, the blocker landscape changes and priorities should shift accordingly.
