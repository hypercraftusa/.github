# Hypercraft Engineering Standards

This repository maintains organization-wide GitHub configuration, software development standards, and contribution guidelines for Hypercraft.

## Purpose

Establish consistent engineering practices across all Hypercraft repositories while promoting software quality, technical accountability, security, and responsible use of AI-assisted development tools.

These standards apply to all employees, contractors, and contributors working within Hypercraft-managed repositories.

## Repository Contents

| File | Purpose |
|---|---|
| `.github/pull_request_template.md` | Standardized pull request documentation and classification |
| `CONTRIBUTING.md` | Organization-wide development and contribution guidelines |
| `README.md` | Repository purpose and governance |

Additional shared configurations and engineering standards may be introduced as needed.

## Engineering Principles

Hypercraft's software development practices are founded on the following principles:

1. **Human Accountability:** Every software change must have an identifiable human owner responsible for its correctness and implementation.
2. **Risk-Based Engineering:** Review, testing, documentation, and approval requirements must be proportional to software criticality.
3. **AI Transparency:** Material AI contributions must be disclosed and traceable through the development lifecycle.
4. **Technical Integrity:** All production code must be understood, appropriately reviewed, and verified before integration.
5. **Security by Design:** Software development must follow applicable cybersecurity, information protection, and access-control requirements.
6. **Engineering Authority:** Technical approvals and exceptions must be granted by designated engineering authorities.

## Organization-Wide Requirements

All Hypercraft repositories must comply with the company's engineering and software development standards.

### Pull Requests

Hypercraft uses a standardized pull request process to maintain software quality, engineering accountability, and traceability.

**Development Branches**

Pull requests targeting branches other than `main` are intended to support iterative development, collaboration, and experimentation.

Completion of the organization-wide pull request template is optional for these changes unless additional repository-specific requirements apply.

Engineers are encouraged to document significant changes, AI involvement, and relevant testing throughout development.

**Main Branch**

All pull requests targeting `main` must satisfy the organization's engineering documentation and verification requirements.

Required information includes:

- Software risk classification (L0–L4).
- AI contribution classification (AI-0 through AI-4).
- Summary of changes and implementation details.
- Disclosure of material AI-generated contributions.
- Appropriate verification and testing evidence.
- Relevant documentation and requirements references.
- Author acknowledgment of implementation ownership and validation.

Pull requests that do not satisfy these requirements will be blocked from merging through automated validation.

**Enforcement**

Organization-level repository rulesets and required status checks enforce the pull request standard for protected branches.

Repository-specific templates may not weaken or bypass mandatory organization-wide requirements.

Additional review and verification requirements may apply to safety-critical, security-critical, or otherwise restricted software.

Merging into `main` does not independently constitute authorization for production deployment or release.


## Governance

Engineering leadership maintains authority over organization-wide development standards, required reviews, and technical approval processes.

Changes to these standards must be reviewed and approved by authorized Engineering leadership.

Exceptions must be documented and explicitly approved before implementation.

## Information Security

This repository is public to support GitHub's organization-wide community health file functionality.

Confidential engineering information, proprietary source code, restricted technical data, and internal security procedures must not be stored in this repository.

Detailed internal engineering policies and procedures are maintained in appropriately access-controlled company systems.

---

**Hypercraft Engineering | Organization-Wide Development Standards**
