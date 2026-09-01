---
name: prd-writer
description: Write a sharp, decision-forcing product requirements document (PRD), product spec, 1-pager, or product brief — problem-first, with crisp scope, success metrics and a tracking/instrumentation plan, management rules, edge cases, and verifiable requirements. Use when the user wants to draft, structure, tighten, or review any of these, OR describes the need without naming it ("write up this feature," "spec out X," "align eng and design on this," "turn this idea into something buildable," "what goes in the doc"). Also use to define success metrics or design a tracking plan (the events/properties that make metrics measurable), or to de-risk a spec with fuzzy problems, missing scope, unhandled edge cases, uninstrumented metrics, or unverifiable requirements. Do not use for pure engineering design docs/RFCs (architecture, data models, interfaces) — those belong to product-capability — or for deciding whether to build at all, which belongs to product-lens.
---

# PRD Writer

A PRD exists to make a team confidently build the right thing without you in the room. It succeeds when an engineer, designer, and stakeholder read it and reach the *same* understanding of what's being built, for whom, why, and how everyone will know it worked. It fails when it reads like a feature list with no problem behind it, hides decisions instead of forcing them, or uses words no two people would interpret the same way.

This skill produces that document. It is **problem-first** (the problem statement is the highest-leverage part — nail it before any requirement), **outcome-oriented** (defines the change in the user's world, not the screens), and **decision-forcing** (surfaces the open questions and non-goals people would otherwise discover mid-build).

## The one belief that drives everything

Most weak PRDs are weak because the author started writing requirements before understanding the problem. As Shreyas Doshi puts it, nailing the problem statement is "deceptively easy to get wrong, and when done well it's a superpower." So the work is front-loaded: spend disproportionate effort on *who hurts, how often, how badly, and what they do today* — and the requirements often write themselves.

A useful gut check borrowed from Amazon's Working Backwards method: if you can't write a compelling one-paragraph description of the outcome for the customer, you don't understand the idea well enough to build it yet. Write the ending first.

## The three pillars of a well-written spec

Once the problem is clear, a complete spec rests on three layers that must not be conflated:

- **User Stories** — the high-level goal from the user's point of view: *what* they want to achieve and *why* it matters.
- **Acceptance Criteria** — the step-by-step path: what must be true or visible for the experience to be considered complete.
- **Management Rules** — the invisible logic underneath: what the system must enforce, validate, or calculate to make it all work, regardless of how visible it is to the user.

A spec that captures only the visible behavior (stories + acceptance criteria) and forgets the invisible logic (management rules) and the 5% off the happy path (edge cases) is the most common way a "finished" PRD still ships bugs.

## Non-negotiable: flag what's missing, never fill the gap with a guess

A PRD's value collapses the moment it states something nobody verified as if it were settled. So when an input you need is absent and you can't reasonably infer it from what's available, **do not fabricate it and do not paper over it with confident-sounding prose or a plausible default.** Mark it instead, in-line, with one of:

- `[MISSING: <what's needed> — <who owns it>]` — a required input you simply don't have.
- `[ASSUMPTION: <the inferred value> — confirm with <owner>]` — something you inferred to keep moving, labelled as a guess, not a fact.
- `[NEEDS EVIDENCE: <claim>]` — a stated fact with no source yet.

Surface them up front: open the doc with a short **§0 Inputs I don't have yet** list so the reader sees the gaps before the content, and never let a `[MISSING]` hide silently inside a requirement or a metric. This applies to every section. **Never invent** business rules, target users, pricing, compliance obligations, numeric success targets, or evidence — these cannot come from a codebase or a hunch. A spec that honestly says "I don't have this yet" is far more useful than one that reads complete but is partly fiction; the gaps *are* the finding, and naming them is the job, not a failure to finish it.

If the missing inputs are central (no real problem, no owner of the metric, no validated evidence), say so plainly at the top rather than producing a polished doc resting on air.

## When to activate

- The user asks for a PRD, product spec, 1-pager, product brief, feature doc, PR-FAQ, or pitch.
- The user describes a feature or product idea and wants it "written up," "specced out," "documented," or made "ready for the team."
- The user wants an existing spec reviewed, tightened, de-biased, or pressure-tested.
- A vague idea needs to become something design and engineering can act on.

Hand off instead when: the question is *whether to build at all* or *is this the right bet* → that's diagnosis (`product-lens`). The artifact needed is an engineering design doc / capability contract — architecture, interfaces, invariants, data model → `product-capability`. Pure acceptance-criteria capture for an already-clear change → `intent-driven-development` (this skill borrows its rigor for the requirements section but covers the whole product narrative). Breaking the finished PRD into an epic and backlog tickets → `jira-story-writer`.

## Workflow

### 1. Gather what only the user knows — ask the minimum, infer the rest

Inspect anything already available (the conversation, attached docs, the repo, prior specs, research) before asking. Then ask **only** the questions whose answers you cannot reasonably infer and that would materially change the document. Group them; don't interrogate. The non-negotiable unknowns are usually:

- **Who** specifically is this for? (a named segment or persona, not "users")
- **What's the pain**, and how do you know it's real? (frequency, severity, current workaround, evidence)
- **What outcome** counts as success, and how will you measure it?
- **What's the appetite / constraint** — how much is this worth (time, scope), and what's the deadline or event driving it?
- **What's explicitly out of scope** or already decided?

If the user can't answer the problem/evidence questions, that's the most important thing to surface — say so plainly rather than papering over it with confident-sounding requirements. A PRD built on an unvalidated problem should say so at the top.

Never invent product truth. Business rules, target users, pricing, compliance obligations, and priorities cannot be inferred from a codebase or guessed — capture them from the user or mark them as open questions / assumptions to confirm.

### 2. Choose the depth — use the smallest document that does the job

Match the artifact to the decision's weight. Bigger docs are not better; Intercom's rule is that forcing a brief onto one page makes you "much better at describing the problem you're solving."

| Depth | Use when | Produce |
| --- | --- | --- |
| **1-Pager / Brief** | Early idea, single team, low-to-moderate risk, need alignment fast | Problem, target user, outcome + metric, sketch of approach, scope/non-goals, open questions. ~1 page. |
| **Full PRD** | Cross-functional build, multiple surfaces, meaningful risk or investment | The full template below. |
| **PR-FAQ** | New product / 0→1 bet, need to test desirability before committing | Future press release (the outcome as if already shipped) + internal & external FAQ that stress-tests the hard questions. |
| **Review** | An existing spec needs tightening | Don't restart. Diagnose against the Quality Bar, return targeted fixes. |

When unsure, default to the 1-Pager and offer to expand. It's easier to grow a tight doc than to rescue a bloated one.

### 3. Write it — problem before solution, always

Draft in the order of the template (problem → outcome → users → requirements → rules → edge cases → scope → risks → open questions). Writing top-to-bottom enforces the discipline: you literally cannot specify requirements until you've articulated the problem and the success metric.

Then edit hard. Editing — deciding what to cut and what to sharpen — is where the value is; a first draft that lists everything is the easy 80%. Cut requirements that don't trace back to the problem. Replace every vague word.

### 4. Self-check against the Quality Bar, then deliver

Before returning the document, run it through the Quality Bar below and fix anything that fails. Present the doc, then flag the two or three open questions or assumptions most likely to change the build — those are what the team should resolve first.

## PRD template (full depth)

Omit sections that don't apply; never pad. Keep each section to the shortest length that conveys the decision.

```markdown
# PRD: <Feature / product name>

**Author:** <name>   **Status:** Draft | In review | Approved
**Last updated:** <date>   **Stakeholders:** <eng / design / data / GTM leads>
**One-liner:** <In one sentence: who gets what outcome, and why it matters now.>

## 0. Inputs I don't have yet
The inputs this doc needs but the user/source didn't supply — listed here, not guessed at below. Delete this section only when it's genuinely empty.
- `[MISSING: <what's needed> — <who owns it>]`
- `[NEEDS EVIDENCE: <claim stated below that isn't yet backed by data>]`

## 1. Problem
The single most important section. State the problem as a specific story, not an abstraction.
- **Who** has this problem (named segment/persona).
- **The pain:** what they're trying to do, where it breaks, how often, how badly.
- **Today's workaround** and why it's inadequate.
- **Evidence** it's real: data, research, support volume, quotes. If thin, say so.
- **Why now:** what changed (market, tech, behavior, strategy) that makes this worth doing today.

## 2. Goals & success metrics
- **Outcome we want:** the change in the user's world or the business, stated as a result, not a feature.
Separate three kinds of metric — the 3–4 cap applies to the first kind only:
- **Success metrics — pick 3–4 MAX** (more = confused definition of success, more instrumentation,
  higher analytics cost). These are what you *optimize*. Spread them across the three tiers so you see cause and effect:
  - **Engagement** (what users *do* — fast feedback on usability/adoption): clicks, uploads, time spent.
  - **Funnel** (how users *progress* — find friction): step completion, drop-off rate.
  - **Business/impact** (why it *matters* — ties to strategy): bookings, revenue, retention.
  Name **one primary metric** among them — the single number that tells us it worked (with a target or direction).
- **Guardrail metrics** (not counted in the cap): what must NOT get worse (latency, churn, support load,
  false-positive/false-green rate). You don't optimize these; you watch them and roll back if they regress.
- **Diagnostic metrics** (not counted in the cap, optional): instrument-and-watch numbers that *explain*
  movement but don't gate the launch (e.g. attach rate, ARPU). When a stakeholder wants "just one more metric,"
  this is usually where it belongs — so the success set stays sharp.
- **Tracking plan — make each metric *computable*, not just named.** An event with the right name is
  not a measured metric. For every metric, write its **formula** (numerator/denominator, or the A/B
  comparison), then list the events + properties that supply *every term* — and check each event carries
  the **key** its formula needs:
    - **Identity** — per-user, repeat, or retention metrics need a stable `user_id`/`entity_id` on the
      outcome event, or you can't tell a returning user from a new one.
    - **Correlation key** — a rate that links two events (e.g. "% of alerts acted on") needs a *shared id*
      on both (e.g. `alert_id` on the alert-sent **and** action-taken events) to attribute one to the other.
    - **Segment/dimension flag** — comparison or A/B metrics need the dimension on the *outcome* event
      (e.g. `badge_visible` on `listing_booked`), not just on the impression.
    - **Context key** — a "during X" metric (a fault *during a rental*) needs the window id (e.g. `trip_id`)
      on the event, so it isn't a fragile timestamp join.
  Then sanity-check **release alignment**: a metric's events must ship no later than the release where the
  metric has to hold — **guardrails are instrumented from launch**, not in a later phase.
  Example: `photo_uploaded { user_id, format, upload_time }`, `clicked_next { user_id, session_id }`.
- **Non-goals / explicitly not measuring:** keeps the metric honest.

## 3. Target users & key use cases
- Primary persona(s) and the top 1–3 jobs-to-be-done / use cases this serves.
- The core user story or two, written 4-part so the trigger is explicit:
  "As <persona>, when <situation/trigger>, I want <capability>, so that <outcome>."

## 4. Proposed solution
- The approach at the level of *what the user can now do*, not pixel-level UI.
- The critical user journey, end to end (happy path).
- **Workflow diagram:** include (or link) a flow diagram of the journey showing the happy path
  *and its decision branches* (Figma / Miro / Lucidchart). A diagram catches missing steps that prose hides.
- Link to designs/prototypes if they exist; the PRD describes intent, designs show form.

## 5. Requirements
Each requirement is observable and verifiable — two people would agree whether it's met. Use IDs so they're referenceable in build and QA. Mark priority.

| ID | Requirement (observable behavior) | Priority |
| --- | --- | --- |
| R1 | <Given/when/then-style behavior. No "fast," "intuitive," "robust" without a defined measure.> | Must / Should / Could |

### 5b. Management rules (system constraints)
The invisible logic the system must enforce, validate, or calculate — independent of UI. Easy to forget, expensive to discover late. Capture at least:
- **Limits & counts:** <e.g. min 5 / max 100; what happens at the boundary>
- **Formats & sizes:** <accepted file types, max size, reject/error behavior>
- **Security & compliance:** <content scanning, permissions, data retention, privacy obligations>
- **Calculations & validation:** <derived values, server-side validation, idempotency>

For high-risk requirements (auth, payments, data migration, privacy), add the verification method and any prohibited side effect — borrow the acceptance-criteria rigor from `intent-driven-development`.

## 6. Edge cases & error states
The ~5% of cases that aren't the happy path — the ones that quietly become bugs. For each: the trigger and the expected behavior.
- <Trigger, e.g. "connection drops mid-action"> → <expected behavior / message / recovery>
- <Boundary, e.g. "max exceeded / min not met"> → <expected behavior>
- <Bulk/odd input, e.g. "user drags & drops many items at once"> → <expected behavior>
Route each one: a heavy edge case that needs real development becomes its own requirement (or a story later); a light one becomes an acceptance criterion or a management rule on an existing requirement.

## 7. Scope & constraints
- **In scope:** what this delivers.
- **Out of scope / no-gos:** tempting adjacent work explicitly excluded (the most-skipped, most-valuable section).
- **Appetite / constraint:** how much this is worth — "we're giving this N weeks," a budget, a fixed date. A constraint, not an estimate.
- **Dependencies & assumptions:** other teams, systems, or beliefs this rides on.

## 8. Risks & rabbit holes
- Technical unknowns, unsolved design problems, or interdependencies that could blow the appetite.
- For each: the risk and how we'll de-risk or bound it.

## 9. Open questions
- [ ] Decisions still required, who owns each, and by when. These are the point of the doc — make them loud, don't bury them.

## 10. Rollout & launch (when relevant)
- **Phasing — Alpha → Beta → Stable:**
  - *Alpha:* internal/opt-in power users; validate core functionality; expect major bugs.
  - *Beta:* a small % of external users; validate real usage, UX friction, performance, edge cases.
  - *Stable:* general availability; fully tested and documented; maximize adoption.
- Flags, who gets it first, how we learn, and what would make us roll back.

## 11. Testing & business-critical flows (when relevant)
- Testing validates the feature works before/while it reaches users: core functionality has no blocker
  bugs, all tracking events fire correctly, and the UX has no confusing or broken steps.
- **Flag the business-critical flows** this feature touches — the ones that, if broken, directly hurt
  the business (e.g. "publish a listing," "book a stay"). Those require full regression before any release,
  even for a change that looks small.
```

## Quality Bar — the document must pass all of these

Modeled on the pass/fail discipline of `intent-driven-development`: a "no" anywhere means revise before delivering.

- [ ] **Problem is concrete and evidenced.** A reader can picture a specific person hitting a specific wall. Evidence is cited, or its absence is flagged.
- [ ] **Success is measurable, and bounded.** A primary metric with a direction/target — "metric, not vibes." ≤4 metrics across the engagement/funnel/business tiers, each backed by a named event. Guardrails name what mustn't regress.
- [ ] **Metrics are actually computable.** For each metric you can write the formula and point to the event(s) that supply every term, and each event carries the key the formula needs — **identity** for per-user/retention metrics, a **correlation key** for two-event rates, a **dimension flag** on the outcome event for comparisons/A-B, a **context key** for "during X" joins. A metric whose events can't compute it is not instrumented, however good the names sound.
- [ ] **Instrumentation ships in time.** Each metric's events land no later than the release where the metric must hold; guardrail events are present from launch, not deferred to a later phase.
- [ ] **Nothing fabricated; gaps are flagged.** Every fact is sourced, inferred-and-labelled (`[ASSUMPTION]`), or flagged (`[MISSING]` / `[NEEDS EVIDENCE]`) — never a silent guess. Required inputs the user didn't provide are listed in §0 up top, not invented to make the doc look finished.
- [ ] **Outcome over output.** Goals describe a change in the user's world, not a list of features shipped.
- [ ] **Every requirement is verifiable.** No "correctly," "seamlessly," "fast," "intuitive," "robust" without an observable definition. Each requirement traces to the problem.
- [ ] **Invisible logic is captured.** Management rules (limits, formats, security, calculations) are stated, not left implicit in the UI behavior.
- [ ] **Edge cases enumerated.** The main failure/boundary states are listed with expected behavior and routed (own requirement vs. acceptance criterion vs. management rule).
- [ ] **Scope has teeth.** Non-goals are explicit. There's an appetite/constraint, not an open-ended wishlist.
- [ ] **Decisions are forced, not hidden.** Open questions are visible with owners; assumptions are labeled as assumptions, not stated as facts.
- [ ] **No invented truth.** Business rules, users, and constraints came from the user or an authoritative artifact — nothing reconstructed from code or wishful thinking.
- [ ] **Right-sized.** As short as it can be while still aligning the team. If a section isn't earning its place, it's cut.

## Anti-patterns to catch (in your draft or the user's)

- **Solution in search of a problem** — the doc opens with the feature and reverse-justifies a problem. Fix: rewrite Section 1 first; if no real problem survives, that's the finding.
- **The everything-list** — dozens of "requirements," no priority, no appetite. Fix: force Must/Should/Could and a constraint.
- **Vibes as metrics** — "improve engagement," "make it delightful." Fix: one primary number with a target, instrumented by a named event.
- **Metric sprawl** — ten dashboards, no clear success signal. Fix: cap at 3–4 metrics across the tiers.
- **Named but not measurable** — the tracking plan lists an event, but the metric needs a key the event doesn't carry: a retention metric on an event with no `user_id`, a "% acted on" rate with no shared `alert_id`, an A/B comparison whose dimension never reaches the outcome event, a "during a trip" join with no `trip_id`. Fix: write the formula first, then add the identity / correlation / dimension / context key each term needs.
- **Guardrail instrumented too late** — the metric must hold from launch, but its event ships in a later phase (false-green monitoring in V3 while the badge ships in MVP). Fix: pull the guarding event into the launch release.
- **Vague requirements** — "the system should be fast and secure." Fix: define the observable threshold or move it to a human-review judgment with named evidence.
- **Invisible logic left invisible** — file limits, formats, permissions discovered mid-build. Fix: write the management rules section.
- **Happy-path-only** — no edge cases, so error states get improvised in code. Fix: enumerate the 5% and route them.
- **Hidden decisions** — disagreements smoothed over in prose. Fix: pull them into Open Questions with owners.
- **No non-goals** — scope creep is pre-loaded. Fix: write the no-gos.
- **Implementation masquerading as requirements** — specifying the *how* (table schemas, API shapes) in a product doc. Fix: state the user-visible promise here; hand the engineering contract to `product-capability`.

## Reference files

For concrete models of what good looks like, read `references/examples.md` — it has a filled 1-Pager, a PR-FAQ opening, and a before/after that turns a vague ask into verifiable requirements.

## A note on style

Write for a smart reader who is short on time and allergic to filler. Prefer plain prose and tight tables over decoration. The author's job, per Shreyas Doshi, is editing — choosing what matters — not authoring volume. A PRD you can read in five minutes and act on beats a thorough one nobody finishes.
