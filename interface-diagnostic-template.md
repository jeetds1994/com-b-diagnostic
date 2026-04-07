# Interface Diagnostic Template

## What this template is

A structured method for analyzing **handoff failures between actors** in a multi-actor behavior system. While per-actor COM-B profiles diagnose what is happening within each persona, interface diagnostics reveal where the system breaks down *between* them.

In most distributed behavior systems, failure concentrates at interfaces — where one actor's output becomes another actor's input. An accurate forecast that is communicated abstractly fails the guide who needs terrain-level decisions. A complete observation that arrives after the forecast cycle closes is invisible to the forecaster. These are interface failures, not actor failures.

This template should be used during Step 4 of the `analysis-template.md` workflow.

---

## How to use this template

1. **Identify all interfaces** in the system (Step 1 below)
2. **Complete a diagnostic card** for each interface (Step 2)
3. **Classify the failure type** (Step 3)
4. **Map the COM-B roots** on both sides (Step 4)
5. **Design interface-level interventions** (Step 5)

---

## Step 1: Map the Interfaces

List every handoff where Actor A produces something that Actor B depends on. Include data, decisions, signals, and permissions — not just formal deliverables.

| # | From (Actor A) | To (Actor B) | What is handed off | Criticality (H/M/L) |
|---|---------------|-------------|-------------------|---------------------|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |

**Criticality guide:**
- **High:** If this handoff fails, the system outcome fails
- **Medium:** Failure degrades the system but does not break it
- **Low:** Failure creates friction but workarounds exist

---

## Step 2: Interface Diagnostic Card

Complete one card per interface. Focus on High and Medium criticality interfaces first.

### Interface: [Actor A] -> [Actor B]

**What Actor A produces:**
- Format: (e.g., structured form, free text, verbal, photo)
- Timing: (e.g., real-time, daily, when prompted, post-event)
- Quality level: (e.g., expert-calibrated, variable, minimal)
- Completeness: (e.g., all fields, partial, inconsistent)

**What Actor B needs:**
- Format: (e.g., structured data, summary, map overlay, alert)
- Timing: (e.g., before decision window, within N hours, continuous)
- Quality level: (e.g., verified, representative, minimum viable)
- Completeness: (e.g., specific fields required, spatial coverage needed)

**The gap:**

| Dimension | What A produces | What B needs | Mismatch? |
|-----------|----------------|-------------|-----------|
| Format | | | Y/N |
| Timing | | | Y/N |
| Quality | | | Y/N |
| Completeness | | | Y/N |
| Meaning / semantics | | | Y/N |

**Feedback loop:**
- Does Actor A know whether their output was received? (Y/N)
- Does Actor A know whether their output was useful? (Y/N)
- Does Actor A receive guidance on how to improve their output? (Y/N)

---

## Step 3: Classify the Failure Type

Each interface mismatch falls into one or more failure types:

| Failure Type | Description | Signal |
|-------------|-------------|--------|
| **Translation failure** | Output is accurate but not in a form the receiver can act on | "The data is there but I can't use it" |
| **Timing failure** | Output arrives outside the receiver's decision window | "By the time I got it, I had already decided" |
| **Quality failure** | Output does not meet the receiver's minimum threshold | "I can't trust this / it's too incomplete" |
| **Volume failure** | Too much output — signal lost in noise | "There's so much data I can't find what matters" |
| **Absence failure** | Output is expected but never arrives | "I was waiting for input that never came" |
| **Semantic failure** | Same words carry different meanings across actors | "We used the same term but meant different things" |
| **Feedback failure** | No signal flows back from receiver to sender | "I have no idea if what I sent was useful" |

---

## Step 4: Map COM-B Roots (Both Sides)

For each interface failure, diagnose the COM-B roots on **both sides** of the handoff. The cause may be on the sender's side, the receiver's side, or both.

### Actor A (sender) COM-B analysis:

| COM-B Code | Barrier | Present? |
|-----------|---------|----------|
| PC | Does A lack knowledge of what B needs? | |
| PHC | Does A lack the skill to produce what B needs? | |
| PO | Do A's tools/time/workflow prevent producing the right output? | |
| SO | Do A's norms/incentives discourage producing what B needs? | |
| RM | Does A not see value in tailoring output for B? | |
| AM | Does A's habit produce output in the wrong form by default? | |

### Actor B (receiver) COM-B analysis:

| COM-B Code | Barrier | Present? |
|-----------|---------|----------|
| PC | Does B lack knowledge to interpret A's output? | |
| PHC | Does B lack the skill to process A's output? | |
| PO | Do B's tools/time/workflow prevent consuming A's output? | |
| SO | Do B's norms/incentives discourage using A's output? | |
| RM | Does B not trust or value A's output? | |
| AM | Does B's habit bypass A's output? | |

### System-level factors:

| Factor | Present? |
|--------|----------|
| No shared standard for the handoff format | |
| No shared vocabulary / semantic alignment | |
| No feedback mechanism from B to A | |
| No single actor owns the interface | |
| Organizational boundary between A and B | |

