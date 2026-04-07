# Case Study: Avalanche Observation Reporting App

## System Definition

| Field | Entry |
|-------|-------|
| System name | Avalanche observation reporting network |
| Target outcome | Timely, representative, high-quality snowpack observations flow from field to forecast to decision-maker |
| System boundary | Inside: Field observers, ski patrol, guides, recreationists (contributors); forecasters, highway control (consumers). Outside: Equipment manufacturers, policy makers, media |
| Key constraint | Distributed actors with uneven capability; observations collected under adverse field conditions; no single actor owns the pipeline end-to-end |

---

## Relevant Personas and App Roles

### Primary Users (Input Side)

| Persona | Role in App | Core Behavior |
|---------|------------|---------------|
| Snow Scientist / Field Observer | Primary contributor | Submit structured, timely, representative observations |
| Ski Patrol / Snow Safety | Contributor + Consumer | Submit operational observations; consume others' data for open/close decisions |
| Mountain Guide / Trip Leader | Contributor + Consumer | Submit route-level observations; consume data for terrain selection |
| Backcountry Recreationist | Citizen contributor + Consumer | Submit informal observations; consume simplified data for trip planning |

### Primary Users (Output Side)

| Persona | Role in App | Core Behavior |
|---------|------------|---------------|
| Avalanche Forecaster | Primary consumer | Synthesize observations into forecasts; assess data quality and representativeness |
| Highway Avalanche Control | Consumer | Filter observations relevant to specific corridors for closure/mitigation timing |

### Secondary Users

| Persona | Role in App | Core Behavior |
|---------|------------|---------------|
| Avalanche Educator | Indirect consumer | Use observation records for teaching scenarios and case studies |
| Search and Rescue (SAR) | Edge consumer | Access observation history post-incident for forensic analysis |

---

## Observation-Specific Role Profiles

The base personas in `personas_jobs.md` describe actors across the full avalanche safety system. For an observation reporting app, several personas contain **behavioral variants** — distinct usage patterns that require different design responses.

### Field Observer Variants

#### Professional Observer (Avalanche Center Staff)

**Observation behavior:** Scheduled, systematic observations following standardized methodology. Submits 1-3 detailed observations per field day during storm cycles.

**What they observe:** Full snowpack profiles, stability tests (ECT, CT, PST), weather data, natural avalanche activity, surface conditions.

**When/how they submit:** Ideally in-field between observation sites. Realistically, back at the truck or office due to connectivity and conditions. Uses structured forms with all fields completed.

**What they consume:** Other observers' submissions to assess spatial representativeness and identify gaps in coverage.

**COM-B specifics:**
- PC: Strong — deep snow science training, calibrated judgment
- PO: Primary blocker — connectivity, cold/glove interface, time pressure between sites
- AM: Habit is thorough but slow; post-field batch submission is the default
- RM: High — professional identity tied to data quality

**Design implications:** Needs offline-first with full form depth. Speed matters between sites. Auto-sync is essential. Quality nudges are unnecessary (they already know what good looks like).

#### Volunteer / Citizen Observer

**Observation behavior:** Opportunistic observations submitted when something notable is encountered. Frequency varies from weekly to a few times per season.

**What they observe:** Surface conditions, recent avalanche activity, weather at their location, notable red flags (whumpfing, shooting cracks). Rarely performs formal stability tests.

**When/how they submit:** Post-trip, often from home. Sometimes in-field if conditions are dramatic enough to photograph.

**What they consume:** Others' observations to validate their own experience and plan future trips.

**COM-B specifics:**
- PC: Moderate — avalanche education (Level 1-2) but limited calibration
- PO: Moderate — connectivity less of an issue (submits from home), but activation energy is high (opening the app, filling a form)
- AM: Low habit strength — submitting is not part of their routine
- RM: Moderate — wants to contribute but unsure if their data is "good enough"

**Design implications:** Needs low-friction quick-submit options. Photo-first workflow. Gentle quality guidance (not gates). Feedback that their data was useful (closes the motivation gap). Progressive forms that don't overwhelm.

---

### Ski Patrol Variants

#### Resort Patrol (Operations-Focused)

