# COM-B Multi-Actor Analysis Template

## What this template is

A step-by-step scaffold for running a behavioral diagnosis of a multi-actor system using the COM-B model. This template turns the reference materials (abbreviations, blocker matrix, diagnostic cycle, intervention mapping, tool levers) into a structured analysis process.

Use this template when you need to understand why behaviors are breaking down across a system of actors and where interventions will have the highest leverage.

## Prerequisites

Before starting, have these reference files available:
- `com-b-abbreviations-reference.md` — COM-B code definitions
- `behavior-jtbd-maturity-diagnostic-cycle.md` — 7-state behavior cycle
- `com-b-behavior-states-primary-secondary-blockers.md` — Quick blocker lookup
- `com-b-to-bcw-intervention-function-mapping.md` — Intervention selection
- `com-b-tool-influence-mechanisms-and-levers.md` — Tool design patterns
- `interface-diagnostic-template.md` — Handoff analysis method
- `prioritization-framework.md` — Ranking what to work on

---

## Step 1: Define the System

**Name the system:** What is the behavior system you are analyzing?

**Draw the boundary:** What is inside scope and what is outside? Include all actors whose behavior directly affects the outcome you care about. Exclude actors whose influence is indirect or environmental.

| Field | Your Entry |
|-------|-----------|
| System name | |
| Target outcome | What does success look like when the system works? |
| System boundary | Who/what is inside vs. outside? |
| Key constraint | What makes this system hard? (e.g., distributed actors, time pressure, environmental uncertainty) |

**Example (Avalanche Observation Reporting):**

| Field | Entry |
|-------|-------|
| System name | Avalanche observation reporting network |
| Target outcome | Timely, representative, high-quality snowpack observations flow from field to forecast to decision-maker |
| System boundary | Inside: Field observers, ski patrol, guides, recreationists (as contributors), forecasters, highway control (as consumers). Outside: Equipment manufacturers, policy makers, media |
| Key constraint | Distributed actors with uneven capability, observations collected under adverse field conditions, no single actor owns the full pipeline |

---

## Step 2: List the Actors

For each actor in the system, capture their role and relationship to the target outcome.

| Actor | Role in System | Contributes (input) | Depends on (input from others) |
|-------|---------------|---------------------|-------------------------------|
| | | | |
| | | | |

Tips:
- Include actors who contribute data, consume data, or both
- Note actors who are dual-role (both contributor and consumer)
- Flag actors who are outside the system boundary but whose behavior influences actors inside it

---

## Step 3: Profile Each Actor (COM-B)

For each actor, complete this profile. Use the COM-B abbreviations (PC, PHC, PO, SO, RM, AM) from the abbreviations reference.

### Actor: [Name]

**Target Behaviors**
- What specific behaviors does this actor need to perform for the system to work?
- List 2-4 concrete, observable behaviors (not goals or aspirations)

**Needs / Desires**
- What does this actor want from their participation in the system?
- What are they optimizing for? (This often differs from what the system needs)

**Capability**
- Psychological (PC): Knowledge, mental models, cognitive skills — present or lacking?
- Physical (PHC): Physical skills or procedural abilities — present or lacking?

**Opportunity**
- Physical (PO): Tools, time, resources, workflows — enabling or constraining?
- Social (SO): Norms, incentives, cultural expectations — supporting or opposing?

**Motivation**
- Reflective (RM): Deliberate intentions, beliefs, values?
- Automatic (AM): Habits, impulses, biases, emotional responses?

**Failure Modes**
- How does this actor's behavior break down?
- What triggers failure? (conditions, context, pressure)
- What does failure look like from the perspective of actors who depend on them?

---

## Step 4: Analyze Interfaces

This is where the highest-leverage problems typically live. Use `interface-diagnostic-template.md` for the detailed method.

For every pair of actors where one actor's output becomes another's input, complete an interface analysis.

**Identify interfaces:**

| From (Actor A) | To (Actor B) | What is handed off? |
|---------------|-------------|-------------------|
| | | |

**For each interface, answer:**
1. What does Actor A produce?
2. What does Actor B need?
3. Where is the mismatch in format, timing, quality, or meaning?
4. What COM-B codes explain the gap on each side?

