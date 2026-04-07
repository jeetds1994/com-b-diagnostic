# Intervention Quality Criteria

## What this file is

For each BCW (Behavior Change Wheel) intervention function, this file defines what **good implementation** looks like, what **poor implementation** looks like, common failure modes, and examples from avalanche observation and reporting contexts.

Use this file when designing or evaluating interventions selected via `com-b-to-bcw-intervention-function-mapping.md`. The BCW mapping tells you *which* intervention function to use; this file tells you *how* to implement it well.

---

## ED — Education

**Purpose:** Increase knowledge or understanding.

### Good Implementation
- Contextual and embedded in the workflow — appears at the moment of need, not in a separate knowledge base
- Specific to the actor's role and the decision they are making
- Uses concrete examples, not abstract principles
- Progressive — builds on what the actor already knows
- Short, scannable, and optional (does not block the workflow)

### Poor Implementation
- Standalone documentation that requires the actor to seek it out
- Generic information not tailored to the actor's role or context
- Front-loaded (all education happens before the workflow, none during)
- Lecture-style content that assumes the actor will retain and apply it later
- Mandatory reading that creates friction without building understanding

### Common Failure Modes
- **Information dump:** Providing all possible knowledge upfront instead of drip-feeding at the point of need
- **Knowledge ≠ behavior:** Actor understands what to do but the education does not translate to action (because the blocker was never really PC — it was PO or AM)
- **Maintenance neglect:** Educational content becomes outdated as the system evolves

### Avalanche Observation Example
- **Good:** When an observer leaves the "aspect" field blank, a tooltip appears: "Aspect tells forecasters which slopes are affected. Tap the compass to auto-detect from GPS." Education is embedded, specific, and action-oriented.
- **Poor:** A 20-page "Observer's Guide to Quality Reporting" PDF linked from the app settings. Few observers ever open it. Those who do retain little because it's disconnected from the submission workflow.

---

## TR — Training

**Purpose:** Build skills or procedural know-how.

### Good Implementation
- Hands-on practice in realistic conditions (or realistic simulations)
- Progressive skill-building with feedback on performance
- Scaffolded — starts simple, adds complexity as skill develops
- Repeated exposure to the skill in varied contexts (not one-time)
- Feedback is immediate and specific ("you missed this" not "try harder")

### Poor Implementation
- Classroom-only training with no field practice component
- One-time training event with no follow-up or reinforcement
- Training on the tool's interface without training on the underlying judgment
- Assessment that tests knowledge recall, not skill application

### Common Failure Modes
- **Transfer gap:** Training environment doesn't match real conditions (warm classroom vs. cold field)
- **Skill decay:** Skills learned in training degrade without regular practice and feedback
- **Tool training vs. behavior training:** Teaching how to use the app without teaching how to make good observations

### Avalanche Observation Example
- **Good:** A "training mode" in the app that shows observers an exemplar observation alongside their own submission: "Here's how an experienced observer reported similar conditions. Compare your entry." Repeated exposure builds calibration over time.
- **Poor:** An annual in-person training day where observers practice filling out the form in a classroom. By the time storm season arrives, the skills have decayed and field conditions introduce challenges the training didn't cover.

---

## PE — Persuasion

**Purpose:** Shift beliefs or emotions; motivate through argument, framing, or salience.

### Good Implementation
- Makes the value of the behavior visible and concrete (not abstract)
- Uses social proof — shows that respected peers perform the behavior
- Frames the behavior in terms the actor already values (safety, reputation, efficiency)
- Uses outcome feedback to connect the actor's action to downstream impact
- Emotionally resonant without being manipulative

### Poor Implementation
- Abstract appeals to values that don't connect to the actor's daily experience
- Guilt-based messaging ("you should be doing this")
- One-time campaigns that create a spike but no sustained change
- Persuasion that contradicts the actor's lived experience of the behavior

### Common Failure Modes
- **Credibility gap:** The persuasion source is not trusted by the target actor
- **Reactance:** Heavy-handed persuasion triggers resistance ("don't tell me what to do")
- **Asymmetric framing:** Emphasizing benefits without acknowledging real costs erodes trust

### Avalanche Observation Example
- **Good:** "Your observation from Tuesday was cited in the Northern Mountains forecast and contributed to a terrain closure decision." This connects the observer's action to a concrete downstream outcome they care about.
- **Poor:** A banner in the app saying "Your observations save lives!" — true but abstract, and after the tenth time seeing it, observers ignore it entirely.

