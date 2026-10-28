# Hypercraft Engineering Contribution Guidelines

## 1. Purpose

These guidelines establish organization-wide expectations for the design, development, review, verification, and maintenance of software in Hypercraft-managed repositories.

Hypercraft encourages engineers to use approved tools, including AI-assisted development tools, to improve engineering quality and delivery speed. Tool choice does not reduce engineering accountability. 

These standards apply to employees, contractors, and other authorized contributors. Repository and program-specific requirements may imposed additional controls but may not weaken mandatory company standards.

## 2. Engineering Principles

1. **Human Ownership.** Every change has an accountable human author or technical owner who understands its intended behavior, assumptions, and limitations.
2. **Engineering intent.** Significant changes begin with a clear problem statement, intended behavior, and acceptance criteria.
3. **Proportionate rigor.** Design, documentation, review, and verification reflect both change complexity and the consequences of failure.
4. **Reviewable increments.** Changes should be coherent, appropriately scoped, and understandable to qualified reviewers.
5. **Evidence over confidence.** Builds, tests, reviews, and other verification evidence support acceptance; confidence in a person or AI system alone does not.
6. **Maintainability and security.** Changes should preserve understandable interfaces, safe failure behavior, and sustainable long-term ownership.
7. **Responsible acceleration.** Approved AI tools are encouraged where they improve engineering outcomes without compromising the standards above.

## 3. Development Workflow

Development generally follows **understand -> plan -> implement -> verify -> review -> integrate**. The formality of each activity depends on complexity and risk; a small fix does not require a separate design document.

### 3.1 Workflow Selection

|**Workflow**|**Typical scope**|**Minimum expectations**|
|------------|-----------------|------------------------|
|**Routine**|Isolated fixes, minor refactoring, documentation, small utilities|Clear change intent, author inspection, applicable tests, review under branch policy|
|**Structured**|New features, new interfaces, substantial refactoring, multi-component changes|Documented approach and acceptance criteria, reviewable implementation steps, verification evidence|
|**Controlled**|Changes affecting safety-related behavior, critical operational functions, or other formally controlled systems|Applicable requirements and traceability, authorized design/review process, independent verification and release controls|

Workflow selection reflects the **complexity and nature of the work**. The software risk level in Section 4 independently determines the minimum required controls. Where requirements differ, the stricter applicable requirement governs.

### 3.2 Work Items and Requirements Traceability

Software development activities must be associated with a documented work item in a company-approved tracking system.

Work items may represent features, enhancements, defects, maintenance, refactoring, infrastructure changes, or other engineering objectives.

Each work item should define, as appropriate:

- Purposed and intended outcome.
- Scope and expected beahvior.
- Acceptance criteria.
- Related features, requirements, or dependencies.

Significant development efforts should be decomposed into manageable tasks with clear responsibilities and verifiable outcomes.

Pull requests targeting `main` must reference an associated work item or applicable parent requirement.

Minor administrative changes, such as documentation formatting or typographical corrections, may be exempt from inidividual work-item requirements.

Critical software must maintain additional requirements and verification traceability according to applicable engineering standards. 

### 3.3 Planning and Implementation

For Structured and Controlled work, establish the expected behavior, important constraints, interfaces, failure modes, and verification approach before substantial implementation. A linked issue or concise design note is sufficient when appropriate; formal documentation is required where dictated by risk or program rules.

Break substantial changes into coherent increments when practical. Avoid mixing unrelated refactoring, dependency changes, and behavior changes in a single pull request unless there is a documented reason.

Engineering decisions that materially change architecture, public interfaces, safety behavior, security boundaries, or operational assumptions require review by the appropriate technical owner before integration.

Hypercraft uses a risk-based development process that distinguishes between development activities and integration into protected branches.

### 3.4 Branches and Integration

Development branches support experimentation and iterative collaboration. Organization-wide PR documentation is optional for PRs not targeting main, unless repository-specific rules require it.

Changes targeting main must use a pull request, meet applicable automated checks, receive the required independent human review, and include sufficient verification information. Direct changes to protected branches require an authorized exception.

Merging into main does not itself authorize production deployment or release. Deployment and release follow applicable program and operational controls.


## 4. Software Risk Classification

