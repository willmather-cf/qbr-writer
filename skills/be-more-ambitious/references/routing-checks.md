# Routing checks

Use these to test that the skill triggers on the right requests after any
change.

Should trigger:
- "Here's my prompt for the weekly report. Make it more ambitious."
- "I keep asking the model to fix one bug at a time. Am I thinking too small?"
- "What would a top data scientist do with this churn question that I'm not asking for?"
- "Level up this campaign brief before I hand it to an agent."

Should not trigger:
- "Make this landing page beat our competitor's homepage." The work needs doing against a named reference; this skill only rewrites the ask.
- "Why does this test keep failing?" Systematic debugging fits.
- "Write the Q3 campaign brief." That is the work itself, not an ask to upgrade.