**Observation behavior:** Observations are embedded in operational routines — route checks, control work results, terrain assessments. Data is often captured in internal systems (patrol logs) rather than shared externally.

**What they observe:** Control results (did the shot produce a slide?), terrain conditions at specific runs, natural activity on visible slopes, weather at patrol stations.

**When/how they submit:** During or immediately after route checks. Internal radio reports are the primary channel; app submission is secondary.

**What they consume:** Forecast products, other patrol members' reports, neighboring resort observations during regional storms.

**COM-B specifics:**
- PC: Strong operationally; may not translate to observation reporting vocabulary
- PO: Dominant blocker — observations go into internal systems; cross-sharing requires a second submission
- SO: Internal culture prioritizes radio communication over app-based reporting
- AM: Habit is to report internally; external reporting is an extra step

**Design implications:** Integration with existing patrol communication systems. Submit-once architecture that routes data both internally and externally. Quick-capture that fits between radio calls and route checks.

#### Backcountry / Highway Patrol

**Observation behavior:** Observations from remote terrain not covered by resort patrol. Higher value per observation due to sparse coverage in their zones.

**What they observe:** Remote terrain conditions, large-scale natural avalanche activity, snowpack structure at elevation bands not accessible to most observers.

**When/how they submit:** In-field when possible; often delayed due to extended remote operations. May batch multiple observations at end of a multi-day cycle.

**COM-B specifics:**
- PC: Strong — specialized terrain knowledge
- PO: Severe — extended time in remote terrain, limited connectivity, competing operational demands
- RM: High — understands the value of their observations for zones with no other coverage

**Design implications:** Robust offline capability with multi-observation batching. Satellite-friendly data formats. High-value observation prioritization (their data fills coverage gaps).

---

### Guide Variants

#### Professional IFMGA/AMGA Guide

**Observation behavior:** Continuous terrain assessment as part of professional practice. Formal observations are secondary to real-time decision-making with clients.

**What they observe:** Terrain-specific conditions along their planned and actual routes. Client group behavior. Conditions that confirm or contradict the morning's forecast.

**When/how they submit:** Post-trip if at all. During the day, attention is on clients, not reporting. Submission is a professional courtesy, not a requirement.

**What they consume:** Morning forecast, recent observations from their operating zone, other guides' trip reports.

**COM-B specifics:**
- PC: Strong — deep terrain reading skills, but observation reporting is not their trained workflow
- PO: High friction — clients are the priority; reporting competes with rest, debrief, and next-day planning
- RM: Values the system but not enough to consistently prioritize submission over recovery time
- AM: No submission habit; post-trip routine is client debrief, not data entry

**Design implications:** Ultra-low friction post-trip capture. Voice-to-observation for the drive home. "Trip summary" format that captures route, conditions, and notable observations in one flow rather than per-observation forms.

#### Informal Trip Leader (Recreational)

**Observation behavior:** Makes terrain decisions for a group but rarely thinks of themselves as an "observer." Their observations are embedded in trip decisions, not externalized.

**What they observe:** Same terrain cues as a guide but with less formal structure. Route conditions, group energy, gut feelings about stability.

**When/how they submit:** Almost never. May post a trip report on social media with incidental observation data.

**What they consume:** Forecast, friend recommendations, social media trip reports. Rarely consumes raw observation data.

**COM-B specifics:**
- PC: Variable — some are highly skilled, others lead groups based on social authority rather than expertise
- PO: High activation energy — doesn't see themselves as having a "reporting" role
- RM: Low — doesn't identify as an observer or data contributor
- AM: No habit whatsoever; no cue to submit

**Design implications:** This variant is unlikely to become a regular contributor through the app alone. The highest-leverage approach is making them a better consumer — presenting observations and forecasts in a way that influences their terrain decisions. If contribution is a goal, a "trip log" format (not "observation report") that matches their self-concept may lower the identity barrier.

---

### Recreationist Variants

#### Trained Contributor (Avy 2+, Active Community Member)

**Observation behavior:** Submits structured observations semi-regularly. Active in online avalanche communities. Sees reporting as part of their identity as a "serious" backcountry user.

