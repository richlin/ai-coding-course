# Harnesses, Agents, and Models

```text
agent = model + harness
```

The equation is intentionally compact. The model supplies the language and reasoning capability. The harness turns that capability into a working process inside a specific environment.

## The Model Predicts; the Harness Operates

A **model** is a trained neural network represented by a large collection of numerical weights. It receives a sequence of tokens and calculates which token should come next. Repeating that calculation produces an explanation, source code, or a structured request to use a tool. The mechanism is prediction, even when the result looks like planning or reasoning.

Providers package those weights with an inference service that sets limits such as the context window and controls how tokens are sampled. They identify each release with a model name. **Claude Opus 4.6 is a model:** Claude is the model family, Opus identifies the tier, and 4.6 identifies the release. **GPT-5.4 is another model.** Choosing one of these names selects a particular set of learned capabilities and service limits; it does not grant access to your files, terminal, or deployment systems.

A **harness** is the software around the model. It loads instructions and repository context, offers tools, checks permissions, executes approved actions, returns results, and decides when to call the model again. Your team can shape much of this layer in files and configuration you can inspect and review.

An **agent** is the running loop created when the harness repeatedly asks the model what to do, carries out an allowed action, and feeds the result back. The **environment** is where that work happens: a repository, terminal, editor, cloud workspace, or another system. A **tool** is one operation the harness exposes for inspecting or changing that environment, such as reading a file, searching code, applying an edit, or running a test.

The loop looks like this:

```text
request
   ↓
harness assembles instructions and context
   ↓
model proposes a response or tool call
   ↓
harness checks permission and runs the tool
   ↓
environment returns output or an error
   └──────────────→ back into the next model request
```

One visible agent task may therefore contain many model requests. Reading three files, editing one, running a test, seeing a failure, and correcting the edit is not one act performed by the model. It is a sequence coordinated by the harness.

This distinction changes how you diagnose failures. If the model saw the relevant code and constraints but still chose a poor design, a stronger model or more reasoning may help. If the harness never supplied the authentication architecture, could not run the tests, or allowed an unsafe command, changing models leaves the actual defect in place.

## Harness Engineering Makes Fast Changes Governable

AI-assisted development makes two familiar team problems more acute. An ambiguous requirement can become code before the misunderstanding is discovered, and a higher volume of changes makes production risks harder to catch early or trace after a failure.

**Harness engineering** is the work of designing and building the environment that lets coding agents carry out development tasks reliably while keeping their changes reviewable, governable, and reusable. A good harness does not eliminate engineering judgment. It places that judgment where the agent can use it and where the team can inspect or enforce it.

The model is usually supplied to you. The harness is where you encode how work happens in this codebase: which rules apply, what evidence enters context, which actions are available, where a human must approve, and what proves the result is acceptable.

## The Six Harness Components

The six components below form a control loop. Rules define the intended result, context describes the current system, tools make a change possible, reusable assets guide repeated work, permissions bound the consequences, and validation produces evidence for the next decision. A reliable workflow usually needs all six, but each should have a clear responsibility.

### 1. Ground Rules and Specifications

Ground rules describe how the agent should work across tasks. Specifications describe what this task must accomplish. Together they give the model goals, constraints, standards, acceptance criteria, and any required execution order.

For the rate-limiting task, the specification might say: limit failed logins to five attempts per user and IP address within ten minutes, return HTTP `429` when the limit is exceeded, and add no new dependency. A repository-level [`AGENTS.md`](../02-configure-agent-harness/ground-rules.md) might separately require focused tests after any authentication change.

Without those constraints, an implementation can be tidy and still solve the wrong problem. More reasoning cannot recover a requirement that nobody stated.

### 2. Context and Knowledge

Context is the information available to the model for the current request. Knowledge is the useful project or domain information the harness can retrieve and place there. This component determines both what the agent can see now and which state, if any, survives into later work.

For the same task, the harness might supply the authentication architecture, existing Redis helper, neighboring middleware, deployment topology, and the current diff. Stable knowledge belongs in durable repository artifacts when practical; changing evidence such as a test failure belongs in fresh tool output.

More context is not automatically better. Irrelevant logs and stale design notes consume attention and can obscure the one constraint that matters. Supply the smallest body of evidence that lets the model make the next decision correctly.

### 3. Tools and Integrations

Tools let the agent inspect or change its environment. Code search reveals the existing pattern, an editor applies the patch, a test runner checks behavior, and documentation access can settle an API question. An integration connects those operations to another system such as source control, an issue tracker, or CI.

A tool is not merely a capability label. Its arguments, working directory, credentials, output, and failure behavior determine what the agent can actually accomplish. Giving an agent a shell that cannot reach the repository does not make it able to test the code.

### 4. Skills and Reusable Assets

Skills package a repeated procedure, such as reviewing an authentication change or preparing a database migration. Reusable assets give that procedure concrete starting material: test templates, checklists, scripts, examples, or document scaffolds.

For rate limiting, the harness might invoke a security-review skill and reuse an API integration-test template. This saves the agent from reconstructing the team's method from a vague instruction every time. The asset should encode a real recurring workflow; a large catalog of unused skills adds discovery cost without improving the result.

### 5. Permissions and Human Approval

Permissions define which actions the harness may perform. Human approval places a deliberate stopping point before an action whose consequences deserve review.

The rate-limiting agent might be allowed to read and edit the local repository and run focused tests. Adding a dependency, changing shared infrastructure, pushing a branch, or deploying to production might require approval. These boundaries should follow consequence: local, reviewable work can move quickly, while external or difficult-to-reverse changes receive more scrutiny.

Instructions and permissions are not interchangeable. “Do not deploy” asks the model to behave; a denied deployment tool prevents the harness from carrying out the action. [Permissions and Tool Execution](permissions-and-tools.md) develops this distinction in detail.

### 6. Validation and Feedback

Validation checks whether the work meets its specification. Feedback returns that evidence to the agent or team so the next action responds to what actually happened.

Before accepting the rate limiter, the harness can run focused authentication tests, type checks, and CI. After rollout, the team can watch `429` responses and failed-login rates for evidence that the behavior works under real traffic. A failed test should re-enter the loop as concrete feedback, not merely appear in a log nobody examines.

Validation closes the harness loop. Without it, the agent can produce changes but cannot establish that they work or know when to stop.

## Build the Smallest Harness That Closes the Loop

Start with one recurring workflow rather than a broad platform project. Give it enough rules, context, tools, reusable guidance, permissions, and validation to reach a trustworthy stopping point. Then improve the component implicated by real failures.

This approach has two advantages. It keeps ownership visible—a team can say who maintains the authentication test template or deployment approval—and it prevents duplicate instructions from drifting across prompts, skills, and documentation. When a failure or a major environment change exposes a gap, update the harness and test that change on the next comparable task.

Avoid adding memory, tools, or rules without a job for them. Memory needs a decision about what may persist and who corrects it. A tool needs a workflow and permission boundary. A rule needs a place where it applies without contradicting another source.