**Common interface failure patterns:**
- Abstract output meets concrete need (e.g., probabilistic forecast vs. go/no-go decision)
- Timing mismatch (data arrives after the decision window closes)
- Quality mismatch (contributor submits minimum; consumer needs detail)
- Semantic mismatch (same terms, different meanings across actors)
- Missing feedback (contributor never learns whether their output was useful)

---

## Step 5: Classify Behavior States

For each target behavior from Step 3, classify its current state using the 7-state diagnostic cycle.

| Behavior | Actor(s) | Current State | State Signal |
|----------|---------|---------------|-------------|
| | | | |

**The 7 states (quick reference):**
1. Fully Realized & Stable — Ritualized, reliable, trusted
2. Realized but Friction-Filled — Mandatory but painful
3. Partially Realized / Inconsistent — Exists in pockets; lacks alignment
4. Weakly Realized — Agreed and valued, but displaced
5. Aspirational Only — Desired but not practiced
6. Actively Suppressed — Forces prevent the behavior
7. Contested / Undefined — No shared definition

For each behavior, look up primary and secondary blockers in `com-b-behavior-states-primary-secondary-blockers.md`:

| Behavior | Primary Blockers (COM-B) | Secondary Blockers (COM-B) |
|----------|------------------------|--------------------------|
| | | |

---

## Step 6: Identify Highest-Leverage Blockers

Look across all behaviors and actors for patterns.

**Blocker concentration:** Which COM-B codes appear most frequently?

| COM-B Code | Count (behaviors blocked) | Actors affected |
|-----------|--------------------------|----------------|
| PC | | |
| PHC | | |
| PO | | |
| SO | | |
| RM | | |
| AM | | |

**Interface leverage:** Which single interface failure cascades to the most downstream problems?

**What the dominant blocker type tells you:**
- PO dominates: the environment is the problem — fix tools, workflows, friction
- PC dominates: understanding is the problem — fix training, shared language, mental models
- SO dominates: norms are the problem — fix incentives, visibility, social proof
- RM dominates: commitment is the problem — fix identity, risk perception, value framing
- AM dominates: habits are the problem — fix defaults, cues, feedback loops

---

## Step 7: Select Interventions

For each high-leverage blocker, use `com-b-to-bcw-intervention-function-mapping.md` to identify which BCW intervention functions apply.

| Blocker (COM-B) | BCW Functions | Specific Intervention Ideas |
|-----------------|--------------|---------------------------|
| | | |

Then use `com-b-tool-influence-mechanisms-and-levers.md` to translate interventions into concrete tool features or design patterns.

Check intervention quality using `intervention-quality-criteria.md`.

---

## Step 8: Prioritize

Use `prioritization-framework.md` to rank interventions. Score each by:

1. **Impact:** How many actors and behaviors does this intervention affect?
2. **Frequency:** How often does the targeted behavior occur?
3. **Blocker concentration:** Does this address the dominant COM-B code?
4. **Interface leverage:** Does it fix a handoff that cascades?
5. **Feasibility:** Within the tool's sphere, or requires organizational change?

| Intervention | Impact | Freq | Blocker | Interface | Feasibility | Priority |
|-------------|--------|------|---------|-----------|-------------|----------|
| | | | | | | |

---

## Step 9: Check System-Level Dynamics

Before finalizing, check for four common patterns:

**1. Last Mile Problem**
Is upstream performance strong but downstream decisions still failing? If yes, the intervention must reach the decision point, not just improve data quality.

**2. Motivation Override**
Is automatic motivation (habits, biases, social pressure) overriding capability and opportunity? If yes, capability-building alone will not work.

**3. Permissive Opportunity**
Is the environment implicitly permitting the wrong behavior? (e.g., easy access, existing tracks, open terrain) If yes, environmental restructuring must make the safe choice the easy choice.

**4. Misaligned Optimization**
Are actors optimizing for different objectives with no one owning end-to-end alignment? If yes, create shared visibility or shared incentives.

---

## Output Checklist

A complete analysis includes:

- [ ] System definition with clear boundary
- [ ] Actor list with roles and dependencies
- [ ] COM-B profile for each actor
- [ ] Interface analysis for each handoff
- [ ] Behavior state classification for each target behavior
- [ ] Blocker concentration analysis
- [ ] Intervention selection with BCW mapping
- [ ] Prioritized intervention list
- [ ] System-level dynamics check
