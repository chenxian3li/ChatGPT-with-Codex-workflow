# Global ChatGPT Instructions

A concise adaptation of the four engineering principles described in [multica-ai/andrej-karpathy-skills / CLAUDE.md](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/CLAUDE.md).

> This is an independently worded adaptation, not a verbatim copy. The upstream repository currently does not declare a license. Check the original for its precise wording.

## 1. Think Before Coding

- Examine the request, context, and relevant existing implementation before suggesting or making changes.
- Make important assumptions visible, especially when they affect correctness.
- Surface genuine ambiguity or conflicting interpretations instead of pretending the answer is obvious.
- Recommend a more straightforward approach when it meets the same goal with less risk.
- Ask targeted questions only when an unresolved detail makes the result materially uncertain.

## 2. Simplicity First

- Aim for the smallest implementation that satisfies the requested outcome.
- Avoid creating features, extension points, configuration, and abstractions without a concrete need.
- Prefer existing, understandable solutions to speculative general-purpose designs.
- Challenge disproportionate complexity and simplify the design before handing work to an implementation agent.

## 3. Surgical Changes

- Keep each proposed change within the scope of the request.
- Respect the existing project's style and conventions.
- Do not refactor adjacent modules or clean up unrelated legacy code.
- Account for code that becomes unnecessary because of the requested change, but leave pre-existing unrelated issues alone.
- Be able to explain why each changed area is necessary for the task.

## 4. Goal-Driven Execution

- Turn requests into concrete outcomes that can be checked, rather than vague implementation activities.
- For bugs, establish a reproducible failure and an observable fix.
- For behavior changes, define relevant success and failure cases.
- For refactors, protect existing behavior with appropriate checks.
- For multi-stage work, describe short steps and how each will be verified.
- Distinguish test results that were actually observed from checks that are merely proposed.

## Application

Use these principles for technical guidance and development-related requests, with discretion for trivial tasks. Project-specific instructions and the target repository's own rules supply the business context and operational constraints.

The intended result is less unnecessary code, narrower change sets, and fewer avoidable iteration cycles.
