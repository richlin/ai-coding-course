# Statelessness

By the end of this article, you will know what an agent forgets between sessions, what it can recover, and how to leave enough durable state for another session to continue the work safely.

Imagine that an agent is adding a file-size limit to an upload form. During the session, it discovers that files can arrive from both the browser and an API client, decides to check the size on the server, edits two files, and runs a focused test. Then the session ends.

A new session does not automatically inherit that working state. It may see the edited files, but it will not know why the check belongs on the server, what the test covered, or whether an unresolved question remains. Unless the first session saved those facts somewhere the next session can read, they are gone.

The useful mental model is simple: **a new session gets artifacts, not history**.

## Where the State Goes

An agent session builds up temporary working state as it reads files, interprets requirements, makes decisions, and observes command output. That state lives in the conversation context. When a new session begins, the harness assembles a new context from the prompt, repository, instructions, tool results, and any other information it chooses to provide.

The model cannot recover an earlier decision merely because it made that decision before. Someone or something must store the decision and place it in the new context.

You can picture the boundary like this:

```text
session A: requirement -> investigation -> decision -> edit -> check
                                      |
                                      v
                         durable project artifacts
                                      |
                                      v
session B: prompt + repository + ticket + handoff -> next decision
```

Built-in memory can carry selected facts across conversations, but it is not a complete project ledger. It may omit a detail, preserve a summary rather than the evidence, or be unavailable to another person or agent. Treat it as a convenience for continuity, not as the only copy of a technical decision.

Statelessness also differs from context degradation. Context degradation happens inside a long-running session when old plans, logs, and obsolete assumptions crowd out the facts that matter. Statelessness appears at the session boundary: the new session starts without the old working context unless durable artifacts reconstruct it.

## Put Each Fact Where It Can Do Its Job

The answer is not to save every conversation. It is to move each important fact into the artifact that should govern future work.

Tests preserve behavior. Code preserves the current implementation. A ticket or task file preserves status, ownership, and acceptance criteria. An architecture decision record preserves a choice whose rationale will matter after the implementation changes. A short handoff connects those artifacts and identifies the next decision.

This separation matters because the artifacts age differently. A handoff that says “the size check lives in `upload.ts`” becomes stale when the code moves. A behavioral test can remain correct. Conversely, a test can show that the server rejects files larger than 10 MB, but it cannot explain why checking only in the browser was rejected. The ticket or decision record carries that rationale.

For the upload task, a useful handoff might say:

```text
Goal: Reject uploads larger than 10 MB with a clear error.
Decision: Check size on the server because API clients bypass the browser form.
The rationale is recorded in the task ticket.
Changed: src/upload.ts, test/upload.test.ts
Checked: npm test -- test/upload.test.ts (8 tests passed)
Open question: Should administrator imports use the same limit?
Next action: Resolve that question before updating the import route.
```

Notice what this handoff does not contain: a diary of every file opened, every failed search, or every draft response. The next agent needs the current state, the evidence behind it, and the next point of uncertainty.

## Exercise: Cross the Session Boundary

1. Pause an active task after making at least one decision and running one verification command.
2. Record the goal, acceptance criteria, decisions, files changed, checks run, open questions, and next action.
3. Link to durable artifacts instead of copying their full contents into the handoff.
4. Start a fresh session with only repository access and the handoff.
5. Ask the new agent to summarize the current state and propose the next command before editing.
6. Compare its answer with the actual state. Add only the missing information that caused a wrong or blocked decision.

The exercise is complete when a fresh agent can reconstruct the current state and choose the next useful action without access to the original conversation. The durable facts should live in team-visible artifacts, not only in the handoff or an agent's private memory.

Use this **rule of thumb**: before ending a session, ask what the next agent could infer incorrectly from the repository alone. Preserve the facts that would change its next decision, put each one in the artifact that should own it, and leave the handoff as a map.
