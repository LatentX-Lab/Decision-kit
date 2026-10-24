# Model Agnostic Technical Research and Decision Management

**Document type:** High-Level Requirements Specification  
**Status:** Draft  
**Audience:** Senior engineers, software architects, and technical managers  
**Domain:** Engineering Knowledge Management and Architecture Knowledge Management

## 1 Purpose and intended outcome

Establish a Git-based knowledge repository and supporting workflow for reusable technical research, technology assessments, architectural decisions, and engineering guidelines. Engineers shall be able to define a research problem once and reassess it using different large language models (LLMs), updated evidence, and revised organizational requirements.

The repository shall maintain research specifications separately from research outputs and accepted decisions. This separation enables repeatable research, comparison of findings over time, and preservation of the rationale behind engineering decisions.

The intended outcome is a maintained body of engineering knowledge that supports context-specific, evidence-based decisions. Recommendations represent the best-supported conclusions available within a documented scope and assessment date. The process does not guarantee a universally optimal answer, exhaustive evidence coverage, or improvement solely from using a newer model.

The approach draws on Docs as Code, Evidence-Based Software Engineering (EBSE), Architecture Knowledge Management (AKM), Architecture Decision Records (ADRs), Requests for Comments (RFCs), and LLM evaluations. These practices inform the requirements; this document does not claim conformance to a particular external standard.

## 2 Problem statement and objectives

Conversational research often leaves questions, constraints, evidence, and recommendations distributed across separate sessions. Repeating the work can require reconstructing its context, while changing technologies and model behavior make results difficult to compare. Earlier reasoning may also be lost when a new recommendation replaces an old answer.

The solution has six objectives:

1. Preserve reusable research questions, scope, constraints, and acceptance criteria independently of generated answers.
2. Enable research across LLM providers and versions without changing the meaning of the research specification.
3. Support recommendations with traceable evidence, explicit assumptions, and verification proportionate to their significance.
4. Compare successive assessments and identify changes that affect engineering decisions.
5. Preserve accepted decisions, rejected alternatives, and the rationale for subsequent changes.
6. Maintain actionable engineering guidance through accountable human review.

## 3 Scope and requirement conventions

### Initial scope

The initial solution comprises a Git repository, artifact templates, documented workflows, and supporting validation where needed. Manual execution through LLM interfaces is acceptable. Automated model invocation, scheduling, or orchestration is not required to satisfy the initial scope.

The scope includes technical research, technology assessment, evidence management, decision support, research quality assessment, and maintenance of engineering guidelines.

A dedicated knowledge management application, autonomous architecture governance, automatic policy approval, general-purpose agent orchestration, complete implementation generation, support for every model provider, and real-time monitoring of all technologies are outside the initial scope.

### Requirement language

- **Shall** identifies a mandatory requirement.
- **Should** identifies a recommendation. A decision not to follow it should have a documented rationale.
- **May** identifies an optional capability or permitted approach.

Objectives and examples provide context. The functional requirements, non-functional requirements, and acceptance criteria define what the initial solution must support. The term **solution** includes the repository, supporting tools, and documented human workflow; it does not imply a standalone software product.

### Key terms

| Term | Meaning in this specification |
| --- | --- |
| Model-agnostic | Core research content is portable across LLM providers and versions. Provider-specific execution adapters may differ. |
| Research brief | Versioned specification of the problem, questions, context, constraints, evaluation criteria, and expected deliverables. |
| Research run | One execution of a specified research brief revision with a recorded model and execution context. |
| Technical assessment | Synthesized findings, analysis of alternatives, limitations, and recommendations derived from research and verification. |
| Quality evaluation | Assessment of research output against a defined rubric or verification method. An LLM eval is one form of quality evaluation. |
| Critical claim | A factual claim whose failure could materially change a decision or violate a mandatory constraint, as identified by the research owner or reviewer. |
| Independent verification | Checking a claim against relevant source material, executable tests, or other inspectable evidence beyond an LLM's unsupported assertion. |
| Accepted decision | A decision approved by an authorized human decision-maker and recorded with its rationale. |
| Material change | A change that could affect a decision, a required practice, or a recommendation's applicability, risks, or trade-offs. |

## 4 Knowledge artifacts

Artifacts shall have stable identifiers and links sufficient to trace requirements, findings, evidence, decisions, and guidance. Several artifacts may share a file when their identities and responsibilities remain clear.

