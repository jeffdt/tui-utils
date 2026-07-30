---
description: Stop asking for approval and drive the current work to a merged PR, unattended
---

Your human partner just invoked `/ship-it`. Treat this as a standing instruction for the remainder of this task: they are about to walk away and expect to come back to a finished, shipped result, not a queue of questions.

From this point on, for the work currently in flight (whatever spec, plan, or implementation is active in this conversation):

1. **Do not stop for approval between stages -- but still do every stage.** If a spec doesn't exist yet, still write one (via `brainstorming`); if a plan doesn't exist yet, still write one (via `writing-plans`). What changes is only the handoff: normally each of these pauses and waits for sign-off before moving to the next. Under `/ship-it`, finish the current stage, note briefly that you're proceeding without waiting, and flow straight into the next one -- spec finishes into plan, plan finishes into implementation. Skip a stage entirely only when the task is genuinely trivial (a one-line fix), same bar as today.

2. **Always use subagent-driven development.** When executing a plan, use `superpowers:subagent-driven-development` (fresh implementer subagent per task, task review after each, broad review at the end) rather than asking whether to use subagents or doing the work inline. This is the standing default, not a one-time choice.

3. **Always ship via PR, never a local merge.** When you reach the point `finishing-a-development-branch` would normally present the "merge locally / push and create a PR / keep as-is" menu, skip the menu and take the PR path: push the branch and open a pull request. Never merge to `main` locally and never leave it "as-is" waiting for a decision. Report the PR URL when done.

4. **Say it once, then go quiet.** Acknowledge that you're proceeding hands-off and that they'll get a PR link at the end -- then don't ask again. Status updates are fine; requests for permission are not.

**What this does NOT override:**

- Still run tests and verification before claiming anything works (`superpowers:verification-before-completion`). A red suite still stops you.
- Still stop for genuine blockers: ambiguity that actually prevents progress, a decision only they can make (irreversible/destructive actions, credentials, business tradeoffs), or being stuck after real debugging effort.
- Never skip pre-commit hooks, force-push, or otherwise bypass safety rails to push through a blocker -- fix the underlying issue or stop and report it.
- Branch naming, commit, and PR conventions from CLAUDE.md still apply as normal.

If nothing is currently in flight (no active spec/plan/branch), tell them `/ship-it` has nothing to attach to yet and ask what to build -- then apply all of the above to it once they answer.
