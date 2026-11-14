---
name: postmortem-format
description: The standard structure and writing rules for a blameless incident postmortem. Use when writing, reviewing, or tidying an RCA, postmortem, or incident report, or when the user asks what a good postmortem should contain.
---

# Postmortem format

A postmortem answers four questions: what happened, how bad was it, why did it happen, and what changes. Write it for a reader who was not on the call.

## Structure

Use these sections, in this order. Drop a section only when it truly does not apply.

```markdown
# Postmortem: <short incident name>

**Date:** <date> | **Duration:** <total> | **Severity:** <level> | **Status:** <draft or final>

## Summary
Three or four sentences: what broke, who was affected, how long, and the root cause.

## Impact
- Users or customers affected, with numbers
- What they could not do
- Time to detect, time to mitigate, total duration
- Data loss, SLA or SLO breach, if any

## Timeline
Table of events in one timezone, each with its source.

## Root cause
The trigger, the root cause, and the contributing factors, each marked confirmed or suspected.

## 5 whys
1. Why did users see <symptom>? Because ...
2. Why ...? Because ...
(continue until the answer is a process, design, or guardrail gap)

## What went well
## What went poorly
## Where we got lucky

## Action items
| Action | Type | Owner | Priority | Done when |
|---|---|---|---|---|

## Open questions
What the evidence does not explain, and what data would answer it.
```

## Writing rules

- **Blameless.** Systems and processes cause incidents. Use roles ("the on-call engineer"), never names. "The deploy pipeline allowed an untested config" beats "X pushed a bad config".
- **Evidence only.** Every time, number, and cause traces to a source. Mark anything else as suspected.
- **Plain words.** Short sentences. Explain internal names the first time they appear.
- **Numbers over adjectives.** "38% of checkout requests failed for 21 minutes", not "a major outage".

## Action item rules

- Type is one of **prevent** (stop it recurring), **detect** (catch it sooner), or **mitigate** (recover faster). A good postmortem has at least one of each when the evidence supports it.
- Each item is one concrete change with an owner role, a priority (P0, P1, P2), and a "done when" test.
- "Be more careful" and "improve monitoring" are not action items. Say which alert, on which signal, at which threshold.
- Five strong items beat fifteen weak ones.
