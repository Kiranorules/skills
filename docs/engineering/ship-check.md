## What it does

`ship-check` is a preshipment review for any change with user impact. It keeps the release decision grounded in evidence: scope, risk, verification, and rollback. It is intentionally brief and practical, so a teammate can use it as a final gate before a branch, hotfix, or feature rollout is considered ready.

## When to reach for it

Type `/ship-check` before shipping a branch, release, or significant change. Use it when the work is built but still needs a final "go / no-go" check.

| Your situation | Reach for |
| --- | --- |
| The feature is done but you need a final release sanity check | `ship-check` |
| You want to confirm what could break before a push | `ship-check` |
| You need a clean rollback plan before release | `ship-check` |
| The work is already validated and you want a concise ship summary | `ship-check` |

## Common questions

**Is this just a generic release checklist?**

It is a release checklist, but built around engineering evidence rather than ceremony. The key difference is that every conclusion is tied to a real fact: the scope, the validation, the risk, and the rollback path.

**Can I skip it for small changes?**

You can, if the blast radius is truly tiny and the team already knows the risk. For anything user-facing, data-changing, or cross-service, the skill is valuable because it forces a clear fallback plan.

**How is it different from a test run?**

A test run answers "does the code work in the happy path." `ship-check` asks, "what else could go wrong, what evidence do we have, and how do we recover?"

## It's working if

- It asks what changed and checks the scope against the original goal.
- It looks for actual evidence, not assumptions.
- It names the main risk and the likely failure modes.
- It asks how the change can be rolled back.
- It finishes with a clear go / no-go statement.

## Where it fits

`ship-check` sits at the sharp edge of the build flow, after implementation and validation but before shipping.

- [implement](https://aihero.dev/skills-implement) is the build step that produces the change.
- [code-review](https://aihero.dev/skills-code-review) checks the diff for standards and spec compliance.
- [tdd](https://aihero.dev/skills-tdd) supplies the quality loop for the actual behaviour.
- [ask-matt](https://aihero.dev/skills-ask-matt) can route you here when the change is ready to ship but still needs a final decision check.
