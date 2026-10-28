# AI-Assisted Software Development Guide

Hypercraft Engineering | Organization-Wide Guidance

## 1. Purpose and Scope

Hypercraft encourages engineers to use approved AI tools to accelerate research, design, implementation, debugging, testing, and documentation. AI is an engineering aid, not a substitute for engineering judgment.

This guide describes recommended development practices for employees and authorized contributors. It supplements CONTRIBUTING.md and the Hypercraft Artificial Intelligence Use Policy. The corporate policy governs approved tools, data handling, access permissions, and operational authorization; applicable engineering and security requirements always take precedence.

**Core principle:** AI may implement a solution, but a responsible engineer must establish its intent, understand its behavior, and demonstrate that it meets applicable requirements.

## 2. Engineering Ownership

The engineer responsible for a change must be able to explain:
- The problem, intended behavior, and acceptance criteria.
- The chosen design and meaningful alternatives or tradeoffs.
- Interfaces, dependencies, assumptions, and relevant failure modes.
- How the implementation was verified and what remains unverified.
  
AI-generated code is held to the same quality, security, review, and verification standards as human-authored code. Passing compilation, AI-generated tests, or AI review alone does not establish correctness. Required independent human review cannot be replaced by AI review.

## 3. Start With a Work Item

Substantive development should begin with a documented work item in a company-approved tracking system. A work item may represent a feature, defect, enhancement, refactor, maintenance task, or other engineering objective.

Before substantial implementation, establish as appropriate:
- **Outcome:** What problem is being solved and why?
- **Scope:** What behavior, interfaces, or components may change?
- **Acceptance criteria:** What observable conditions demonstrate success?
- **Constraints:** Performance, safety, security, compatibility, deployment, and operational requirements.
- **Verification approach:** How will the result be evaluated independently of its implementation?
  
A brief work item may suffice for routine changes. Significant changes should have an implementation plan or design record, which may be linked from the work item. Pull requests targeting main should reference the applicable work item or requirement, subject to documented exceptions for minor administrative changes.

## 4. Choose the Appropriate Workflow

Use the development workflow defined in CONTRIBUTING.md, based on complexity, impact, and risk. The L0–L4 software risk classification remains separate from the amount of AI involvement.

| Workflow | Typical work | Expected approach |
|---|---|---|
| **Routine** | Small fixes, isolated refactors, straightforward utilities | Understand, implement, inspect, test, review. |
| **Structured** | New features, interfaces, multi-component changes, significant refactors | Define acceptance criteria, review a plan, implement in increments, verify, review. |
| **Controlled** | Safety-related or other critical functions | Follow applicable requirements, design, verification, approval, and change-control processes. |

A small change can still be high risk. A complex change can be low risk. Neither AI use nor change size alone determines the required controls.

## 5. Recommended AI Development Loop

### 5.1 Explore

Use AI to understand unfamiliar code, map dependencies, identify relevant interfaces, and suggest questions to investigate. Verify consequential claims against source code, specifications, and authoritative documentation.

### 5.2 Plan

For nontrivial work, ask AI to propose an approach, alternatives, and risks before generating substantial implementation code. The engineer evaluates and selects the approach. Record significant design decisions in the work item or design documentation.

### 5.3 Implement

Use AI for code generation, refactoring, test scaffolding, and debugging as appropriate. Prefer coherent, reviewable increments. Inspect diffs as work progresses and correct the approach when it diverges from requirements. Avoid accepting broad unrelated rewrites or unnecessary dependencies simply because an agent produced them.

One-shot generation is not prohibited. The relevant question is whether the resulting change is understood, appropriately scoped, and adequately verified.

### 5.4 Verify

Check behavior against acceptance criteria and independent expectations. Run applicable builds, linters, static analysis, tests, simulation, hardware-in-the-loop tests, or system-level checks. Investigate failures instead of repeatedly prompting until a test turns green.

### 5.5 Review and Integrate

Review the complete diff, document meaningful decisions and verification evidence, identify known limitations, and submit a PR under the applicable review requirements. Material AI-generated implementation must be disclosed in the PR as required by the contribution standard.

## 6. Testing AI-Assisted Changes