**What they observe:** Surface conditions, stability tests (when performed), natural activity, notable red flags. Quality varies but intent is high.

**When/how they submit:** Post-trip, usually same evening. May submit from the trailhead if connectivity exists.

**What they consume:** Forecast, all recent observations from their zone, community discussion.

**COM-B specifics:**
- PC: Moderate-to-strong — formal training, active learning
- PO: Moderate — willing to spend time on submission but frustrated by clunky tools
- RM: High — identity-driven ("I'm the kind of person who reports")
- AM: Developing habit; consistency depends on tool friction and feedback

**Design implications:** Good candidate for the feedback loop — showing impact reinforces their identity. Progressive forms that reward depth without requiring it. Peer visibility (contribution dashboards) feeds their social motivation.

#### Casual Consumer (Checks Conditions, Never Submits)

**Observation behavior:** None. Consumes forecast and observation data to plan trips. Never submits.

**What they consume:** Forecast danger rating, recent observations (especially from their planned zone), trip reports from others.

**COM-B specifics:**
- PC: Low-to-moderate — may misinterpret raw observation data
- PO: N/A for submission; for consumption, needs data translated into actionable terms
- RM: Low for contribution; moderate for consumption (wants to stay safe)
- AM: Consumption is habitual (check forecast before every trip); contribution is absent

**Design implications:** Not a contribution target. Design the consumption experience for this variant: observation summaries, danger signal aggregation, "what this means for your planned trip" cards. If observations are presented well, this variant makes better decisions — which is the system's ultimate goal.

#### Social Sharer (Posts Trip Reports with Incidental Data)

**Observation behavior:** Posts trip reports on social media or community forums. Reports contain incidental observation data (photos of snow conditions, descriptions of terrain) but not in structured form.

**What they observe:** Everything a trained contributor observes, but captured as narrative and photos rather than structured data.

**When/how they submit:** To social platforms, not to the observation system. Submission to the app is a separate, unfamiliar behavior.

**What they consume:** Social media trip reports, forecast, friend recommendations.

**COM-B specifics:**
- PC: Variable — observation quality embedded in trip reports ranges widely
- PO: Already creating content; the barrier is routing it to the right system, not creating it
- RM: Motivated by social validation (likes, comments), not data contribution
- AM: Strong habit of posting to social media; no habit of posting to observation systems

**Design implications:** The most interesting opportunity. This variant already produces observation data — it just goes to the wrong place. A "share to observation network" integration with social platforms, or a trip-report format that auto-extracts structured data from narrative + photos, could convert social sharing into system-useful observations without changing the actor's behavior.

---

## Core Behavior Diagnoses

### Behavior 1: Submitting Field Observations

**Current state: Realized but Friction-Filled (State 2)**

The behavior happens but the environment makes it painful.

**Symptoms:** Multiple devices and workarounds, post-field reporting (recall bias + delay), form fatigue, connectivity issues, inconsistent formats across organizations.

**Primary blockers:**

| Blocker | COM-B | Specific Barrier |
|---------|-------|-----------------|
| Tool/system constraints | PO | Reporting tools are clunky, desktop-oriented, or require connectivity |
| Time/resource scarcity | PO | Reporting competes with the observer's primary task |
| Workflow friction | PO | Too many steps between noticing something and it being in the system |

**Secondary blockers:**

| Blocker | COM-B | Specific Barrier |
|---------|-------|-----------------|
| Learned helplessness | AM | "Reporting is just painful, always has been" |
| Cognitive overload | PC | Translating field experience into form fields under adverse conditions |
| Cultural acceptance | SO | Organizations tolerate delayed, incomplete reporting |

---

### Behavior 2: Consuming and Interpreting Observations

**Current state: Partially Realized / Inconsistent (State 3)**

Consumed unevenly. Forecasters interpret expertly; patrol reads operationally; recreationists can't interpret raw data.

**Primary blockers:**

| Blocker | COM-B | Specific Barrier |
|---------|-------|-----------------|
| Mental-model variation | PC | Each persona interprets through a different cognitive lens |
| Procedural knowledge gaps | PC | Recreationists and some guides can't translate observations to terrain decisions |
| Local norms | SO | Each organization has its own conventions for interpreting observations |