| Artifact | Primary responsibility |
| --- | --- |
| Research brief | Define the research problem and the criteria for an acceptable assessment. |
| Research run record | Identify the exact inputs, execution context, outputs, and completion status of a research run. |
| Technical assessment | Present supported findings, alternatives, uncertainty, and recommendations. |
| Evidence and verification artifacts | Preserve source references, tests, benchmark procedures, compatibility checks, and their results. |
| Quality evaluation record | Record the rubric, checks, reviewer or evaluator, results, and unresolved quality issues. |
| RFC or design proposal | Present a proposed approach or standard for engineering review when discussion is needed. |
| Architecture Decision Record | Record a significant architectural decision and its context, rationale, status, and consequences. |
| Engineering guidelines | Publish maintained implementation guidance, its applicability, exceptions, and approval status. |

An RFC or ADR is required only when the subject warrants the corresponding review or decision record. Routine research does not require either artifact. Run and quality evaluation records may be combined if research execution and output assessment remain distinguishable.

## 5 Functional requirements

### FR 01 Research brief management

The solution shall support version-controlled research briefs containing:

- A stable identifier, owner, problem statement, and research objectives.
- Research questions, dependencies, scope, exclusions, and relevant technical context.
- Organizational constraints, target environments, and applicable technology versions or version-selection rules.
- Evaluation criteria, their priorities, expected deliverables, and acceptance criteria.

Briefs shall remain usable independently of previous generated answers. They shall distinguish required constraints from hypotheses and shall permit conclusions that reject a proposed approach or find insufficient evidence. Changes to scope, criteria, or constraints shall create a new brief revision.

### FR 02 Model-agnostic research execution

The solution shall support executing the same research brief revision with different LLM providers or model versions without rewriting its core requirements.

Provider-specific instructions, tool configuration, and invocation details shall be maintained separately from the brief. Such adaptations shall preserve the brief's meaning and acceptance criteria.

Each run shall record available research capabilities and material limitations, including unavailable browsing, inaccessible sources, or inability to execute tests. A run that cannot satisfy a required criterion shall identify that criterion as unmet; it shall not represent unperformed research or verification as completed work.

### FR 03 Research decomposition and synthesis

The solution shall support decomposing a research objective into related questions and recording their dependencies.

Dependent analysis shall reference the specific upstream findings and verification status it uses. Where an upstream result remains uncertain, the synthesis shall preserve that uncertainty and explain its effect on the recommendation.

The solution shall support combining findings into a technical assessment without losing links to the underlying questions and evidence.

### FR 04 Evidence management and provenance

Each assessment shall link material factual claims to supporting sources or verification results. Evidence records shall identify the source, a retrievable reference or locator, the access or verification date, and applicable technology versions. Publication or update dates shall be recorded when available.

Assessments shall:

- Distinguish supported findings, assumptions, interpretations, and recommendations.
- Identify contradictory evidence, unresolved questions, and material limitations.
- State the assessment date and the versions or environments to which findings apply.
- Identify critical claims requiring independent verification and record their verification status.

Research should prioritize authoritative primary sources, relevant empirical findings, and reproducible experiments. Source authority and recency shall not be treated as sufficient evidence of applicability. Where source retention is feasible and permitted, evidence records should include a versioned reference or snapshot to reduce the impact of later source changes.

### FR 05 Technical assessment and recommendations

Each technical assessment shall compare viable alternatives against the brief's criteria and explain relevant benefits, costs, constraints, risks, and implementation consequences. Retaining the current approach shall be considered where relevant.

Recommendations shall state their rationale, applicability, material limitations, and conditions that could change the conclusion. If the evidence does not support a recommendation, the assessment shall identify the remaining work or decision needed.

Multi-criteria decision analysis (MCDA) may be used where it improves the comparison. When numerical scoring is used, the assessment shall disclose the criteria, weights, scoring basis, and material sensitivity to those choices. Scores shall not imply greater precision than the evidence supports.

### FR 06 Architectural decision management

The solution shall support an ADR lifecycle that distinguishes proposed, accepted, rejected, deprecated, and superseded decisions. Significant architectural decisions should be documented in ADRs; a model-generated recommendation does not become an accepted decision merely by being recorded.

Each accepted ADR shall capture its context, alternatives, selected approach, rationale, expected consequences, approval date, decision authority, and supporting research references.

An accepted ADR's substantive rationale shall remain historically intact. A material change to the decision shall be recorded in a new ADR that links to the superseded record. Status updates, cross-references, and clearly identified editorial corrections may be applied to the earlier record.

### FR 07 Engineering guideline management

The solution shall support deriving engineering guidelines from validated assessments and accepted decisions, where applicable.

Guidelines shall identify their owner, approval status, scope of applicability, supporting artifacts, and review date or reassessment triggers. They shall distinguish mandatory organizational standards from recommended practices and optional examples.

As relevant to their subject, guidelines shall address design principles, implementation practices, compatibility, accessibility, performance, security, maintainability, exceptions, and verification criteria. Proposed changes shall remain distinguishable from currently approved guidance.

