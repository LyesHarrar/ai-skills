---
name: interview-script-review
description: Audit and optimize user-research interview scripts and discovery guides — critique the questions, flag what's leading, hypothetical, double-barreled, or off-goal, then rewrite them into clean, behavior-first versions. Use whenever the user shares an interview guide, discovery script, question list, or moderation guide and wants it reviewed, tightened, de-biased, or improved — even if they only say "look over my questions," "is this script good," "make these less leading," or "improve my user interview." Works in the script's own language (e.g., keep French scripts in French). Pair with user-research for end-to-end study design.
---

# Interview Script Review

A good interview reduces the risk of building the wrong thing. A bad script quietly manufactures the answer the team already wanted — through leading questions, hypotheticals, and prompts that flatter the product. This skill exists to catch that before the interviews happen, when fixing it is still cheap.

The job is two things, in order: **critique** the script honestly against the rubric below, then **rewrite** the weak questions into clean versions. Don't stop at a list of problems — show the better question.

## When to Use

- The user shares an interview guide, discovery script, question list, or moderation guide and wants feedback
- A script needs to be de-biased: "these feel leading," "am I steering people," "make this neutral"
- Questions need tightening before fieldwork starts
- Someone wants past-behavior questions instead of hypothetical ones
- A script is being adapted for a new segment (e.g., churned vs. active users) and needs a pass

If the user instead needs to design a study from scratch, plan a screener, or synthesize results, that's the broader **user-research** skill — this one is specifically the script-review lane.

## Core Principles

These are the lens for every critique. The detailed rubric and worked rewrite examples live in `references/rubric.md` — read it before reviewing a substantial script.

1. **Past behavior over hypotheticals.** "Tell me about the last time you rented a car" beats "would you rent a car?" People are poor predictors of their own future behavior but reliable narrators of what they actually did. Hypothetical and "would you" questions are the most common defect — flag every one.
2. **Non-leading and unprimed.** A question must not telegraph the answer it wants. "What frustrated you about the pickup?" presumes frustration; "Walk me through the pickup — how did it go?" doesn't. Strip embedded assumptions, loaded adjectives, and product-flattering framing.
3. **One idea per question.** Double-barreled questions ("How did you find the price and the driving experience?") force the respondent to pick one and bury the other. Split them.
4. **Open, not closed.** Yes/no and multiple-choice phrasings end stories. Reserve them for facts (how many times, do you own a car); use open prompts for everything experiential.
5. **Grounded in a real moment.** The strongest questions anchor to a specific episode ("the first/last time…") rather than a general habit ("usually, how…"). Specificity surfaces detail; generality surfaces rationalization.
6. **Every question earns its place.** Each question should map to a learning goal. If you can't say what decision an answer informs, cut it or mark it.
7. **Logical arc and good probes.** Warm-up → past-behavior stories → problem exploration → wrap-up. Branching probes (the indented follow-ups) should deepen, not repeat. Note where a probe is missing at a high-signal moment.

## Workflow

```
1. Read the whole script once before judging anything — get the intent and the arc.
2. Identify (or ask for) the learning goals. If none are stated, infer them from the
   sections and note that you inferred them — a script can't be judged against goals
   it doesn't declare.
3. Go question by question. For each, assign a status:
   - KEEP        — already strong, leave it
   - TIGHTEN     — mostly fine, small fix (wording, split, add a probe)
   - REWRITE     — leading / hypothetical / closed / off-goal; replace it
   - CUT / MERGE — redundant or doesn't serve a goal
   Tag the specific defect (leading, hypothetical, double-barreled, closed,
   ungrounded, unmapped) so the user learns the pattern, not just the fix.
4. Check the script as a whole: does the arc flow? Are sensitive questions late?
   Are there gaps where a learning goal has no question? Is sequencing priming
   later answers?
5. Produce the rewritten script in the SAME LANGUAGE as the input, preserving the
   user's structure and numbering so they can diff old vs. new.
6. End with a short "what changed and why" so the rewrite is a teaching tool, not a
   black box.
```

**Language:** Always review and rewrite in the language the script is written in. A French script gets French rewrites; keep idiom natural (e.g., "Racontez-moi la dernière fois où…"), don't translate to English and back.

## Output Format

Produce a markdown file, `SCRIPT-REVIEW.md`, with this spine:

```
# Interview Script Review — [script name]

## Summary
2-4 lines: overall verdict, the single most common defect, and the biggest win available. Plain language.

## Scorecard
A short table or list rating the script on the seven principles (e.g., strong / mixed / weak), so the user sees the shape of the problem at a glance.

## Question-by-question
For each original question:
> original question (quoted)
- **Status:** KEEP / TIGHTEN / REWRITE / CUT
- **Defect:** (if any) leading | hypothetical | double-barreled | closed | ungrounded | unmapped
- **Rewrite:** the improved question, in the original language
- **Why:** one line

## Structural notes
Arc, sequencing, priming risks, missing probes, gaps vs. learning goals.

## Optimized script
The full rewritten guide, in the original language, ready to use — same sections and numbering as the original so it diffs cleanly.
```

Keep observation (what the question does) separate from recommendation (the rewrite). The user should be able to disagree with a specific rewrite without losing the diagnosis.

## A Worked Mini-Example

Drawn from a real discovery guide (the structure these reviews typically see):

**Original:** "Qu'avez-vous pensé de l'expérience de conduite ? Quels étaient les points positifs et/ou négatifs ?"
- **Status:** TIGHTEN
- **Defect:** double-barreled + mildly leading (pre-sorts into positive/negative)
- **Rewrite:** "Racontez-moi le trajet lui-même, du moment où vous avez démarré. Qu'est-ce qui s'est passé ?" — then probe neutrally: "Y a-t-il eu un moment qui vous a marqué ?"
- **Why:** Let the driver narrate the episode before you hand them evaluative buckets; the buckets bias which memories surface.

**Original:** "Pourquoi avoir finalement choisi Getaround ?"
- **Status:** KEEP (with a probe)
- **Defect:** none — anchored to a real decision
- **Add probe:** "Qu'avez-vous failli choisir à la place, et qu'est-ce qui a fait pencher la balance ?" to surface the real alternatives and the deciding factor.

See `references/rubric.md` for the full defect catalog, scoring rubric, and a dozen more before/after rewrites in both English and French.

## Integration

- **user-research** — for the surrounding study: learning goals, screener, synthesis of the resulting interviews. This skill assumes those exist or infers them.
- **product-lens** — to pressure-test whether the question behind the script is the right one to be asking.
