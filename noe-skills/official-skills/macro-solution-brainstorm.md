---
name: macro-solution-brainstorm
description: Turn a consolidated list of problems or pain points into macro solutions through a structured divergence → convergence brainstorm, and rationalize (cluster and reduce) the list so one solution can cover several problems. Use whenever the user has a problem list and wants to ideate solutions, "reduce the list," find the macro solution for each problem, run a divergence/convergence or design-thinking session, do a post-it brainstorm, or decide which solution direction to bet on — even if they only say "what could we do about these problems," "group these and give me solutions," or "help me converge on what to build." Writes in the user's chosen language (e.g., French sessions in French). Pairs with a prioritization matrix (Impact × Effort) for the scoring step.
---

# Macro-Solution Brainstorm

A problem list is not a plan. This skill takes a set of problems — ideally already consolidated and sourced — and turns it into a short set of **macro solutions**: solution *directions* (bets), not feature specs. It does this in the two phases a real workshop uses, **divergence** (open up, no filtering — the post-it phase) then **convergence** (choose, with explicit criteria), and it rationalizes the list along the way so that one macro solution can resolve several related problems instead of one feature per pain point.

A *macro* solution answers "what is our bet to fix this?" at the level of a direction — e.g. "make vehicle condition objectively verified before booking" — not "add a 5-star photo upload field." Keep it at that altitude; the feature spec comes later.

## When to Use

- The user has a list of problems / pain points and asks "what's the solution for each?"
- "Reduce the list," "group these," "what's the macro solution," "let's brainstorm fixes"
- Running a divergence/convergence, design-thinking, or post-it ideation session
- Deciding which solution *direction* to bet on before writing any spec
- The output of a problem-consolidation or research-recap step needs a next move

If the user wants to score/rank problems on Impact × Effort, that's the prioritization matrix step — this skill feeds it. If they want a build-ready spec, hand off to a PRD/capability skill afterward.

## Intake — Get These Before Brainstorming

Don't generate solutions until you know what they're for. Ask for, or infer and confirm, the following. If the user can't answer, propose a default and flag it.

1. **The problem list.** Ideally consolidated, deduplicated, and tagged with sources/impact. If it's raw, cluster it first (see Workflow step 1).
2. **The goal / north-star.** What metric or outcome should the solutions move (e.g. first-time-user repeat rate, NPS, owner retention)? Solutions are judged against this.
3. **Constraints.** Team size, tech reality, timeframe, two-sided dependencies, budget — the boundaries convergence will respect.
4. **Altitude.** Confirm "macro" = direction/bet, not feature. State an example so the user can correct the level before you generate.
5. **Language.** Run the whole session in the language the team works in; default to the language the user is writing in.

## Workflow

```
1. RATIONALIZE the list first.
   - Cluster problems that share a root cause; separate root causes from symptoms.
   - Reduce N problems to a tighter set of problem clusters (a fixable root usually
     sits under several visible symptoms).
   - Name each cluster by its root cause, list the problems it absorbs.

2. DIVERGENCE — open up, no filtering ("post-it" phase).
   - For each cluster (and any standalone problem), generate 3-6 candidate macro
     solutions. Quantity over quality here; do not judge yet.
   - Force breadth with lenses so you don't get six versions of the same idea:
       • Prevent / Detect / Resolve     (esp. for quality, safety, defects)
       • Product / Process / Policy / Pricing / Partnership   (the 5 Ps)
       • Supply side / Demand side / Marketplace mechanics    (two-sided products)
       • Automate / Verify / Incentivize / Inform
   - Include at least one "cheap/process" option and one "bold/structural" option
     per cluster so convergence has real range to choose from.

3. CONVERGENCE — choose, with explicit criteria.
   - Score each candidate (light-touch) on: Impact on the north-star · Reach (how
     many problems/users it covers) · Confidence (strength of the evidence behind
     it) · Effort. See references/techniques.md for the scoring rubric.
   - Pick ONE macro solution per cluster (occasionally two if genuinely distinct).
   - Strongly prefer solutions that collapse MULTIPLE clusters — that is the whole
     point of rationalizing first.
   - Record why the chosen one won and why the runners-up were dropped (one line each).

4. OUTPUT a divergence board + a convergence table (see Output Format).
   Then offer the prioritization handoff (Impact × Effort scoring).
```

## Macro-Solution Rules

1. **Direction, not feature.** "Verify condition before booking," not "add a photo field." If it names a UI element, it's too low.
2. **Solve root causes, not symptoms.** Aim each solution at the cluster's root, so it drains several symptoms at once.
3. **Favor solutions that collapse the list.** A solution that resolves three clusters beats three solutions that each resolve one.
4. **Stay evidence-anchored.** Every solution should trace to a problem that the data/research actually showed; flag any that rest on assumption.
5. **Respect both sides.** In a two-sided product, check each solution against supply *and* demand — a renter win that hurts owners isn't a win.
6. **Keep divergence judgment-free.** Bad ideas in divergence are fuel; do not prune until convergence.

## Output Format

Produce a markdown file (or Notion page), in the session language, with this spine:

```
# Macro Solutions — [project]

## 0. Goal & constraints
The north-star the solutions must move, plus the binding constraints.

## 1. Rationalized problem clusters
A short table: Cluster (root cause) | Problems it absorbs | Source strength.
Show N problems → fewer clusters.

## 2. Divergence — the board
Per cluster, the 3-6 candidate macro solutions as a flat list (the "post-its").
No scoring here. Tag each with the lens it came from if helpful.

## 3. Convergence — chosen macro solutions
A table: Cluster | Chosen macro solution | Why it wins | Problems/clusters it covers | Runners-up dropped.
Call out any solution that spans multiple clusters.

## 4. Shortlist
The reduced set of distinct macro bets (usually 4-7), ordered by coverage/impact —
this is the list that goes into Impact × Effort prioritization.
```

## A Worked Mini-Example

Problems: dirty cars · undetected mechanical defects · listings don't match reality · disputed cleaning charges.

- **Rationalize:** all four share a root cause → *no objective, independent signal of a car's true condition between rentals.* One cluster, four symptoms.
- **Diverge (post-its):** mandatory periodic inspection (Process) · AI photo diff at check-in/out (Product/Detect) · "Quality Verified" badge from rolling ratings (Product/Inform) · standardized published cleaning-fee schedule (Policy/Pricing) · owner maintenance nudges from telematics (Product/Prevent) · third-party inspection partner (Partnership).
- **Converge:** chosen bet = **"Objective, verified vehicle condition built into the booking flow"** (AI photo diff + Verified badge), because it covers all four symptoms, is high-confidence (every research stream pointed at it), and addresses the root rather than each symptom. Dropped: standalone cleaning-fee schedule (treats a symptom), third-party inspection (effort/cost too high for the reach).

See `references/techniques.md` for the divergence lenses in full, the convergence scoring rubric, clustering heuristics, and facilitation tips.

## Integration

- **Issue Prioritization Matrix (Impact × Effort)** — the natural next step: score the converged shortlist to sequence the bets.
- **Problem consolidation / research recap** — the upstream step that produces the problem list this skill consumes.
- **product-capability / intent-driven-development** — downstream: turn a chosen macro solution into a build-ready spec with acceptance criteria.
- **product-lens** — to pressure-test whether a chosen bet actually addresses the right "why" before committing.