---

## INC — Incentivization

**Purpose:** Reinforce behavior via rewards, recognition, or positive consequences.

### Good Implementation
- Rewards the behavior, not just the outcome (submitting a quality observation, not just "being right")
- Recognition is visible to peers who the actor respects
- Incentives are proportional and sustainable (not one-time prizes that distort behavior)
- Intrinsic motivation is reinforced alongside extrinsic rewards
- Progress visibility (streaks, contribution counts) creates self-reinforcing momentum

### Poor Implementation
- Large extrinsic rewards that distort behavior (gaming the metric)
- Incentives that reward volume over quality (more submissions = more points)
- Competition that discourages collaboration or creates social friction
- Rewards that are invisible to peers (private achievement badges no one sees)

### Common Failure Modes
- **Metric gaming:** Observers submit low-quality observations to inflate their count
- **Crowding out intrinsic motivation:** Extrinsic rewards replace internal drive — when rewards stop, behavior stops
- **Inequity:** Incentive structures favor actors with more field access (professional observers vs. recreationists)

### Avalanche Observation Example
- **Good:** A contribution dashboard showing each observer's submission frequency, coverage map, and a "forecast impact" indicator. Visible to the observer network. Recognizes consistency and quality, not just volume.
- **Poor:** A leaderboard ranking observers by number of submissions per month. Drives observers to submit low-effort observations from parking lots to increase count.

---

## COE — Coercion

**Purpose:** Apply pressure, consequences, or negative expectancies.

### Good Implementation
- Used sparingly and only when safety is at stake
- Consequences are clear, predictable, and proportional
- Applied to the behavior (not the person) — "this observation does not meet minimum standards" not "you are a bad observer"
- Paired with enablement — the actor has a clear path to compliance
- Transparent about why the standard exists and what it protects

