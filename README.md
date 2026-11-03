# Hypercraft GitHub Configuration

Organization-wide GitHub defaults for Hypercraft repositories: the contribution guide, the pull request template, and the shared PR validation workflow.

This repository is **not** where engineering standards are maintained. Hypercraft staff and contractors can find them in the internal [engineering-standards](https://github.com/hypercraftusa/engineering-standards) repository. That link needs org access. If anything here conflicts with that repository, the standards repository wins.

## Contents

| File | Purpose |
| --- | --- |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Quick guide to contributing to Hypercraft repositories |
| [.github/pull_request_template.md](.github/pull_request_template.md) | Default PR template for repositories that don't define their own |
| [.github/workflows/pr-validation.yml](.github/workflows/pr-validation.yml) | Reusable workflow that checks PRs to `main` for required template fields |

## Pull requests

**PRs to `main`** must complete the PR template:

- Summary and linked work item
- Software risk classification (L0–L3)
- Implementation notes and any breaking changes
- Verification performed and known limitations
- Disclosure of material AI contribution, with details of how it was reviewed and validated
- Author declaration

The `pr-validation` workflow checks that these fields are filled in. It checks completeness, not quality. Human review is still required.

**PRs to other branches** need only a summary unless the repository requires more.

Merging into `main` does not authorize deployment or release. Those follow separate approvals.

Repository-specific templates and checks may add requirements but may not remove these.

## Changes and exceptions

Changes to this repository and exceptions to the PR requirements must be approved by Hypercraft engineering leadership.

## Information security

This repository is public because GitHub requires it for organization-wide community health files. Do not add confidential engineering information, proprietary source code, restricted technical data, customer or program details, or internal security procedures here.

