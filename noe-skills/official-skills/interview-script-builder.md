---
name: interview-script-builder
description: Build a user-research interview script or discovery guide from scratch — turn a decision, a set of learning goals, and a target segment into a clean, behavior-first guide with a warm-up, past-behavior stories, problem exploration, branching probes, and a wrap-up. Use whenever the user wants to write, create, draft, or design an interview guide, discovery script, moderation guide, or question list — even if they only say "I need questions for user interviews," "help me write a discovery guide," "what should I ask churned users," or "make me an interview script for X." Writes in the user's chosen language (e.g., French scripts in French). Hands off to interview-script-review to audit the draft.
---

# Interview Script Builder

A discovery interview is only as good as the questions going in. This skill turns intent — a decision to inform, things to learn, a kind of person to talk to — into a ready-to-run guide that already obeys the rules a reviewer would otherwise have to enforce: past behavior over hypotheticals, non-leading, one idea per question, anchored to real moments.

This is the **create** half of a two-skill pair. Its companion, **interview-script-review**, audits and rewrites an existing script. Build with this one, then path straight into the reviewer for a second pass — they share the same principles, so a script built here should score well there.

## When to Use

- The user needs an interview guide and doesn't have one yet
- "What should I ask [segment]?" — churned users, power users, non-adopters, a new persona
- A guide is needed for a specific decision ("should we build X," "why are people leaving")
- Adapting an existing study's intent into a fresh script for a new segment or market

If the user already has a draft and wants it critiqued or tightened, that's **interview-script-review**, not this skill.

## Intake — Get These Before Writing

Don't write questions until you know what they're for. Ask for, or infer and confirm, the following. If the user can't answer, propose a default and flag it.

1. **The decision.** What will the team do differently depending on what's learned? A guide with no decision behind it produces research theater.
2. **Learning goals** — 3 to 5 questions you must be able to answer afterward. These become the spine; every interview question maps to one.
3. **Segment** — who exactly to talk to (e.g., "people who rented once on Getaround and never came back"). This shapes branching and recruiting.
4. **Context** — product/market, what's already known, any prior research to avoid re-asking.
5. **Constraints** — session length (drives question count), language, in-person vs. remote.
6. **Language** — write the entire guide in the language the interviews will be conducted in. Default to the language the user is writing in; for a French study, produce a French guide with natural idiom.

State back the decision + learning goals before drafting so the user can correct the target before you build to it.

## Workflow

```
1. Lock the decision and 3-5 learning goals. Write them at the top of the output —
   they are the contract the script is judged against.
2. (If recruiting matters) draft a short screener: 2-4 questions that confirm the
   person is in-segment and screen out bad fits.
3. Build the arc, section by section:
   - Warm-up / context      → who they are, low-stakes, builds rapport
   - Grounding behavior     → "the last/first time you…", the real episode
   - The experience         → walk-through of what actually happened, neutrally
   - What happened after    → repeat use, switching, churn — with branches
   - Wrap-up                → anything missed, magic-wand, thanks
4. For each section, write questions that map to a learning goal. Use open,
   non-leading, single-idea, episode-anchored phrasing (see references/templates.md
   for the section-by-section template and a reusable question bank).
5. Add branching probes where the path forks ("[if they churned]…", "[if they
   tried again]…") and label them so the interviewer knows which to take live.
6. Mark where to probe ("why was that?") vs. move on, and where to stay silent.
7. Map-check: every learning goal has ≥1 question; every question serves a goal.
   Note and fix orphans on both sides.
8. Output the guide in the chosen language, then offer the review handoff.
```

## Question-Writing Rules

Build the script right the first time so the reviewer finds little to fix:

1. **Past behavior, not hypotheticals.** "Tell me about the last time you rented a car," never "would you rent a car?"
2. **Non-leading.** No embedded verdicts or product flattery. "Walk me through the pickup — how did it go?" not "what frustrated you about the pickup?"
3. **One idea per question.** Never join two asks with "and/or."
4. **Open for stories, closed only for facts.** Yes/no is fine for "do you own a car?"; never for an experience.
5. **Anchor to a moment.** "The first/last/most recent time…" beats "usually."
6. **Problem before solution.** Establish the need exists before testing any feature reaction.
7. **Each question earns its place** by mapping to a learning goal.

These mirror the rubric in **interview-script-review** exactly — that's intentional, so the two skills agree.

## Output Format

Produce a markdown file, `INTERVIEW-GUIDE.md`, in the interview language, with this spine:

```
# Interview Guide — [study name]

## Decision & learning goals
The decision this informs, then the 3-5 learning goals (numbered — questions reference these).

## Screener            (if recruiting)
2-4 in/out questions.

## Guide
### 1. Warm-up
### 2. Grounding behavior
### 3. The experience
### 4. What happened after   (with [branch] labels)
### 5. Wrap-up
Each question on its own line; indented sub-bullets for probes; [branch] tags where the path forks; → goal tags (e.g. "→ G2") if the user wants the mapping shown.

## Logistics
Suggested number of interviews, session length, recording/consent reminder, note-taking note (capture verbatim quotes).
```

Keep the tone conversational — these are spoken aloud, so they should read like something a human would actually say, not a survey.

## A Worked Mini-Example (French study)

Decision: should we invest in surfacing vehicle condition before booking? Goal G2: understand how renters currently judge a car's condition before they book.

- Grounding: « Racontez-moi la dernière fois que vous avez réservé une voiture sur Getaround. C'était pour quoi ? »
- Experience: « Décrivez-moi la réservation puis la récupération, étape par étape. » → probe: « Y a-t-il eu un moment qui vous a surpris ? »
- After (branch): « [s'il/elle n'a pas reloué] À quel moment avez-vous décidé de ne pas reprendre de voiture sur Getaround ? »

See `references/templates.md` for the full section template, a learning-goal→question map, a bilingual question bank, and a screener template.

## Handoff to Review

After producing the guide, offer: *"Want me to run this through the interview-script-review skill for a critique pass?"* If yes (or if the review skill is available and the user wants a quality check), pass the draft to **interview-script-review**, which will tag each question and return an optimized version. Because both skills share the same principles, the review is a confirmation/polish step, not a rebuild.

## Integration

- **interview-script-review** — the companion critique+rewrite skill; the natural next step after building.
- **user-research** — for the wider study: synthesis of the interviews, surveys, usability tests, feedback mining.
- **product-lens** — to pressure-test whether the decision behind the script is the right one before you invest in fieldwork.