### Poor Implementation
- Punitive without providing guidance on how to improve
- Applied inconsistently (some actors face consequences, others don't)
- Disproportionate to the behavior gap
- Creates fear that suppresses the behavior entirely (actors stop submitting to avoid being judged)

### Common Failure Modes
- **Suppression effect:** Coercion reduces behavior frequency instead of improving quality — actors stop submitting rather than risk rejection
- **Underground behavior:** Actors perform the behavior outside the system to avoid scrutiny
- **Resentment:** Excessive coercion erodes trust and motivation

### Avalanche Observation Example
- **Good:** Observations missing critical safety fields (location, date, instability indicators) are flagged with "This observation cannot be routed to forecasters without [field]. Add it now?" The standard is clear, the fix is easy, and the reason is concrete.
- **Poor:** Rejecting observations that don't meet a high completeness threshold. Observers who submitted useful partial data stop submitting entirely because they feel their contributions are unwelcome.

---

## RE — Restriction

**Purpose:** Limit options to reduce competing behaviors.

### Good Implementation
- Removes genuinely unhelpful options (not just options the designer dislikes)
- Reduces cognitive load by narrowing choices to valid ones
- Constraints are logical and self-explanatory (the actor understands why an option isn't available)
- Preserves the actor's ability to override when they have a legitimate reason

### Poor Implementation
- Removes options that some actors legitimately need
- Rigid constraints that don't account for edge cases
- Restrictions that feel arbitrary or patronizing
- No override mechanism for experienced actors

### Common Failure Modes
- **Workaround generation:** Actors route around restrictions by using external tools or free-text fields
- **Expert frustration:** Experienced actors are constrained by guardrails designed for novices
- **Loss of signal:** Restricting input options may prevent actors from reporting unusual or novel conditions

### Avalanche Observation Example
- **Good:** The observation form only allows elevation values within the range of the selected zone. Prevents data entry errors without restricting what can be observed.
- **Poor:** Limiting observation types to a fixed dropdown with no "other" option. An observer who encounters an unusual condition (e.g., a rain crust at an unexpected elevation) cannot report it because the form doesn't allow it.

---

## ER — Environmental Restructuring

**Purpose:** Change the physical or social environment to reduce friction and introduce cues.

### Good Implementation
- Makes the desired behavior the path of least resistance
- Removes environmental barriers before asking actors to change their behavior
- Introduces cues at the right moment (not just anywhere)
- Changes are invisible to the actor — the environment just works better
- Reduces steps, clicks, fields, decisions, and context-switches

### Poor Implementation
- Adds new environmental elements (notifications, prompts, dashboards) without removing friction
- Restructures the environment in ways that create new friction elsewhere
- Changes that are visible and annoying rather than invisible and smooth
- Over-reliance on notifications and reminders instead of genuine friction reduction

### Common Failure Modes
- **Notification fatigue:** Too many environmental cues become noise
- **Shifting friction:** Reducing friction for one actor increases it for another
- **False simplicity:** Removing steps that were actually load-bearing (e.g., a confirmation step that caught errors)

### Avalanche Observation Example
- **Good:** GPS auto-captures location, elevation, and aspect when the observer opens the app. The observer doesn't need to enter this data manually. The environment does the work.
- **Poor:** Adding a daily push notification "Don't forget to submit your observations!" without reducing the actual friction of submission. The reminder is environmental restructuring, but it addresses the wrong barrier (the problem is PO/friction, not AM/forgetting).

---

## MO — Modeling

**Purpose:** Show examples of good behavior or patterns to imitate.

### Good Implementation
- Models come from actors the target respects and identifies with
- Models show the process, not just the outcome ("here's how I decide what to report")
- Multiple models for multiple contexts (not one idealized example)
- Models are embedded in the workflow, not in a separate gallery
- Models evolve as the system matures

### Poor Implementation
- Models from authority figures the target doesn't identify with
- Only showing perfect outcomes without the messy process
- Static models that don't reflect current conditions or practices
- Models that are so polished they feel unattainable

### Common Failure Modes
- **Aspiration gap:** The model is so far from the actor's current ability that it discourages rather than inspires
- **Context mismatch:** The model was created under different conditions than the actor faces
- **Single model bias:** One canonical example becomes a template that actors copy without understanding

### Avalanche Observation Example
- **Good:** When submitting an observation of a specific type (e.g., "natural avalanche"), the form shows an exemplar: "Here's how an experienced observer reported a similar natural avalanche last week." The exemplar includes the same fields the observer is filling out.
- **Poor:** A "Hall of Fame" page showing the season's best observations. Newer observers feel their contributions don't measure up and are discouraged from submitting.

---

## EN — Enablement

**Purpose:** Remove barriers beyond education and training; make behavior possible or easier.

### Good Implementation
- Directly addresses the specific barrier the actor faces (not a generic capability gap)
- Reduces the prerequisite capabilities needed to perform the behavior
- Provides tools, infrastructure, or support that did not previously exist
- Makes the behavior possible for actors who previously could not perform it at all
- Works at the system level — benefits all actors, not just one

### Poor Implementation
- Provides resources that actors don't know how to use (enablement without education)
- Removes one barrier but leaves a harder barrier in place
- Enablement that helps some actors but creates new dependencies for others
- Infrastructure that requires maintenance nobody owns

### Common Failure Modes
- **Orphaned infrastructure:** An enabling tool is built but nobody maintains it after launch
- **Partial enablement:** The barrier is reduced but not removed — actors still can't perform the behavior reliably
- **Dependency creation:** Actors become dependent on the enablement and cannot perform the behavior without it

### Avalanche Observation Example
- **Good:** Offline-first mobile app with automatic sync. This enables field observations in areas with no cell service — a barrier that previously made real-time reporting impossible for backcountry observers. The barrier is removed, not just reduced.
- **Poor:** Providing observers with satellite communicators for real-time upload, but the communicators require a subscription that observers must pay for themselves. The barrier shifts from "no connectivity" to "no budget."

---

## Quick Reference Summary

| BCW Function | Good Implementation Signal | Poor Implementation Signal |
|-------------|---------------------------|---------------------------|
| ED | Appears at point of need, role-specific | Separate knowledge base nobody reads |
| TR | Hands-on, feedback-rich, repeated | One-time classroom event |
| PE | Connects action to concrete outcome | Abstract value appeals |
| INC | Rewards quality and consistency | Rewards volume (gaming) |
| COE | Clear, proportional, paired with help | Punitive, suppresses behavior |
| RE | Reduces cognitive load, preserves overrides | Frustrates experts, generates workarounds |
| ER | Makes desired behavior path of least resistance | Adds notifications without removing friction |
| MO | Relatable, process-focused, embedded | Aspirational, static, discouraging |
| EN | Removes the actual barrier to action | Partial fix, creates new dependencies |
