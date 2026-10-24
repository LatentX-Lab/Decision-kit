# Contributing

Propose changes on a branch and open a pull request explaining the problem, the resulting behavior or guidance, and validation performed.

## Research

Use the [brief review instructions](instructions/research-brief-review-instructions.md) and [brief template](templates/research-brief.md). Keep questions neutral and distinguish mandatory constraints, preferences, hypotheses, and unresolved items.

Give each topic and run a stable identifier. Record the exact input commit and paths, instructions, model, execution date, capabilities, and evidence. Mark unavailable values as unknown. Preserve original outputs; put subsequent synthesis or corrections in separately identified artifacts.

Verify critical claims independently before they support an accepted decision. If verification is incomplete, report the limitation and affected conclusion. Model consensus alone is not verification.

## Decisions and approval

Create significant decisions in `decisions/` using the [ADR template](templates/decision.md). Keep proposed, accepted, rejected, deprecated, and superseded records in the same directory, and maintain the index.

Acceptance requires a recorded authorized human decision-maker, date, and review reference. A merged proposal does not imply approval unless that approval is explicit. Projects adopting this toolkit must identify their own decision authority.

Preserve an accepted ADR's substantive rationale. Record a material change in a new ADR and link both records. Editorial corrections and status or cross-reference updates may be made transparently.

Publish guidelines with their scope, owner, approval status, evidence, and reassessment triggers. Distinguish required standards from recommendations and examples.

## Reassessment and review

Create a new run, link the previous assessment, and identify changed inputs and evidence. Explain material differences and their impact on decisions or guidance. Do not assume a newer model is more correct.

Before requesting review, check relative links, stable identifiers, dependency references, evidence traceability, and approval claims. Documentation-only changes need no runtime tests. Research that depends on executable verification must include its procedures and actual results.
