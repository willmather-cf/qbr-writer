---
name: be-more-ambitious
description: Rewrite a task, prompt, or recurring chore into a deeper, higher-reaching version that a model can still finish and an outside check can still verify, before any work starts.
owner: Will Mather
group: Generic
context:
  - voice/writing-guidelines.md
---

# Be More Ambitious

Turn a small ask into an ambitious one that a model can still finish and an
outside check can still verify. Hand it a prompt or a repeating task that
feels small for what a model can do. It runs the ask through three lenses
(Altitude, Depth, and Range), checks what access actually exists, names an
outside judge, and hands back one upgraded ask you can paste straight into an
agent, plus a list of what was cut and why. The goal is a deeper version of
the ask, not a bigger one: more scope with the same method is not ambition.
Method credit: Felix Rieseberg, "How to be more ambitious: A tutorial for
humans with models". This skill is an interpretation of the essay, not its
text.

## When To Use

Use this before work starts, when an ask or a recurring chore feels small
for what a model can do.

Trigger phrases:

- "Be more ambitious with this."
- "Aim higher."
- "Am I thinking too small?"
- "Level this up."
- "What would a top expert do here?"
- "10x this ask."

Or the operator runs `/be-more-ambitious`.

This skill upgrades the ask. It does not do the work. Do not use it to debug
a specific failure ("why does this test keep failing?") or to beat a named
reference ("make this page beat a competitor's homepage"); those need the
work done, not the ask rewritten. Creative, taste-led work (brand voice, art,
copywriting) gains less from Altitude; lean on Depth and Range and keep a
human as the judge.

## Inputs

Collect conversationally. If the operator pastes the ask with the request,
start immediately.

- Required:
  - The ask itself: the prompt, task, or recurring chore, verbatim.
- Optional:
  - What happens after the task is done, if the operator knows. This seeds
    Altitude. Without it, infer and confirm.
  - What data, tools, and systems the work can touch. Without it, check what
    is connected in the workspace and ask about the rest.
  - Whether the task is a one-off. A true one-off keeps rung 0; say so
    instead of inflating it.

Never assume access. Anything that cannot be confirmed with a tool is marked
`unknown - ask user`.

## Context

- `voice/writing-guidelines.md` sets the house voice for the upgraded ask and
  the ambition read: plain words, short sentences that carry the point, and a
  hard specific in place of a superlative. Apply it to every line written
  back to the operator.

The method detail and a full before-and-after live in
`references/worked-example.md`, bundled with this skill. Read it before the
first run, or when the operator asks for an example.

## Workflow

Run the steps in order. Write each answer down; do not keep it in your head.

1. **State check: what access exists now.** List what the model can actually
   touch today: raw data, logs, tools, connected systems, a place to run
   scheduled jobs, test devices. Mark each item `present`, `missing`, or
   `unknown - ask user`. Check the workspace's connected resources where you
   can; anything you cannot confirm is `unknown - ask user`.
2. **Altitude: climb from task to outcome.** Ask "and then what?" two or
   three times. Each answer is a rung.
   - Rung 0: the task as asked.
   - Rung 1: the outcome the task serves.
   - Rung 2: a standing system that keeps producing that outcome with fewer
     human touches.

   For each rung, write the access it needs from the step 1 list. Pick the
   highest rung that an outside check can still confirm and whose access is
   present or can be granted. If a rung's access is missing, the first
   deliverable is "grant this access", not the ambitious task. Stop climbing
   when no outside check could confirm the goal ("grow the business" fails).
   Signals a task wants altitude: it recurs, it lives in a recurring
   meeting, or someone re-prompts the same fix each week.
3. **Depth: work like the top expert.** Answer four questions before
   rewriting anything:
   1. What would a top professional do here that the ask never mentions?
   2. What is the rawest material they would start from (logs, event tables,
      source files, not a summary)?
   3. Which instruments and methods would they use (stats models, profilers,
      simulations, SQL)?
   4. What independent evidence would prove the result?

   Then set a hard, specific target that sounds a bit unreasonable (200 ms,
   not "faster"). Name the assumption the task rests on and ask for it to be
   tested against raw data. Where it fits, ask for new knowledge: a
   simulation, a leading signal, or a model validated on held-out data.
4. **Range: borrow other fields.** Restate the deliverable as the job it does
   (a "deck" is really a way to make a causal story credible to busy people
   and get a decision fast). Pick a crew of two to four roles from that verb.
   Add one adversary (a short seller, a forensic accountant, a hostile
   reviewer) when the result moves money, touches a production system, or
   makes a public claim. Each role does the work and produces an artifact;
   "research the short case and list the evidence" is right, "write like a
   short seller" is role-play.
5. **Outside judge.** Name the check that runs outside the model that did the
   work: a test suite, a held-out dataset, a benchmark script, a
   fresh-context reviewer, a real user metric. The model never grades its own
   output. Prefer a check the model can run itself for fast feedback.
6. **Write the upgraded ask.** Use the layout in Output exactly. Keep the
   upgraded ask as one block that covers outcome, raw inputs, hard target,
   methods, crew tasks, judge, and stop condition. Access to be granted comes
   first.
7. **Verify the rewrite, then fix and re-check.** Run the Quality Bar as a
   pass/fail list. Fix any failure and check again. Then write the artifact.

## Output

One Markdown artifact saved to the shared outputs folder as
`be-more-ambitious-<topic>.md`, where `<topic>` is a short slug for the ask.
It holds four sections, in order:

1. **Original ask.** Verbatim.
2. **Ambition read.**
   - Altitude: rung 0 to rung N, one line per rung.
   - Depth: expert delta; raw material; instruments; evidence.
   - Range: verb rewrite; crew roles and what each produces.
   - Outside judge: the check, and who or what runs it.
   - Access: each item marked present, missing, or unknown - ask user.
3. **Upgraded ask (paste this).** One block, ready to paste into an agent.
4. **What I cut and why.** Rungs or ideas dropped because no outside check
   could confirm them or the access was missing.

Also show the upgraded ask in the chat reply so the operator can copy it
straight away.

## Quality Bar

- The chosen rung is named and has an outside check. A true one-off keeps
  rung 0.
- Every rung's access is listed as present, missing, or unknown. Nothing
  unknown is treated as present. Missing access is the first deliverable.
- The target is a specific number or a pass/fail condition, not "better".
- The method changed, not just the vocabulary. A rewrite that only adds
  expert-sounding words fails; redo Depth question 3 until the instruments
  change.
- Crew roles each produce an artifact. No "act as a world-class X" personas.
- An outside judge exists and is not the model that did the work.
- Scope is something a model can finish. If the goal is so high nothing can
  check it, drop a rung and say so.
- Deeper, not bigger. If the scope grew but the method stayed the same, go
  back to Depth.
- The upgraded ask is one pasteable block with a stop condition.

## References

| File | Purpose |
|------|---------|
| `references/worked-example.md` | A full run on a weekly ads report, upgraded to a standing ad-health system: working notes for every step, then the final answer in the exact output layout. Numbers are illustrative. |
| `references/routing-checks.md` | Requests that should and should not trigger this skill, for testing after any change. |
