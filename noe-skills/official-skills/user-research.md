---
name: user-research
description: Plan, run, and synthesize user research for product work — discovery interviews, surveys, usability tests, and mining feedback from review platforms. Use whenever the user wants to talk to users, write an interview guide or screener, design a survey, run or analyze a usability test, turn raw interview notes or transcripts into insights, build personas or JTBD statements, or scrape and analyze customer feedback from places like the App Store, G2, Reddit, or support tickets. Trigger even when the user doesn't say "research" — phrases like "I need to understand why users churn," "help me figure out what customers actually want," "make sense of these interview notes," or "what are people saying about our product" all belong here.
---

# User Research for Product Managers

Research exists to reduce the risk of building the wrong thing. The job is not to produce a tidy report — it is to change a decision. Every artifact this skill produces should end with a "so what": what we now believe, how confident we are, and what we'd do differently because of it.

Two failure modes to actively avoid:

- **Research theater** — interviews and surveys that confirm what the team already wanted to do. Guard against it by writing questions that can produce a "no," and by separating what users *said* from what they *did*.
- **Insight laundering** — dressing up an opinion as a finding. Keep observation, interpretation, and recommendation visibly distinct so the reader can check your reasoning.

## When to Use

- Before committing to a feature — to validate the problem is real and worth solving
- When the team disagrees about what users want and needs evidence to break the tie
- Turning a pile of interview notes, call transcripts, or survey responses into something decision-grade
- Designing a survey and worrying the questions are leading or unanswerable
- Planning or debriefing a usability test on a prototype or live flow
- Understanding sentiment at scale — what reviews, forums, and support tickets reveal about real pain

## Operating Principles

These hold across every mode:

1. **Start from the decision, not the method.** Ask "what will we do differently depending on the answer?" If nothing, don't run the study.
2. **Separate behavior from opinion.** What people do predicts the future better than what they say they'll do. Probe past behavior ("tell me about the last time…") over hypotheticals ("would you use…").
3. **Make claims falsifiable.** A good finding could have come out the other way. Note sample size and how confident the evidence makes you.
4. **Quote the user.** Verbatim language is the most valuable raw material — for insights, for specs, and for marketing copy later. Preserve it.
5. **Separate fact, inference, and recommendation.** The reader should always be able to tell which is which.

## Modes

### Mode 1: Discovery & Interviews

For understanding the problem space — why users behave as they do, what jobs they're hiring the product for.

```
1. Define the decision and the learning goals (3-5 questions you must answer)
2. Define who to talk to and write a screener to find them (and screen out bad fits)
3. Write a discovery guide:
   - warm-up → past-behavior stories → problem exploration → wrap-up
   - open, non-leading questions; one idea per question
   - "tell me about the last time…" over "would you ever…"
4. Note where to probe deeper ("why was that frustrating?") vs. move on
5. Plan logistics: number of interviews, recording/consent, note-taking method
```

Output: an `INTERVIEW-PLAN.md` with learning goals, screener, the guide, and a note-taking template that captures verbatim quotes.

### Mode 2: Synthesis & Insights

For turning raw research data (notes, transcripts, open-ended survey text) into insights, themes, personas, or JTBD statements.

```
1. Read everything once before coding anything — get the gestalt
2. Tag observations by theme (affinity mapping); keep the user's words attached
3. Promote recurring patterns to themes; note how many sources support each (e.g., "5 of 8")
4. For each theme: the observation, your interpretation, the supporting quotes, the confidence
5. Where useful, distill into:
   - JTBD: "When [situation], I want to [motivation], so I can [outcome]"
   - Personas grounded in observed behavior, not demographics-for-their-own-sake
6. End with implications: what this means for the roadmap, ranked by impact
```

Output: an `INSIGHTS.md` structured as themes → evidence → implications, with a short executive summary up top and verbatim quotes preserved throughout. Resist inventing patterns that aren't in the data; "we didn't learn enough about X" is a legitimate finding.

### Mode 3: Surveys & Quant

For measuring how widespread something is, once qualitative work has surfaced what to measure.

```
1. State the hypothesis the survey will test before writing any question
2. For each question, check: is it answerable, unambiguous, and non-leading?
   - avoid double-barreled questions, loaded wording, and unbalanced scales
   - prefer behavioral/frequency questions over attitudinal where possible
3. Choose scales deliberately (e.g., 5-pt Likert, NPS) and keep them consistent
4. Sequence: easy/engaging first, sensitive/demographic last
5. Note the realistic sample needed for the confidence you want, and flag when results would be directional only
6. For analysis: report distributions not just averages, segment where it matters, flag low-n cuts
```

Output: a `SURVEY.md` with the hypothesis, full question list with answer options and rationale, and an analysis plan. When given results, produce a findings summary that reports distributions, segments, and explicit caveats about confidence.

### Mode 4: Usability Testing

For evaluating whether people can actually use a flow, prototype, or feature.

```
1. Define realistic tasks tied to real goals ("buy a gift for a friend"), not UI instructions ("click checkout")
2. Write a script: intro, think-aloud prompt, tasks, post-task questions
3. Keep the facilitator neutral — no leading, no rescuing; silence is data
4. Capture per task: completion (yes/no/assisted), time, errors, quotes, observed friction
5. Rate each issue by severity (blocker / major / minor / cosmetic) and frequency
6. Report top issues with evidence and a specific recommended fix for each
```

Output: a `USABILITY-TEST.md` (script + task list before; findings report after) with a severity-ranked issue list, each issue tied to evidence and a concrete fix.

### Mode 5: Feedback Mining from Trusted Platforms

For understanding sentiment and pain at scale from feedback users have already left publicly or in support channels — app store reviews, G2/Capterra, Reddit and community forums, support tickets, social mentions.

```
1. Confirm sources and scope with the user (which platforms, time window, product/competitor)
2. Gather feedback:
   - prefer official/legitimate access: APIs, exports, or built-in tools (e.g., support-desk exports, app-store review APIs, a connected MCP)
   - respect each platform's terms of service; do not bypass access controls or scrape gated content
   - if a source can't be accessed legitimately, say so and propose an alternative
3. Categorize by theme and sentiment; track volume and trend over time
4. Separate signal from noise: weight by recency, frequency, and whether it ties to a real job-to-be-done
5. Watch for bias — reviewers skew toward extremes; support tickets skew toward problems
6. Surface: top pain points, most-requested improvements, emerging issues, and notable verbatim quotes
```

Output: a `FEEDBACK-ANALYSIS.md` with themes ranked by volume and severity, sentiment trend, representative quotes (with source), and prioritized implications. Always note the bias of the source so the reader doesn't over-read it.

> Access note: when a task needs data from a platform with no legitimate programmatic access, check whether a relevant MCP connector is available before anything else, and fall back to asking the user to export the data. Never circumvent paywalls, logins, or terms of service to obtain feedback.

## Output Standards

Every deliverable is a markdown file and follows this spine so it stays decision-oriented:

```
# [Title]
## Executive summary        (what we now believe + the recommendation, in a few lines)
## [Body — varies by mode]  (plan, or themes→evidence→implications, etc.)
## Confidence & caveats     (sample size, biases, what we still don't know)
## Recommendation / next step
```

Keep quotes verbatim and attributed. Keep observation, interpretation, and recommendation visibly separate. A reader should finish knowing what to do next.

## Integration

Pair with:

- `product-lens` — to pressure-test the "why" before research, and to act on findings after
- `product-capability` / `intent-driven-development` — to turn validated needs into specs
- `market-research` — for the market/competitor context around user needs
- `competitive-platform-analysis` — when feedback mining extends to competitors