### FR 08 Reassessment and change analysis

The solution shall support periodic and event-driven reassessment. Triggers may include technology releases, standards changes, newly identified defects or vulnerabilities, new empirical evidence, improved model capabilities, or changed organizational requirements.

Each reassessment shall:

1. Identify the previous assessment and confirm or revise the research brief.
2. Review updated evidence, assumptions, and relevant verification results.
3. Compare findings and recommendations with the previous assessment.
4. Identify material differences and the downstream decisions or guidelines affected.
5. Recommend retaining, revising, superseding, or retiring the affected guidance or decision.

The comparison shall identify changed inputs, evidence, models, tools, and criteria where known. It shall not attribute a difference to model quality when other changed conditions could explain it. A newer model or a different answer shall not automatically invalidate an accepted decision.

### FR 09 Research quality assessment and LLM evaluations

Research outputs shall be assessable against the brief's acceptance criteria. The solution should support a shared quality rubric covering factual correctness, evidence validity, completeness, constraint compliance, trade-off analysis, actionability, and treatment of uncertainty.

Evaluation methods may include deterministic checks, executable tests, reference-based checks, rubric-based assessment, and expert review. Each recorded quality evaluation shall identify the output revision, rubric or criteria revision, methods used, evaluator, results, and unresolved issues.

LLM-based judging may assist evaluation. Critical technical claims shall receive independent verification before they support acceptance; model agreement or a judge score alone does not constitute verification.

Cross-model comparisons shall disclose differences in inputs, tool access, evidence availability, and execution conditions. Repeated runs may be used to assess variability when consistency is an evaluation objective.

### FR 10 Version control and research run records

The repository shall preserve distinguishable revision histories for research briefs, assessments, evidence, quality evaluations, proposals, ADRs, and guidelines. These histories may reside in one Git repository; separate repositories or branches are not required.

Each research run record shall include:

- A run identifier, execution date, provider, model identifier, and model version when exposed by the provider.
- The research brief revision and revisions of referenced inputs or upstream assessments.
- Execution instructions or a reproducible reference to them, available tools, and relevant configuration where exposed.
- Evidence references, output artifacts, completion status, and material execution limitations.

Unavailable metadata shall be marked as unknown. Completed run outputs shall be retained; later corrections or reviewed syntheses shall be distinguishable from the original output. The repository shall support comparisons between runs and identification of the latest approved guidance.

### FR 11 Human review and decision authority

The solution shall distinguish generated output, reviewed findings, proposed decisions, and accepted decisions.

Acceptance of significant architectural decisions and company-wide engineering standards shall require an authorized human decision-maker. The review record shall identify the reviewer or approver, date, disposition, and unresolved material concerns.

Automated research shall not independently change organizational policy. Engineers shall be able to challenge findings, request further evidence, and reject recommendations through the documented review workflow.

## 6 Non-functional requirements

| ID | Quality attribute | Requirement |
| --- | --- | --- |
| NFR-01 | Portability | Core specifications shall use documented, provider-independent formats. Execution adapters shall not become the sole source of research requirements. |
| NFR-02 | Maintainability | Specifications and narrative artifacts shall use human-readable, diffable formats. Shared templates and documented contribution practices shall support routine engineering review. |
| NFR-03 | Traceability | A reviewer shall be able to navigate from an approved guideline or decision to its assessment, relevant evidence, and research brief revision. |
| NFR-04 | Repeatability | Recorded inputs and procedures shall be sufficient to repeat an assessment to the extent the underlying services and evidence remain available. Identical LLM outputs are not required. |
| NFR-05 | Extensibility | Additional model integrations, verification methods, and evaluation rubrics should be supported without changing the meaning of existing briefs. |
| NFR-06 | Auditability | Historical decisions, run outputs, reviews, and changes shall remain accessible with their identities and revision relationships intact. |
| NFR-07 | Verifiability | Critical claims shall identify an independent verification method and result, or remain explicitly unverified and ineligible to support acceptance. |
| NFR-08 | Consistency | Shared templates and, where used, evaluation rubrics shall provide a common basis for assessment while allowing documented, justified deviations. |

## 7 Operating workflow and responsibilities

An engineer may perform more than one role. Decision authority shall remain explicit even when research, review, and maintenance are performed by the same person.

| Role | Responsibility |
| --- | --- |
| Research owner | Maintain the brief, define acceptance criteria, and identify reassessment needs. |
| Research contributor | Execute research, preserve run records, and prepare findings and evidence. |
| Technical reviewer | Check evidence, challenge reasoning, and assess whether acceptance criteria are met. |
| Decision authority | Accept or reject significant decisions and organizational standards. |
| Guideline maintainer | Publish approved guidance and coordinate updates when supporting knowledge changes. |

