# Feature implementation plans

Create a short `NNN-topic.md` plan for cross-module, long-running, or high-risk work. Name the related GitHub Issue, list scope/non-goals, exact files or modules, implementation steps, acceptance tests, and rollback/uncertain-command behavior.

Update the plan when an architectural decision changes; create an ADR for durable cross-cutting decisions. Do **not** store session-specific progress in plans. Use local, gitignored `.agents/checkpoint.md` for one active task, deleting it when completed.
