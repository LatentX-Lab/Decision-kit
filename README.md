# Decision Kit

A model-agnostic toolkit for LLM-assisted technical research, evidence-based engineering decisions, and human-reviewed guidelines.

Define reusable research questions, compare evidence across models and time, and preserve why engineering decisions were made. Engineers remain responsible for accepting decisions and standards.

## Start here

1. Read the [requirements](docs/technical-research-decision-requirements.md) for scope, terminology, and acceptance criteria.
2. Apply the [research brief review instructions](instructions/research-brief-review-instructions.md) to your questions and constraints.
3. Save the resulting brief in `research/<topic>/brief.md`.
4. Record each execution in `research/<topic>/runs/<run-id>/`, using the [run template](templates/research-run.md). Keep original output separate from reviewed findings.
5. Verify important claims, review alternatives, and propose significant decisions using the [ADR template](templates/decision.md).
6. Publish approved practices in [guidelines](guidelines/README.md). Reassess when evidence or requirements materially change.

The requirements and instructions are drafts. This starter repository does not itself demonstrate that every acceptance criterion has been satisfied.

## Repository map

| Location | Purpose |
| --- | --- |
| `docs/` | Requirements and explanation of the framework |
| `instructions/` | Reusable, provider-independent LLM instructions |
| `templates/` | Starting points for briefs, runs, decisions, and guidelines |
| [research/](research/README.md) | Topic briefs, run outputs, assessments, and evidence |
| [decisions/](decisions/README.md) | Proposed and accepted ADRs, rationale, and decision index |
| [guidelines/](guidelines/README.md) | Maintained engineering practices with explicit approval status |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Review and maintenance workflow |
| [AGENTS.md](AGENTS.md) | Entry point for agents working in this repository |

Use this repository as a shared toolkit or adopt its structure in a project. Keep sensitive project research in a repository with appropriate access controls; this repository is public.

## Reuse from another repository

Pin an adopted revision by full commit SHA. A release tag can provide a readable label when one exists; record its resolved SHA as well. No `v1.0` release is assumed by this starter.

A consuming repository can keep a reviewed local copy of the relevant requirements, instructions, and templates, with their source URL and commit SHA recorded. Its root `AGENTS.md` should explain which documents to read for each task. Update the adopted revision through a reviewed pull request.

A Markdown link is a reference, not a universal remote-import mechanism. Ensure the chosen agent can actually access and read the referenced content. Keep the requirements document separate from `AGENTS.md`; add folder-specific instructions only when they add relevant local guidance.

## Principles

- Keep reusable inputs separate from provisional findings and approved decisions.
- Prefer verified evidence over model agreement.
- Preserve uncertainty and historical rationale.
- Treat newer model output as a reason to reassess, not automatic authority to change policy.
- Use only the artifacts needed for the problem; manual execution is supported.

## License

See [LICENSE](LICENSE).
