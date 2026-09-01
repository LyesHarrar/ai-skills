---
name: jira-story-writer
description: Turn a PRD, feature, or product idea into a well-structured backlog — one epic and a set of vertical-slice user stories with INVEST quality, management rules, edge cases, tracking events, and verifiable acceptance criteria, formatted for Jira (paste or CSV import). Use whenever the user wants to write or break down epics, user stories, or backlog items; "turn this PRD into tickets/stories," "break this feature into stories," "write the epic for X," "split this story, it's too big," "draft acceptance criteria for these stories," "add the management rules / edge cases / tech tasks for this," or "what stories do we need for this." Chains naturally off a PRD (e.g. from prd-writer) but works from any feature description. Drafts only — it does NOT create issues in Jira directly; it produces import-ready content for the user to review and load. Do not use to write the PRD itself (that's prd-writer) or to capture acceptance criteria for a single already-scoped engineering change (that's intent-driven-development).
---

# Jira Story Writer

This skill turns product intent into a backlog a team can pull from: **one epic** that names the outcome, broken into **user stories** that are each a thin vertical slice of real user value, each with **acceptance criteria two people would agree on**, the **management rules** the system must enforce, and the **tracking events** that prove it worked. It is **PRD-first** (built to consume a doc like a prd-writer PRD) but works from any feature description, and it is **draft-only** — it produces Jira-ready content for the user to review and import, never writing to Jira itself.

## The two beliefs that drive everything

**1. A story is a slice of value, not a layer of the system.** The classic failure is splitting work horizontally — "build the database," "build the API," "build the UI" — so nothing is usable until the last ticket lands. Following Jeff Patton, slice *vertically*: each story should walk the user through a complete (if minimal) piece of the journey. A good story, even a tiny one, produces something a user could touch. The first release is a "walking skeleton" — the thinnest end-to-end path through the whole journey.

**2. A story is a placeholder for a conversation, not a contract.** Ron Jeffries' 3 Cs — Card, Conversation, Confirmation — remind us the ticket is a *token* for a shared understanding, and the acceptance criteria are the *confirmation* of what "done" means. So write enough that the team shares intent and can verify completion, but don't over-specify the *how*. The "so that…" matters more than a wall of detail: it tells the team why the story exists, so they can negotiate the solution.

## The anatomy of a story (the three layers + two wrappers)

A well-formed story carries three layers that must not be conflated, plus two wrappers the slides emphasize:

- **The story** — the high-level goal: what the user wants and why.
- **Acceptance Criteria** — the visible path: what must be true/visible for "done."
- **Management Rules** — the invisible logic the system must enforce, validate, or calculate (limits, formats, security), regardless of UI.
- **Edge cases** (wrapper) — the 5% off the happy path, routed to the right place.
- **Tracking** (wrapper) — the events the story must fire so the epic's success metric is measurable.

Optionally, under a story sit **Tech Tasks** — the Frontend / Backend / Infra implementation sub-tasks (the *how*).

## Non-negotiable: flag what's missing, never invent it

When the source doesn't give you what a story needs — a persona, the real benefit, a management-rule limit, an acceptance threshold, a success metric, or a tracking event/key — **do not guess it into existence to make the ticket look complete.** Mark it instead:

- `[MISSING: <what's needed> — <who owns it>]` on the story, and repeat it as an open question.
- `[ASSUMPTION: <inferred value> — confirm]` when you inferred something to keep the slice coherent.

Never fabricate acceptance-criteria thresholds, management-rule limits/formats, personas, success metrics, or event names/keys. If you can't write a *verifiable* AC because a number is unknown, write `[MISSING: threshold for X]` rather than inventing a plausible one — an invented threshold reads as fact and ships as a bug. End delivery by listing every `[MISSING]` and `[ASSUMPTION]` so the team resolves them before pulling the work. A short story that honestly flags its unknowns beats a fully-specified one that's quietly making things up.

## When to activate

- The user wants to write an epic, user stories, or backlog items — or break a PRD/feature into them.
- The user says "turn this into tickets," "what stories do we need," "draft the backlog," or "split this story."
- The user wants acceptance criteria, management rules, edge cases, or tech sub-tasks written for a set of stories.

Hand off instead when: the user needs the **PRD/product narrative** written first → `prd-writer`. They need rigorous **acceptance criteria for one already-scoped change** (not a backlog) → `intent-driven-development`. They need an **engineering design / capability contract** → `product-capability`.

## Workflow

### 1. Ground in the source — extract, don't invent

If a PRD or feature doc exists, read it and pull out the raw material:

- The **outcome** and **success metric** (these become the epic's goal — and the per-story tracking events trace back to them).
- The **requirements** (these become candidate stories) and their **priorities** (Must/Should/Could map cleanly to story priority and release sequencing).
- The **management rules** (these attach to the stories they govern, not as separate tickets).
- The **edge cases** (route them — see step 5).
- The **personas / actors** (these become the "As a …" — never settle for "As a user").
- The **scope and non-goals** (non-goals are a fence: don't generate stories outside it).

If there's no PRD, ask only the few things you can't infer: who the user is, what outcome the feature delivers, and what's explicitly out of scope. Don't invent product truth — flag unknowns as open questions on the relevant story rather than guessing business rules.

### 2. Frame the epic — outcome, not feature-dump

The epic names the goal a stakeholder would recognize, sized in **weeks-plus** (if it's days, it's a story; if it spans quarters/teams, it may be an initiative). Capture:

- **Epic summary:** the outcome in plain language.
- **Goal & success metric:** why it exists and how we'll know it worked (pull from the PRD; keep to the 3–4 metrics that matter).
- **Measurement plan (the epic owns this once; stories inherit it):** a small table of *metric → formula → event(s) → required key → which story fires it → release*. This is the single home for traceability — each story's Tracking block just points back to a row. Building it here, before writing stories, is what surfaces a metric with no event, an event with no key, or a guardrail whose instrumentation drifts to a later release. See `references/examples.md` for a filled table.
- **Scope / non-goals:** what's in, what's explicitly out.
- **Link** back to the PRD as the source of truth.

### 3. Map the journey — backbone before tickets

Before writing tickets, lay out the **backbone**: the user's journey as a left-to-right narrative flow of activities (Patton's story map). This is what stops you from missing steps and from writing a flat, arbitrary list. Stories hang under the activity they belong to.

From the backbone, derive candidate stories by mapping each PRD requirement to the activity it serves. Then mark the **walking skeleton** — the minimum set of stories that gives a usable end-to-end path (this is your first release / MVP slice). If the PRD already cuts releases, keep that grouping; otherwise propose Release 1 (skeleton) → 2 → 3 by functional slices, because shipping sooner means faster feedback and fewer accumulated bugs.

### 4. Check INVEST, and split what's too big

Run every story against **INVEST** (Bill Wake): **I**ndependent, **N**egotiable, **V**aluable, **E**stimable, **S**mall, **T**estable. The two that catch the most problems: *Valuable* (if you can't state the user benefit, it's a task, not a story) and *Small* (if it can't fit in a sprint, split it).

To split, use **SPIDR** (Mike Cohn) — five reliable cuts, always keeping each piece a vertical slice:

- **Spike** — carve off the research/unknown into a time-boxed learning story, leaving the build estimable.
- **Path** — if there are multiple ways through, ship one path first.
- **Interface** — split by platform/surface (web before mobile) or deliver a simple interface, then a rich one.
- **Data** — handle one data subset/type first, expand later.
- **Rules** — defer edge cases and secondary business rules to follow-up stories.

Prefer splitting over a vague "we'll size it later." A story you can't estimate usually hides an unknown — make it a spike.

### 5. Write each story

Use the **Connextra** template, extended with the situation/trigger so the story is grounded (the form the course teaches), plus confirmation:

```
As a <specific persona>, when <situation/trigger>, I want <capability>, so that <benefit/why>.
```

(The plain three-part "As a … I want … so that …" is fine as a short form when there's no meaningful trigger.)

Then attach the layers:

**Acceptance criteria** — choose the lighter of two forms:

- **Gherkin (Given/When/Then)** for behavioral stories — it pins down observable behavior with example data and is BDD/automation-friendly. Keep scenarios to the behaviors that matter; don't pad.
- **Checklist** for simpler stories where full scenarios are overkill.

Either way, criteria must be **observable and verifiable** — borrow the discipline from `intent-driven-development`: ban "works correctly," "fast," "intuitive," "robust," "seamless" unless tied to an observable threshold or marked as a human-review judgment.

**Management rules** — the invisible logic governing this story: limits/counts, accepted formats/sizes and reject behavior, security/compliance, validation. Keep them distinct from AC (AC = visible; rules = invisible). Note any **prohibited side effect** for risk-sensitive stories.

**Edge cases** — enumerate the off-happy-path cases for the story (connection drops, boundary exceeded, bulk/odd input). Route each: if it needs **significant development**, promote it to its own story; otherwise fold it into this story's acceptance criteria or management rules.

**Tracking** — the events the story must fire, with the properties its metric needs to be *computable* (not just named). Trace each event to the epic metric it serves, and include the **key** that metric's formula requires: **identity** (`user_id`) for per-user/repeat/retention metrics; a shared **correlation key** (e.g. `alert_id`) on both events of a two-event rate; the **dimension flag** (e.g. `badge_visible`) on the *outcome* event for a comparison/A-B; a **context key** (e.g. `trip_id`) for a "during X" metric. If the event the metric needs lives in a *different* story, say so — the metric is only instrumented once that story carries the key too. e.g. `photo_uploaded { user_id, format, upload_time }`.

### 6. Optional: tech sub-tasks (the HOW, never a standalone story)

When a story needs an engineering breakdown, list implementation sub-tasks grouped **Frontend / Backend / Infra**. These describe *how to build* what the story requires — not *why* or *what the experience should feel like*. Keep them as Jira **sub-tasks linked to the parent story**, never as separate backlog items, and never as a substitute for the user-facing story. Example for a photo-upload story: FE = upload component + validation + counter logic; BE = upload endpoint + secure storage + draft persistence; Infra = content-moderation scan, tests, analytics wiring.

**Always include an instrumentation sub-task when the story has a Tracking block** — a named event that nobody builds is not instrumentation. The sub-task spells out the event name and the *key* it must carry (e.g. "emit `listing_booked` with `renter_id` + `badge_visible`"), so the analytics work ships with the feature rather than as an afterthought that arrives a release too late.

### 7. Format for Jira and deliver

Produce draft-only output the user can load:

- **Readable draft** (default): epic + stories grouped under the backbone, each with summary, story, AC, management rules, edge cases, tracking, priority, and suggested labels/components. A story-points field left blank (estimation is the team's job, in conversation).
- **CSV for bulk import** when the user wants to load many at once — see `references/jira-import.md` for the exact column format and the epic-link gotcha.

End by surfacing:

- the **requirement traceability check** — every Must-have PRD requirement maps to at least one story;
- the **metric measurability check** — build a small table of *metric → event(s) → owning story*, and for
  each metric confirm (a) every term of its formula has a firing event, (b) those events carry the key the
  formula needs (identity / correlation / dimension / context), and (c) the events ship no later than the
  release where the metric must hold (**guardrail events belong in the walking skeleton**). Name any metric
  whose chain is broken — a missing key or a late-shipping event means it is *not* measurable yet, even if an
  event with the right name exists;
- the **walking-skeleton** subset, the **business-critical** stories needing full regression before release,
  and the **2–3 riskiest open questions** to resolve before pulling these in;
- and **every `[MISSING]` / `[ASSUMPTION]` flag** raised across the stories, gathered into one list so the team resolves the unknowns before pulling the work — never silently filled in to make a ticket look complete.

## Output format (readable draft)

```markdown
# Epic: <outcome-level name>
**Goal:** <the change we want + success metric (3–4 metrics max)>
**Scope:** <in> · **Non-goals:** <out> · **Source PRD:** <link>

## Backbone: <activity 1> → <activity 2> → <activity 3> …

### <Activity>
#### Story: <short title>   [Priority: Must/Should/Could]  [🦴 walking skeleton]  [⚠️ business-critical?]
**As a** <persona>, **when** <situation/trigger>, **I want** <capability>, **so that** <benefit>.

**Acceptance criteria**
- **Given** <context> **When** <action> **Then** <observable outcome>
- **Given** <edge context> **When** <action> **Then** <observable outcome>

**Management rules** (invisible logic the system enforces)
- <limit/count, format/size + reject behavior, security/compliance, validation>
- Must not: <prohibited side effect, if risk-sensitive>

**Edge cases**
- <trigger> → <expected behavior>  (or: promoted to Story <link> if heavy)

**Tracking** (events → epic metric)
- `event_name { property, key }` — <metric it serves> · <key it carries: user_id / correlation id / dimension flag / context id>

**Tech sub-tasks** (optional, the HOW — Jira sub-tasks of this story)
- FE: <…>  · BE: <…>  · Infra: <…>

**Notes / open questions:** <unknowns, dependencies, links to designs>
**Labels:** <area, surface, business-critical?>   **Story points:** _(team to estimate)_
```

## Quality Bar — every story must pass

Modeled on the pass/fail discipline of `intent-driven-development`: any "no" means revise.

- [ ] **Vertical slice.** The story delivers something a user could touch — not a layer ("build the API"), not a horizontal task.
- [ ] **Valuable & specific persona.** "As a …" names a real persona (not "a user"), and "so that …" states a genuine benefit, not a restatement of the action.
- [ ] **Right-sized.** Fits in a sprint. Anything larger is an epic or must be split (SPIDR). Anything trivial may be a sub-task.
- [ ] **Testable, observable AC.** Two people would agree whether each criterion is met. No "correctly/fast/intuitive" without a measure.
- [ ] **Invisible logic captured.** Management rules (limits, formats, security, validation) are stated where they apply, distinct from the visible AC. Risk-sensitive stories name the prohibited side effect.
- [ ] **Edge cases handled.** Off-happy-path cases are enumerated and routed (own story vs. AC vs. management rule), not left to be improvised in code.
- [ ] **Instrumented & measurable.** User-facing stories name the tracking event(s) they fire, each traceable to an epic metric — and each event carries the key that metric's formula needs (identity for repeat/retention, correlation key for two-event rates, dimension flag for comparisons, context key for windowed joins). An event with the right name but no usable key does not count as instrumented.
- [ ] **Guarded from launch.** Any event a guardrail or launch metric depends on is in the walking-skeleton release, not deferred to a later one.
- [ ] **Nothing invented.** Personas, AC thresholds, management-rule limits, metrics, and event names/keys come from the source or are flagged `[MISSING]` / `[ASSUMPTION]` — never guessed into existence. Every flag is surfaced at delivery, not buried in a ticket.
- [ ] **INVEST-clean.** Independent enough to build alone (or dependency noted), negotiable (says what/why, not a rigid how), estimable (no buried unknowns — spike them).
- [ ] **Traceable & in-scope.** Each Must-have requirement maps to a story; no story invents work outside the PRD's non-goals.
- [ ] **Honest unknowns.** Gaps and product decisions are open questions on the story, not silently assumed.

## Anti-patterns to catch

- **Horizontal slicing** — "DB schema," "API," "UI" as separate *stories*. Fix: re-slice vertically (SPIDR Path/Data/Rules) so each ships usable value. (Note: FE/BE/Infra are fine as **sub-tasks** of one story — see step 6 — just never as standalone stories.)
- **"As a user, I want a button"** — no persona, no benefit, describes UI not value. Fix: name the persona, the trigger, and the "so that."
- **AC that restates the title** — "Given the export feature, then it exports." Fix: concrete given/when/then with example data and edge cases.
- **Management rules smuggled into AC** — file limits and permissions buried as if they were visible behavior. Fix: pull them into a distinct management-rules block.
- **Happy-path-only stories** — no edge cases, so error states surface in QA. Fix: enumerate and route them.
- **Stories with no instrumentation** — ships, but nobody can tell if it moved the metric. Fix: name the event(s) and tie them to an epic metric.
- **Event with no usable key** — the story fires `listing_booked` but the epic's repeat-rate metric needs `user_id` it doesn't carry, or a "% of alerts acted on" rate has no shared `alert_id` across the two stories that fire the two events. Fix: add the identity / correlation / dimension / context key the metric's formula requires, even when the two events live in different stories.
- **Guardrail instrumented after its release** — the metric must hold at MVP, but the event that measures it sits in a V2/V3 story (false-green monitoring in V3 while the badge ships in MVP). Fix: pull the guarding event into the walking-skeleton release.
- **Epic-sized "stories"** — multi-sprint, many ACs. Fix: promote to epic, split into slices.
- **Tech tasks dressed as stories** — "Upgrade the library" as a backlog story with no user value. Fix: make it a **sub-task/enabler** of the user-facing story it unblocks (step 6), or tie it to that outcome.
- **Gherkin theater** — ten scenarios for a trivial story. Fix: cover the behaviors that matter; use a checklist for simple cases.
- **"Definition of Done" smuggled into every AC** — repeating "code reviewed, tested, deployed" per story. Fix: keep cross-cutting quality bars in the team's Definition of Done, not in each story's AC.

## Reference files

- `references/examples.md` — a worked example turning a real PRD (Car Health) into an epic, a story-map backbone, exemplar stories with Gherkin AC, management rules, tracking events, and a SPIDR split.
- `references/jira-import.md` — the CSV column format for bulk import, how epic/story/sub-task linking works, and the common gotchas.

## A note on style

The ticket is a token for a conversation, not a substitute for one — so write for shared understanding, then stop. A backlog of small, valuable, testable slices that a team can actually pull beats an exhaustively specified set nobody wants to read. Per `intent-driven-development`, observable beats thorough.