Classify changes based on the potential consequences of failure, not whether AI was used to create them. If multiple classifications apply, use the highest applicable level.

| Level | Classification | Description |
|---|---|---|
| **L0** | Experimental | Disposable prototypes, exploratory code, and experiments not relied on operationally |
| **L1** | Low Risk | Internal utilities, scripts, and noncritical development tools |
| **L2** | Production | Production applications, services, libraries, and infrastructure |
| **L3** | Critical | Software affecting critical operational functions, security, or system availability |
| **L4** | Safety Critical | Software implementing or affecting safety-related functions |

Experimental software must be reassessed before it becomes part of a production or operational workflow. Classification applies to the affected behavior and deployment context, not merely the repository name.

### 4.1 Minimum Review and Verification Expectations 

| Requirement | L0 | L1 | L2 | L3 | L4 |
|---|---|---|---|---|---|
| Accountable human owner | Required | Required | Required | Required | Required |
| PR documentation | Basic | Basic | Standard | Detailed | Detailed |
| Independent human review | Branch policy | Branch policy | Required | Required | Required |
| Automated checks | As applicable | As applicable | Required | Required | Required |
| Design documentation | Optional | As applicable | As applicable | Required | Required |
| Requirements traceability | Optional | Optional | As applicable | Required | Required |
| Formal technical approval | No | No | As applicable | Required | Required |
| Safety-specific verification | No | No | If applicable | If applicable | Required |

Organization-wide branch protection may require independent review for all PRs targeting main, including L0 and L1. Applicable customer, regulatory, safety, cybersecurity, and program requirements take precedence where more restrictive.

## 5. Software Quality Standards

Contributors are expected to:
- Implement the intended behavior with clear, maintainable code and appropriately separated responsibilities.
- Preserve documented interface contracts and avoid unreviewed breaking changes.
- Handle invalid inputs, errors, timeouts, and relevant failure modes explicitly.
- Consider concurrency, resource use, performance, and determinism where relevant to the system.
- Avoid unnecessary complexity, duplication, and dependencies.
- Evaluate new dependencies for security, licensing, maintenance, and deployment compatibility.
- Keep tests and documentation consistent with behavior changes.
- Avoid hardcoded secrets and unauthorized exposure of company or customer information.
Language-specific conventions, tooling, build commands, and architectural rules belong in repository-level documentation and must remain consistent with these standards.

## 6. Testing, Verification, and Validation

Every change must be evaluated using methods appropriate to its risk and intended use. Evidence may include compilation, linting, static analysis, unit or integration tests, simulation, hardware testing, fault injection, requirements-based testing, or system-level testing.

Testing checks observed behavior; verification establishes that specified requirements are met; validation establishes suitability for the intended use. These activities may overlap for routine changes but must be distinguished where required by the system or program.

For significant or critical behavior, expected results and acceptance criteria must be grounded in reviewed requirements, specifications, reference behavior, or other independent engineering evidence. Tests generated by the same AI system that wrote an implementation can be useful, but passing those tests alone does not establish correctness.

Test failures, omitted checks, and known limitations must be disclosed. Contributors must not represent unexecuted tests as passing. Applicable verification evidence must be recorded or linked in the PR.

## 7. Code Review

Code review evaluates engineering quality, not just formatting or whether CI passes. Reviewers should consider:
- Correctness against the intended requirements and acceptance criteria.
- Design clarity, maintainability, and unnecessary complexity.
- Interfaces, dependencies, compatibility, and operational impact.
- Error handling, failure modes, concurrency, and security implications.
- Test quality, coverage of meaningful cases, and limitations of the evidence.
- Documentation and traceability appropriate to the change.
Authors must inspect their own changes before requesting review. Reviewers must be sufficiently qualified to evaluate the affected work and must not approve changes they cannot adequately assess. The author cannot serve as the sole independent reviewer.

For L3 and L4 changes, review and approval must involve the designated technical authorities and personnel with appropriate system expertise. AI-assisted review may supplement, but never replace, required human review.

## 8. AI-Assisted Development

Hypercraft encourages approved AI tools for codebase exploration, design alternatives, implementation, debugging, testing, refactoring, documentation, and review, within the company's authorized information-handling and access boundaries.

### 8.1 Engineering Ownership