**Secondary blockers:**

| Blocker | COM-B | Specific Barrier |
|---------|-------|-----------------|
| Resistance to standardization | RM | Experienced practitioners resist common frameworks |
| Raw data presentation | PO | Data presented as records, not actionable intelligence |
| Inconsistent terminology | PC | Same terms carry different weight across actors |

---

### Behavior 3: Cross-Boundary Sharing

**Current state: Weakly Realized (State 4)**

Everyone agrees it's valuable. It keeps getting displaced.

**Primary blockers:**

| Blocker | COM-B | Specific Barrier |
|---------|-------|-----------------|
| Competing urgencies | PO | Operational demands crowd out the extra step |
| Habit competition | AM | Existing habits go to internal systems |
| High activation energy | PO | Different logins, different formats, extra steps |

**Secondary blockers:**

| Blocker | COM-B | Specific Barrier |
|---------|-------|-----------------|
| Short-term focus | RM | Immediate needs override long-term network value |
| No triggers | PC | Nothing in the workflow prompts cross-sharing |
| Reactive culture | SO | Proactive sharing feels like a luxury |

---

### Behavior 4: Observation Quality and Completeness

**Current state: Partially Realized / Inconsistent (State 3)**

Quality varies dramatically. No shared standard for "good enough."

**Primary blockers:**

| Blocker | COM-B | Specific Barrier |
|---------|-------|-----------------|
| Variable standards | PC | "Representative" and "complete" mean different things to different observers |
| Procedural gaps | PC | Many observers lack systematic methodology training |
| Divergent norms | SO | Different organizations enforce different quality standards |

**Secondary blockers:**

| Blocker | COM-B | Specific Barrier |
|---------|-------|-----------------|
| Resistance to one method | RM | "My way works fine" |
| Permissive tools | PO | Forms accept whatever is entered |
| Transfer failure | PC | Classroom training doesn't translate to field practice |

---

## Interface Failure Map

```
Field Observer ──[submit]──> Observation Database ──[consume]──> Forecaster
      |                            |                                |
      |                            |                                v
  Ski Patrol ──[submit]──>         |                         Forecast Product
      |                            |                                |
  Guide ──[submit]──>              |                                v
      |                            |                     Guide / Recreationist
  Recreationist ──[submit?]──>     |                        (decision point)
```

### Critical Interfaces

| Interface | Failure Type | COM-B Root | Criticality |
|-----------|-------------|-----------|-------------|
| Observer -> Database | Timing, Quality, Completeness | PO (friction), AM (helplessness), PC (cognitive load) | High |
| Database -> Forecaster | Volume, Translation | PO (no filtering), PC (overload at volume) | High |
| Forecaster -> Guide/Recreationist | Translation | PC (mental-model gap), PO (no translation layer) | High |
| Observer -> Observer | Feedback absence | SO (no visibility), AM (no feedback loop) | Medium |
| Guide/Recreationist -> Database | Absence | PO (activation energy), RM (identity gap) | Medium |

---

## Blocker Concentration

| COM-B Code | Behaviors blocked | Actors affected |
|-----------|------------------|----------------|
| **PO** | 4 (submission, sharing, quality, interpretation) | All |
| **PC** | 3 (interpretation, quality, sharing) | Forecaster, Guide, Recreationist |
| **AM** | 3 (submission, sharing, quality) | Observer, Patrol, Guide |
| **SO** | 2 (interpretation, quality) | All |
| **RM** | 2 (sharing, last-mile motivation) | Guide, Recreationist |

**Dominant blocker: PO (Physical Opportunity)** — the environment is the primary problem.

---

## Recommended Interventions

### Priority 1: Reduce Submission Friction (Score: 15/15)
**State transition:** Friction-Filled -> Stable
**COM-B target:** PO | **BCW:** ER, EN

| Feature | Mechanism | Variant Impact |
|---------|-----------|---------------|
| Offline-first mobile capture | Remove connectivity barrier; sync on signal | Professional Observer, Backcountry Patrol |
| GPS + timestamp auto-capture | Eliminate manual location/elevation/aspect | All contributors |
| One-tap quick observations | Preset templates: whumpf, shooting crack, natural avalanche (<30 sec) | Volunteer Observer, Patrol, Guide |
| Photo-to-observation AI assist | Photo of snow profile pre-fills structured fields | All contributors |
| Voice-to-observation | Hands-free dictation in cold/gloved conditions | Professional Observer, Guide |

