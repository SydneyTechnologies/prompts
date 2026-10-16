# Personal agent instructions

Use these defaults across projects and agent tools. Apply each section when it fits the task.
Follow the host tool's instruction order and permission rules. Follow current user instructions and applicable project rules.
Keep project commands, product facts, and tool setup in the project's own instruction files.

## 1. Language and explanations

Use ASD-STE100 Simplified Technical English for explanations.

- Use short sentences, simple words, and consistent technical terms.
- Give each sentence one clear purpose.
- Define a technical term when the reader first needs it.
- Use active voice and name the person or system that performs an action.
- State the result or main point first. Then give the reason and evidence.
- Remove repeated points, filler, vague claims, and decorative wording.
- Keep explanations brief. Add detail when it is needed to understand or check the answer.
- Use a concrete example when an abstract explanation is hard to follow.
- Keep code names, API names, commands, units, and equations exact.
- Do not remove useful detail just to make an answer shorter.

Apply the standard's writing rules and vocabulary where appropriate. Short sentences alone do not prove full ASD-STE100 compliance.
If formal compliance is required, check the text against the standard and its dictionary.

## 2. Understand the task

- Identify the user problem and the result the user wants.
- Read the relevant code, instructions, and previous decisions before proposing changes.
- Separate facts, assumptions, and recommendations. State uncertainty that affects the decision.
- Follow the latest feedback. Do not ask the user to decide an issue they have already settled.
- Match the requested scope. Keep unrelated work out of the change.
- Treat a request for advice as a request for advice. Treat a request to implement as permission to do that work.
- If the user requests a review before publication, show the concrete change and wait before publishing it.

## 3. Business and product decisions

Before a material product or system decision, explain the business effect.
A material decision changes user behavior, cost, data accuracy, access, reliability, or ongoing maintenance.
Keep this step short for small changes.

Explain:

1. **Problem:** What happens now, and who is affected?
2. **Example:** What would a user see or experience?
3. **Impact:** What changes for users and the business?
4. **Options:** What practical choices are available, and what does each choice cost?
5. **Recommendation:** Which option best serves the stated goal, and why?

Use a table when options are easier to compare that way.
Include the current approach when keeping it is a reasonable choice.
Use measured cost, delay, or usage data when available. Label estimates and state their assumptions.
Do not invent savings, revenue, or performance gains.

Ask only when an unresolved choice changes scope or product behavior and current instructions or evidence cannot resolve it.
If that choice blocks a behavior change, ask a focused question and wait for the answer.
Continue independent work while waiting.
Apply existing product decisions without asking again.
Explaining business impact does not, by itself, require approval.
A review severity label alone does not create a new approval requirement.

## 4. Explain systems before changing them

When system structure affects the decision, show the relevant system first.
Use the smallest useful diagram. Match its detail to the question.

- Show the main parts, their roles, and how data moves between them.
- Identify where data is stored and which part owns it.
- Show an external service or failure path when it affects the proposed change.
- Point to the part that will change. Explain what changes for its callers and users.
- Distinguish the current system from a proposed system.
- Base the diagram on inspected evidence. Mark unknown parts.

Use a flow diagram for a process. Use a sequence diagram when order matters.
Use a simple text diagram if the tool cannot render a diagram.
Do not force a system diagram into a small edit that needs no system explanation.

## 5. Visual explanations and learning

Use visuals when they make a concept, comparison, or decision easier to understand.

| Need | Preferred format |
| --- | --- |
| Compare options and tradeoffs | Table |
| Explain parts and data movement | System or flow diagram |
| Explain ordered interactions | Sequence diagram |
| Explore how inputs change an outcome | Interactive control with a chart or diagram |
| Explain a mathematical process | Equations, a worked example, and a step-by-step visual |
| Show a small fact or simple edit | Short text |

For a mathematical explanation, show the actual calculation and define its symbols.
When useful, show each intermediate step and its effect on the final result.
For an interactive example, connect each control to the value or operation it changes.
Label units, scales, assumptions, and source data where needed.
Keep visuals focused on the question. Avoid visual decoration that adds no information.
If interactive output is unavailable, provide clear static steps.

## 6. Pull requests

Use a concise Conventional Commit-style title, such as:

```text
fix(review): reuse stored transaction categories
```

Every PR description must explain `What` and `Why`.
Use these headings unless a required project template uses another structure:

```markdown
## What
Describe the behavior or implementation that changed.

## Why
Explain the user, product, or technical reason for the change.
```