---

## Step 5: Design Interface Interventions

Interface interventions differ from actor-level interventions. They target the *gap between actors*, not a single actor's COM-B profile.

**Intervention categories for interfaces:**

| Category | What it does | BCW Functions | Example |
|----------|-------------|--------------|---------|
| **Translation layer** | Convert A's output into B's needed format | ER, EN | Observation summary cards that translate raw data into role-specific insights |
| **Timing alignment** | Ensure output arrives within decision window | ER | Auto-routing observations to forecasters within their intake cycle |
| **Quality gateway** | Guide minimum viable quality without blocking | TR, EN | Progressive forms with completeness nudges |
| **Feedback loop** | Signal from B back to A about output usefulness | INC, PE | "Your observation was cited in today's forecast" |
| **Shared standard** | Align format/vocabulary across A and B | ED, MO | Canonical observation fields with shared definitions |
| **Interface owner** | Assign accountability for the handoff | ER, SO | Tool feature that monitors handoff health metrics |

---

## Worked Example: Field Observer -> Forecaster

### Interface Diagnostic Card

**What the Field Observer produces:**
- Format: Structured observation form (snowpack test results, weather data, photos) + free-text notes
- Timing: Typically after returning from the field (1-6 hour delay); sometimes next morning
- Quality level: Highly variable — expert observers submit rich, calibrated data; newer observers submit bare minimums
- Completeness: Critical fields (aspect, elevation, spatial representativeness) often missing or estimated

**What the Forecaster needs:**
- Format: Structured, queryable data with spatial metadata — observation must be locatable on a map and filterable by date, zone, elevation band
- Timing: Before the morning forecast cycle (typically 5-6 AM); afternoon observations needed by 3 PM for evening updates
- Quality level: Representative — the observation must be interpretable as indicative of broader conditions, not just a single point
- Completeness: Elevation, aspect, date/time, location, snow surface conditions, and any instability indicators are non-negotiable for forecast utility

**The gap:**

| Dimension | Observer produces | Forecaster needs | Mismatch? |
|-----------|------------------|-----------------|-----------|
| Format | Structured form + free text | Queryable structured data | Partial — free text is hard to query |
| Timing | 1-6 hour delay, sometimes next-day | Before 6 AM / 3 PM cycle | Y — observations often miss the window |
| Quality | Highly variable | Representative, calibrated | Y — no quality floor or calibration |
| Completeness | Critical fields often missing | Elevation, aspect, location, instability required | Y — gaps in spatial metadata |
| Meaning | Observer describes what they saw | Forecaster needs to infer what it means for the zone | Y — translation burden on forecaster |

**Feedback loop:**
- Does the observer know their data was received? Sometimes (system confirmation)
- Does the observer know their data was useful? Almost never
- Does the observer receive guidance on improvement? No

### Failure Classification

| Failure Type | Present? | Evidence |
|-------------|----------|----------|
| Translation | Yes | Free-text notes require forecaster interpretation; raw data doesn't map to forecast zones |
| Timing | Yes | Post-field submission misses morning forecast cycle |
| Quality | Yes | No calibration between observers; no minimum quality floor |
| Volume | Partial | High-activity days overwhelm manual triage |
| Absence | Partial | Some zones chronically under-observed |
| Semantic | Minor | Most terminology is standardized via avalanche education |
| Feedback | Yes | Observers submit into a void |

### COM-B Roots

**Observer (sender) side:**
- **PO** (dominant): Field conditions make real-time reporting difficult; tools require connectivity; post-field entry is the only practical option
- **PC**: Newer observers don't know which fields matter most to forecasters
- **AM**: Habit is to fill the minimum and move on — no cue to add context or check completeness

**Forecaster (receiver) side:**
- **PO**: No automated triage — forecaster manually scans all incoming observations
- **PC**: Must mentally translate point observations to zone-level inferences (high cognitive load at volume)
- **AM**: Habit is to rely on trusted observers and ignore unfamiliar ones

**System-level:**
- No shared standard for what "forecaster-useful" observation looks like
- No feedback loop from forecaster to observer
- No single actor owns the Observer -> Forecaster interface

### Interface Interventions

| Intervention | Targets | BCW |
|-------------|---------|-----|
| Offline-first mobile submission with GPS auto-capture | Timing + Completeness gap (Observer PO) | ER |
| "Forecast-ready" completeness indicator on submission form | Quality gap (Observer PC, AM) | TR, EN |
| Auto-routing observations to forecast zone inbox with priority scoring | Volume + Timing gap (Forecaster PO) | ER |
| "Your observation was used in today's forecast" notification | Feedback gap (Observer AM, RM) | INC, PE |
| Observation-to-zone translation layer (map overlay showing spatial coverage + gaps) | Translation gap (Forecaster PC) | ER, EN |
| Shared "minimum viable observation" standard, embedded in the form | Semantic + Quality alignment (System-level PC) | ED, MO |