### Priority 2: Close the Feedback Loop (Score: 13/15)
**COM-B target:** AM, RM | **BCW:** INC, PE

| Feature | Mechanism | Variant Impact |
|---------|-----------|---------------|
| "Your observation was cited" notification | Connect action to downstream outcome | All contributors (especially Volunteer Observer) |
| Observation view counter | Show that data was consumed | All contributors |
| Contribution dashboard | Frequency, coverage, quality relative to network | Trained Contributor Recreationist |
| Coverage gap alerts | "Zone X has no observations today — your data would fill a critical gap" | Professional Observer, Backcountry Patrol |

### Priority 3: Guide Quality Through Design (Score: 12/15)
**State transition:** Inconsistent -> Consistent
**COM-B target:** PC, AM | **BCW:** TR, ER

| Feature | Mechanism | Variant Impact |
|---------|-----------|---------------|
| Progressive disclosure forms | Start with essentials; reveal depth by observation type | All (especially Volunteer Observer) |
| Inline quality nudges | "Adding aspect makes this 3x more useful to forecasters" | Volunteer Observer, Recreationist |
| Exemplar observations | "How an expert reported similar conditions" | Volunteer Observer, Trained Recreationist |
| Auto-validation | Flag impossible combinations before submission | All contributors |
| Completeness indicator | Visual score — nudge, not gate | All contributors |

### Priority 4: Standardize Interpretation (Score: 11/15)
**State transition:** Inconsistent -> Consistent
**COM-B target:** PC, SO | **BCW:** ED, TR, MO

| Feature | Mechanism | Variant Impact |
|---------|-----------|---------------|
| Observation summary layer | Plain-language, role-appropriate summaries | All consumers |
| Danger signal aggregation | Heat map of observation clusters and instability signals | Forecaster, Patrol |
| "What this means for you" cards | Role-specific interpretation per persona | Guide, Recreationist (especially Casual Consumer) |
| Shared glossary | In-app definitions with examples | All |

### Priority 5: Enable Cross-Boundary Sharing (Score: 11/15)
**State transition:** Weakly Realized -> Partially Realized
**COM-B target:** PO, AM | **BCW:** ER, INC

| Feature | Mechanism | Variant Impact |
|---------|-----------|---------------|
| Submit-once, share-everywhere | Auto-route based on location and type | Resort Patrol (biggest impact — eliminates double entry) |
| Organizational federation | Each org keeps their view; shared pool requires no extra effort | All organizations |
| Social media bridge | Extract structured data from trip reports posted to social platforms | Social Sharer Recreationist |

---

## System-Level Insights

### 1. The app is connective tissue, not a database
Every design decision should be evaluated by: does this make the interface between personas work better, or just make one persona's job easier in isolation?

### 2. The feedback loop is the highest-ROI missing feature
Observers submit into a void. Showing downstream impact is self-reinforcing — once established, it improves submission quality and frequency without additional intervention. It's a force multiplier for Priority 1.

### 3. Quality through design, not enforcement
Mandating completeness reduces submissions. Design the form so the path of least resistance produces good-enough data: smart defaults, auto-capture, progressive disclosure, gentle nudges.

### 4. The role variants reveal design conflicts
Professional Observers need form depth and speed. Volunteer Observers need simplicity and encouragement. Trained Recreationists need recognition. Casual Consumers need translation. A single interface cannot serve all variants — the app needs role-aware adaptive experiences.

### 5. The Social Sharer is an untapped data source
This variant already produces observation data — it just goes to social media. Converting social sharing into structured observations (without changing the actor's behavior) is a high-value, low-friction opportunity that most observation systems miss entirely.

### 6. The last-mile problem is real but partially addressable
The app cannot fix powder fever or optimism bias. But it can make risk concrete (terrain overlays), make conservative behavior visible (social proof), and reduce the gap between what people know and what they do at the decision point.