AI may write tests, but tests should be derived from requirements, established contracts, known invariants, defect reproductions, or independently reviewed expected behavior. Avoid relying exclusively on tests invented from the generated implementation itself.

For meaningful changes, consider:
- Normal operation, boundaries, invalid inputs, and error paths.
- State transitions, timeouts, retries, recovery, and degraded operation.
- Concurrency, resource limits, and performance where relevant.
- Backward compatibility of APIs, schemas, configurations, and persistent data.
- Security implications and dependency or license changes.
- Regression cases that demonstrate the original defect is fixed.
  
For critical functions, apply the required requirements-based verification, simulation, fault injection, independent review, and system validation processes. Do not infer safety or production readiness from passing unit tests alone.

## 7. Agentic Development and Tool Permissions

AI agents that can edit files, run commands, access repositories, retrieve data, or interact with external systems must operate within explicitly authorized permissions and approved information-handling boundaries.
- Use least-privilege access and approved credentials.
- Review commands and changes with potentially destructive, external, or irreversible effects before execution.
- Do not grant unapproved access to confidential or restricted information, secrets, production systems, or deployment credentials.
- Keep changes and verification results traceable through normal development systems.
- Do not permit unattended autonomous changes to safety-critical systems, production infrastructure, or security configurations except through an explicitly approved process.

Local models and paid enterprise subscriptions are not automatically authorized for restricted or regulated data. Follow the corporate AI policy for tool approval, information classification, and export-controlled or customer-restricted information.

## 8. Examples
### Good: AI-Assisted Feature Development
An engineer defines a new configuration-validation feature with acceptance criteria, reviews a proposed design, uses an agent to implement the parser and tests, checks compatibility and failure handling, runs the relevant CI suite, and submits a focused PR explaining verification and limitations.
### Poor: Unreviewed One-Shot Implementation
An engineer asks an agent to build a new service, accepts a large generated diff, relies only on the agent's own tests, and merges without understanding error handling, interfaces, or operational behavior.
### Good: Fast Routine Change
An engineer asks AI to fix a small, isolated bug, inspects the diff, runs a regression test, and submits a short PR. No formal design document is needed solely because AI was used.
### Critical Change: Controlled Process Still Applies
An engineer uses AI to explore a vehicle-control fault-handling change. Requirements, intended transitions, and failure responses are reviewed by qualified personnel before implementation. The resulting code undergoes applicable independent verification and authorized approval regardless of how much was generated by AI.

## 9. Pull Request Expectations

PRs targeting `main` follow the organization-wide template and applicable repository rules. The PR should communicate:

1. What changed and why, with a linked work item or requirement.
2. Significant implementation decisions and any breaking changes.
3. Software risk classification (L0–L4).
4. Verification performed and known limitations.
5. Material AI contribution details when applicable.
6. The author's confirmation of understanding and readiness for independent review.

Routine autocomplete, explanations, and minor suggestions do not require detailed AI provenance. Disclosure does not reduce or increase the underlying engineering quality requirements.

## 10. Reviewer Guidance

Reviewers should assess correctness, clarity, maintainability, interfaces, dependencies, failure behavior, security, tests, and consistency with intended requirements. For substantial generated changes, pay particular attention to assumptions, unnecessary complexity, unsupported APIs, fabricated behavior, and tests that mirror implementation mistakes.

Reviewers may use AI to identify concerns, but must independently evaluate the change. If the reviewer cannot adequately assess a change, request clarification, smaller increments, additional evidence, or an appropriately qualified reviewer.

## 11. Continuous Improvement

AI tools and engineering practices will evolve. Teams should evaluate whether AI improves delivery speed and quality using indicators such as lead time, review burden, regressions, rework, test reliability, and developer experience. Do not use AI-generated line counts or prompt volume as proxies for engineering performance.

Engineers are encouraged to share effective workflows, recurring failure patterns, and improvements to repository-specific agent instructions. Updates to this guide follow the engineering governance process in CONTRIBUTING.md.

--- 
Related documents: CONTRIBUTING.md · Hypercraft Artificial Intelligence Use Policy · Repository-specific engineering and agent instructions