The responsible engineer must be able to explain the implementation's intended behavior, key design choices, assumptions, interfaces, and relevant failure modes. AI-generated code is held to the same quality and verification standards as human-authored code.

AI may propose a design or generate substantial implementation work, but it does not independently establish requirements, authorize architectural changes, or approve the result for integration or operational use.

### 8.2 Effective Development Practices

For nontrivial AI-assisted work, engineers should:
1. Establish the problem, constraints, and acceptance criteria before generating substantial implementation code.
2. Use AI to explore alternatives and identify assumptions, then select an engineering approach deliberately.
3. Inspect changes incrementally and keep the result reviewable.
4. Verify behavior against independently established expectations, including negative and failure cases where relevant.
5. Review the final diff, dependencies, tests, and documentation before requesting human review.

One-shot generation is not prohibited for appropriately scoped work. However, the size or speed of AI output does not excuse missing engineering intent, inadequate understanding, or insufficient verification. Large agent-generated changes may be divided into smaller PRs or require additional design review.

### 8.3 Disclosure and Provenance

PRs targeting main must indicate whether AI made a material contribution to the implementation. Routine autocomplete, explanations, and minor suggestions do not require detailed provenance.

For substantial AI-generated or agentic implementations, briefly identify the affected functionality, significant human design decisions or modifications, and how the result was validated. Tool names may be recorded where useful for auditability or required by repository or program rules.

Unverified work is not ready for integration; it is not a separate AI contribution category. Material AI disclosure does not replace ordinary implementation and verification documentation.

### 8.4 Agents and Authorized Access

AI tools and agents must use approved accounts, permissions, data categories, and environments. Repository, terminal, network, credential, deployment, and infrastructure access must follow the Hypercraft Artificial Intelligence Use Policy and applicable security controls.

Agents must not independently execute consequential or irreversible actions without the required authorization. Unattended changes to safety-critical systems, production infrastructure, or security configurations require the documented approvals specified by company policy.

## 9. Documentation and Traceability

Documentation should be proportional to the change's complexity and risk. Significant changes to architecture, APIs, data structures, protocols, deployment behavior, configuration, dependencies, operational assumptions, and failure handling must be documented or linked.

Use the team's approved issue and requirements tracking systems for relevant work items and traceability. For L3 and L4 systems, documentation must support applicable design review, requirements traceability, and verification processes.

Documentation generated with AI must be reviewed for technical accuracy. Do not publish confidential or restricted engineering details in public organization-wide standards repositories.

## 10. Pull Request Requirements

PRs targeting `main` must provide:
1. A concise description of the change and its purpose.
2. Reference to the associated work item or requirement.
3. Significant implementation decisions or impacts, where applicable.
4. The L0–L4 software risk classification.
5. Verification performed, results, and relevant limitations.
6. Links to requirements, issues, or design records where applicable.
7. Disclosure of material AI-generated or agentic implementation, when applicable.
8. Confirmation that the author understands and has reviewed the change.

Required checks and approvals are enforced by the applicable repository and organization rules. PRs targeting other branches may use lighter documentation unless additional requirements apply.

## 11. Security, Operational Adoption, and Ownership

All contributors must comply with the company's cybersecurity, confidentiality, intellectual property, export-control, and AI-use policies. Proprietary code and engineering information may only be processed by tools authorized for the applicable information classification.

Internal applications, automations, manufacturing tools, and other solutions must not enter operational use solely because they were successfully prototyped or merged. Operational adoption requires the appropriate department approval, technical review, and designated operational owner and technical maintainer, consistent with the Hypercraft Artificial Intelligence Use Policy.

## 12. Engineering Authority and Exceptions

Engineering leadership maintains the organization-wide development standard and designates technical approval authorities. Repository maintainers may add controls but may not waive mandatory company requirements on their own.

Exceptions must be documented and approved by authorized engineering leadership before the exception is exercised. Applicable security, quality, manufacturing, program, and regulatory approvals remain in force.

## 13. Continuous Improvement

These standards will be reviewed periodically as engineering needs, development tools, and AI capabilities evolve. Contributors are encouraged to propose improvements based on observed quality, delivery performance, maintainability, and developer experience.

---
**Hypercraft Engineering | Organization-Wide Contribution Standard**