The workflow consists of the following steps:

1. **Define:** Create or revise a research brief and select the revision to execute.
2. **Research:** Conduct an LLM-assisted research run and preserve its inputs and outputs.
3. **Verify and assess:** Validate material claims, analyze alternatives, and record quality findings. Iterate where evidence is incomplete.
4. **Review and decide:** Submit an RFC when discussion is needed and record significant decisions in ADRs where appropriate.
5. **Publish:** Incorporate approved results into maintained engineering guidelines.
6. **Reassess:** Repeat research when due or triggered, compare changes, and submit justified updates for review.

## 8 Acceptance criteria

The initial solution shall demonstrate the following using a representative research brief and its supporting artifacts. Acceptance is assessed through repository inspection and a documented end-to-end walkthrough; a dedicated application or automated execution engine is not required.

| ID | Demonstration | Requirements covered |
| --- | --- | --- |
| AC-01 | Create and revise a research brief containing the required fields while preserving its identifier and revision history. | FR-01, FR-10 |
| AC-02 | Execute the same brief revision with at least two different LLM providers or model versions without changing its core requirements. Preserve both run records and disclose execution differences. | FR-02, FR-10; NFR-01 |
| AC-03 | Produce an assessment that links material claims to evidence, identifies applicable versions, and distinguishes uncertainty and unverified claims. | FR-04; NFR-07 |
| AC-04 | Synthesize at least two related questions into a recommendation that compares viable alternatives and retains dependency references. | FR-03, FR-05 |
| AC-05 | Record a reassessment that identifies changed inputs and material differences, or explicitly concludes that no material change is justified. | FR-08 |
| AC-06 | Demonstrate proposal, acceptance, and supersession of an architectural decision while retaining the earlier rationale and approval record. | FR-06, FR-11 |
| AC-07 | Trace an approved guideline to its assessment, supporting evidence, and brief revision, including an ADR when applicable. | FR-07; NFR-03 |
| AC-08 | Record a quality evaluation against specified criteria and independently verify critical claims used to support acceptance. | FR-09; NFR-07 |
| AC-09 | Have an engineer use the recorded inputs and procedures to repeat the research workflow and document any unavailable dependencies. | FR-10; NFR-04 |
| AC-10 | Demonstrate a review that can challenge or reject generated recommendations and distinguish proposed changes from currently approved guidance. | FR-11; NFR-06 |

For AC-02, two versions from one provider satisfy the minimum demonstration. Using two providers is recommended because it more directly tests provider portability. This demonstration does not establish compatibility with every provider.

## 9 Illustrative research brief

### Framework agnostic UI component architecture

**Objective:** Assess whether standards-based Web Components are suitable for a company-wide UI component library consumed by multiple frontend frameworks. Recommend an approach that meets the organization's interoperability, performance, accessibility, and maintenance requirements.

**Scope definition:** Before execution, specify the frameworks, exact versions, target browsers, representative component types, and workloads. State whether server-side rendering, hydration, form participation, and other specialized capabilities are in scope. Replace open-ended version labels such as “React 19+” with an explicit tested matrix and a rule for selecting future versions.

**RQ-01 Framework interoperability:** For each selected framework, can applications consume custom elements directly without a required framework-specific wrapper or adapter? Assess property and attribute handling, custom events, lifecycle behavior, and any in-scope rendering features. Report limitations by capability and version rather than relying on an undefined claim of “native support.”

**RQ-02 Integration and performance:** What additional considerations arise compared with framework-native components under equivalent workloads? Identify which existing optimization practices apply, which require adaptation, and which integration costs can be measured. Define the benchmark environment and acceptance thresholds before drawing performance conclusions.

**RQ-03 Architecture and implementation guidance:** Based on verified findings from RQ-01 and RQ-02, what component architecture and implementation practices should be adopted? Identify exceptions, required adapters, or alternative approaches if Web Components do not meet particular requirements.

**Evaluation criteria:** Web standards compliance, interoperability, runtime and rendering performance, API stability, maintainability, developer experience, accessibility, and long-term compatibility. The brief owner shall distinguish mandatory constraints from preferences and define any necessary thresholds or priorities.

**Expected artifacts:** A versioned compatibility matrix, performance and integration assessment, comparison of viable approaches, proposed engineering guidelines, verification procedures and results, and ADRs for significant architectural decisions where applicable.

**Reassessment triggers:** Relevant framework or browser releases, changes to applicable standards, new compatibility or benchmark evidence, and changes to organizational requirements. Reassessment shall determine whether existing guidance remains appropriate and identify justified changes.

