---
name: ship-check
description: Run a preshipment review for scope, risk, tests, rollout, and rollback.
disable-model-invocation: true
---

# Ship Check

Use this skill before shipping a change, a release, or a branch with user impact. The job is not to invent more work. The job is to confirm that the work is safe, explained, and reversible.

## Core rule

Do not call the release ready until the change has evidence behind it. Evidence is a short list of artefacts:

- the spec, ticket, or understanding of what changed
- the key regression checks that pass
- a clear statement of risk and blast radius
- a rollback or mitigation path
- a brief note for the humans who are shipping it

If the change cannot be explained in plain language, it is not ready.

## Process

### 1. Confirm the change

Start from the originating spec, issue, or ticket. Answer:

- What exactly changed?
- What was intentionally excluded?
- What is the expected user-visible behaviour?
- What is the release boundary: branch, feature flag, full release, or hotfix?

If the change is vague, stop and sharpen it before moving on.

### 2. Check the evidence

Review the relevant proof points.

Look for:

- passing tests at the relevant seam
- any manual validation that was actually run
- warnings, TODOs, or partially-complete work that still ships
- dependency or migration steps that are easy to miss

If a claim is made without evidence, mark it as a blocker.

### 3. Assess the risk

Write down the likely failure modes.

Ask:

- Who or what can break?
- Is this read-only, write-heavy, or data-changing?
- Does it affect authentication, billing, permissions, or critical workflows?
- Does it need a feature flag, a phased rollout, or a canary?

The goal is not zero risk. The goal is to know the risk and not be surprised by it.

### 4. Check rollback and recovery

A change is not a release unless the team knows how to undo it.

Answer:

- How do we revert it quickly?
- Does the data model support rollback?
- Do we need scripts, DB migrations, or config changes to walk back?
- Is the feature flag or toggle already available?

If rollback is unclear, leave the change not ready.

### 5. Produce a go or no-go summary

End with a concise summary that states:

- current status: go / no-go / conditional go
- why the change is safe or not safe
- the key evidence behind the decision
- the remaining blockers, if any
- the rollout or rollback plan

Keep it short enough that a teammate can review it in one minute.

## Questions to ask before shipping

- Is this the actual scope we agreed to?
- Is there a real regression test or a concrete validation step?
- What is the user-visible consequence if it fails?
- Is there a high-confidence rollback path?
- Are the docs, release notes, or communications ready?
- Is there any work hidden in this branch that should not ship yet?

## Completion criteria

The skill is done when the output includes a clear answer to these questions:

- [ ] What changed?
- [ ] What is the evidence it works?
- [ ] What could break?
- [ ] How do we undo it?
- [ ] Do we ship now or wait?

If any of those are missing, the answer is not ready.
