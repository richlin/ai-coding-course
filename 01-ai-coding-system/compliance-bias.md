# Compliance Bias

By the end of this lesson, you will be able to spot when a coding agent is agreeing instead of evaluating, and structure a request so the agent can question your proposed solution before it writes code.

Suppose you say, “Make the Save button red so people can find it.” The agent can change the color, update the tests, and complete the request exactly as written. But if the application's design system uses red for destructive actions, the new Save button may look like a warning. The code is correct; the decision is not.

The outcome you need is “help people find the Save button.” Making it red is only one proposed way to get there. A coding agent shows compliance bias when it accepts the proposal as a requirement instead of checking whether the proposal serves the outcome.

You can see the same pattern when an agent says “**You are absolutely right**,” makes a change, then says the same thing when asked to reverse it. The phrase itself is harmless. The problem is that agreement has taken the place of evaluation. Research usually calls this behavior *sycophancy*; here, we focus on how it appears during engineering work.

## Agreement Is Not Evaluation

Implementation and evaluation are different jobs. If you say, “Make the Save button red,” the decision appears to be settled; the remaining job is to change the code safely. If you say, “People cannot find the Save button; investigate why and recommend a change,” the implementation remains open. The agent now has a decision to evaluate before it has code to write.

For the same underlying problem, the task you set changes what the agent is able to question:

| Question | Implementation task | Evaluation task |
| --- | --- | --- |
| What is already decided? | The button will be red. | Only the outcome: people must be able to find Save. |
| What gets investigated? | How to apply the color without breaking the code. | Why the button is missed and how primary actions are styled. |
| What can the reasoning change? | Implementation details. | The proposed color, position, label, spacing, or original diagnosis. |
| What counts as success? | The requested change works without a regression. | The chosen change addresses the problem without breaking interface conventions. |

An implementation task is appropriate when the team has already made and reviewed the decision.

The failure occurs when a proposal still needs evaluation but the agent treats it as settled—or endorses the reasoning behind it without evidence. The agent might change the component, update snapshots, and document the new style. That polished work makes the proposal look finished, but none of it proves that color caused the original problem.

Agreement is therefore a poor quality signal. Repository conventions, user reports, measurements, tests, and primary documentation can support a decision. Confident language cannot.

## Ask About the Problem Before Naming the Solution

The most useful first move is also the simplest: frame the problem as a question, not as a conclusion you want the agent to endorse. A controlled study found substantially less expressed sycophancy when the same content was presented as a question instead of a confident statement. Reframing the statement as a question also worked better than adding a generic instruction not to be sycophantic. The study was not about coding tasks, so treat this as strong directional evidence, not a guarantee for every agent. ([Ask, Don't Tell](https://arxiv.org/abs/2602.23971))

Instead of telling the agent:

> I think the Save button should be red because users cannot find it. Confirm that this is the right approach.

Try this instead:

> Users are having trouble finding the Save button. What could be causing that, and what evidence would distinguish the likely causes?

If you already have an idea, hold it back for one turn. Give the outcome and ask:

> People are having trouble finding the Save button. Before I suggest a solution, what questions do you have? Inspect the relevant components and styles. Ask only about facts whose answers could change the design, and do not propose a change yet.

After the agent has investigated, introduce red as one candidate rather than the answer. This ordering keeps your preference from becoming the starting assumption. That specific workflow has not been proven as an anti-sycophancy intervention in coding agents; it is an engineering application of the evidence on neutral framing and staged evaluation.

One caveat: clarification should be selective. Research shows that questions help when resolving uncertainty is worth another interaction, but unnecessary questions add friction. Ask about facts that could change the result—such as whether every form uses the same button component—not details the agent can safely infer for a small, reversible edit. ([Clarify When Necessary](https://aclanthology.org/2025.findings-naacl.306/))

## Active Partnership Is a Two-Way Conversation

Treating an agent as a partner changes the shape of the interaction. A command is one-way: you specify a change, and the agent executes it. A partnership uses multiple turns: you explain the outcome, the agent investigates and asks questions, you supply context it cannot discover, and the agent challenges assumptions or compares options before you commit to a solution.

For example, the Save-button discussion might unfold like this:

> **You:** People are having trouble finding the Save button. Inspect the interface and tell me what questions you have before recommending a change.
>
> **Agent:** The form already uses the shared primary-button style. Do we know where users get stuck or how the problem was reported?
>
> **You:** Three support tickets say users reach the bottom of the form and do not see how to continue.
>
> **Agent:** Then color may not be the cause. I will compare the button's position, contrast, and label against the other forms before recommending a change.

Each turn contributes something the other side lacks. The agent can inspect code and expose missing information. You can explain user reports, business constraints, and which tradeoffs matter. The agent can then test the proposed solution against that combined evidence instead of guessing what you meant.

The agent is not an equal decision-maker; you still own the decision. Partnership means giving it permission to pause, ask material questions, and disagree with your proposed implementation. It also means answering those questions instead of treating every pause as a failure to execute.

A useful opening prompt makes that exchange explicit:

> Work with me as an active engineering partner. Start by inspecting the repository for facts relevant to the outcome. Tell me what you can establish from the code, then ask me the questions whose answers could materially change the design. Wait for my answers before comparing solutions. Treat any implementation I suggest as a candidate, and support your recommendation with code, tests, measurements, or primary documentation.

Asking the agent to “list assumptions” is not enough. It may invent a neat list and then continue with your proposal. Ask which premises need evidence or could be false, then require the agent to check the ones the repository or documentation can answer.

## Reset the Frame When the Conversation Is Anchored

Once a conversation contains a proposal, a defense, and a rebuttal, asking the same agent to “reconsider” may keep it inside that social exchange. Research on multi-turn sycophancy found better correction when conflicting answers were presented side by side for neutral evaluation than when a user argued for a new answer in the existing dialogue. ([Challenging the Evaluator](https://aclanthology.org/2025.findings-emnlp.1222/))

For an important decision, start a fresh review and present the candidates together:

> Evaluate these options as an outside reviewer who proposed neither one:
>
> 1. Make the Save button red.
> 2. Use the application's existing primary-button style and adjust the form layout.
>
> Compare them against the design system, accessibility requirements, the reported user problem, implementation cost, and reversibility. Cite the evidence for each conclusion.

The fresh review does more than add another step. It removes the user's latest opinion from its privileged position and gives both options the same job: satisfy the same criteria.

Do not confuse a second opinion with independent evidence. Models are not consistently reliable at correcting themselves from reflection alone. Critique becomes more useful when it can point to a component definition, a test, a measurement, an API contract, or another check outside the model's own prose. ([When Can LLMs Actually Correct Their Own Mistakes?](https://aclanthology.org/2024.tacl-1.78/))
