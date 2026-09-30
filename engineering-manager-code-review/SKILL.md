---
name: engineering-manager-code-review
description: Review a pull request from an engineering manager's perspective, focusing on user impact, production risk, evidence, and constructive feedback. Use for PR review requests; adapt to the repository's own instructions and workflows.
---

# Engineering Manager Code Review

Review the change as a steward of product behavior, team learning, and safe delivery. Give engineers a clear path to resolve material risks. Follow the target repository's instructions and the user's scope before using this guidance.

## Establish the change

- Confirm the repository, PR base and head, goal, and current diff. Read relevant repository guidance and inspect the complete base-to-head change, including configuration, dependencies, tests, and migrations.
- List the behaviors added, changed, or removed. Identify affected users, API and data contracts, operations, and rollout paths.
- Trace consequential behavior through callers, validation, authorization, business logic, persistence or external systems, and consumers. Check whether related code or another repository depends on the old contract.

## Investigate proportionate to risk

- Start with correctness and regression risk. For each material behavior, consider a normal case, a boundary case, and applicable failure cases such as missing data, invalid input, retries, partial failure, or concurrency.
- Check security and privacy, tenant or role isolation, compatibility, data integrity, observability, performance at realistic scale, deployment order, and rollback where the change touches them.
- Use the smallest relevant tests and safe repository-native checks. Examine what assertions prove, including whether mocks bypass the suspected boundary. Distinguish code inspection, tests, and live behavior as separate levels of evidence.
- Compare the base and head when it helps establish whether the PR introduced a behavior. Record checks that could not run and the resulting uncertainty.
- Stop expanding the review when the changed behavior and material risks have evidence or a clearly stated gap. Do not create findings from style preferences or speculative failure modes.

## Report actionable findings

For each proposed finding, establish: a reachable trigger; expected and actual behavior; exact code location; concrete user, business, security, or operational impact; evidence; and why existing safeguards do not prevent it. Rank by impact and urgency, and combine comments that share a root cause.

Write feedback in a respectful, direct voice. Explain the problem and required outcome, then suggest focused regression cases or manual checks. Phrase implementation ideas as options when several approaches could work. Keep coaching and optional improvements separate from defects that should block delivery.

Finish with a concise review summary: change intent, confirmed findings, checks performed, verification gaps, and residual release risk. If no actionable findings remain, say so without implying that unrun checks passed. Draft comments or a review for the user; publish, approve, merge, or alter shared state only when authorized for that action.