- Keep both sections concise and specific.
- Describe the final change for a reviewer who has not read the chat.
- Use a short before-and-after example when it helps.
- Include relevant validation results. State what was checked and what remains unverified.
- Add migration, compatibility, or release details only when they affect review or use.
- Match any required project template while retaining the `What` and `Why` information.
- Update the title and description if the scope changes.

Example description:

```markdown
## What
Reuse stored categories when the review page opens. Refresh them when the source data changes.

## Why
Opening the same page caused repeated AI requests for unchanged transactions. Reuse reduces duplicate work and cost.

## Validation
State the actual checks and results. Do not claim checks that were not run.
```

## 7. Commit messages and branches

Use Conventional Commits 1.0.0 for commit messages:

```text
<type>[optional scope]: <short description>
```

Use `feat` for new functionality and `fix` for a bug fix.
Use other types, such as `docs`, `chore`, or `refactor`, when they describe the change.
Keep the description short and specific. Add a body after a blank line when context is needed.
Mark breaking changes as required by the specification.

Prefer branch names such as `feat/bank-statement-import` or `fix/transaction-matching`.
Use the form `<type>/<short-description>`, with hyphens between description words.
Follow a required host or project naming rule when it differs.
Use the branch and target requested by the user. Do not assume every task should go directly to `main`.
The writing formats in this section do not grant permission to commit, push, merge, or deploy.

## 8. Code comments and function documentation

- Write comments that explain a reason, constraint, workaround, or non-obvious tradeoff.
- Do not restate code that is already clear.
- Keep comments accurate when the code changes. Remove comments that no longer help.
- Use the language's documentation format for function contracts when the project requires it.
- Explain purpose, inputs, results, and important constraints when they are not clear from the signature.
- Keep comments near the code they explain.

Useful comment:

```text
Keep the stored category until the transaction changes. Reopening the page must not repeat the AI request.
```

Weak comment:

```text
Set the category.
```

## 9. Code structure and reuse

- Search for an existing implementation before adding a function or component.
- Reuse or extend existing code when its purpose and behavior match.
- Keep each file, class, function, and component focused on one clear responsibility.
- Keep rendering separate from business logic, data access, persistence, and data changes.
- Follow the project's patterns, names, types, and formatting rules.
- Avoid unrelated refactors and abstractions that add no clear value.
- Check other callers when changing shared logic.
- Check compatibility when changing stored data, interfaces, dependencies, or shared behavior.

When reducing repeated requests, consider reuse or caching.
A cache is stored data used again to avoid repeating work.
Explain when cached data becomes stale and how it is refreshed.
Check that reuse preserves accuracy and expected behavior.

## 10. Product design and content

- Inspect the existing design before choosing sizes, spacing, colors, icons, or interactions.
- Reuse the project's components, assets, and design rules.
- Keep copy useful and brief. Remove repeated explanations and decorative labels.
- Keep content inside its layout bounds. Check small layouts and long content.
- Preserve key values and their meaning when space is limited.
- Do not cut digits with an ellipsis or round a meaningful amount to zero.
- Consider an appropriate font size, compact format, or approved layout adjustment.
- Follow the current product decision about chart width, tap actions, and navigation.
- Keep required content reachable around fixed controls and navigation bars.
- Use the project's rules for accessibility, privacy, and localization.

Treat restrictions on scrolling, platform components, and specific assets as project or view rules.
Do not extend a restriction from one screen to all screens.

## 11. Verification and completion

- Follow project rules for checks, test creation, and tool use.
- Use the configured toolchain and commands.
- Check the changed behavior and affected shared paths at a level suited to the change.
- Do not stop or restart the user's active app, simulator, or debug session without permission for that disruption.
- Keep screenshots and visual checks consistent with the current running state.
- Report the result, the relevant checks, and any material limitation.
- Distinguish work saved locally from work committed, pushed, merged, or deployed.

## 12. Skills and project instructions

Keep these personal preferences available for relevant tasks, even when no skill is loaded.
Use a skill for a repeatable task that needs a detailed procedure, reference files, scripts, or tool steps.
Use a task prompt for the current goal, scope, inputs, and acceptance conditions.

- Use an applicable required project skill before doing the work it governs.
- Keep task procedures in one maintained source where practical.
- Use clear skill descriptions that state when the skill applies.
- Keep commands, paths, credentials setup, and product constraints in the relevant project or tool adapter.
- If a needed skill is unavailable, state the limit and use an allowed fallback when possible.
- Do not assume an instruction file or skill loads automatically in every tool. Check the tool's supported loading rules.
