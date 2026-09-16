# Contributing to Project Documentation

This repository contains the maintained project and product documentation.

The contribution process is designed to preserve project knowledge, maintain a clear history of documentation changes, and prevent conflicting or uncontrolled updates while keeping collaboration lightweight.

## Source of Truth

The `main` branch represents the current accepted state of the documentation.

Documentation may be drafted, discussed, and collaboratively developed using tools appropriate for the team, including Google Docs, Word, Figma, FigJam, issue trackers, and other project collaboration tools.

Once information becomes maintained project documentation, the Markdown version stored in the `main` branch of this repository is authoritative.

Changes made to external working or drafting documents do not automatically constitute changes to the maintained documentation. Relevant updates must be contributed to this repository through the documented contribution workflow.

Git history is used to preserve previous document states. Do not create separate copies such as `document-old.md`, `document-v2.md`, or `document-final.md` for versioning purposes.

## Repository Structure

Documentation is organized according to its purpose rather than its author or team ownership.

```text
requirements/  Business requirements, project scope, and related requirements
concepts/      High-level descriptions of system functionality and behavior
project/       Infrastructure, environments, services, and project maintenance information
user-guide/    Task-oriented documentation for product users
```

Place new documentation according to the primary question it answers:

- **Requirements:** What must the project or product deliver?
- **Concepts:** How does something work?
- **Project documentation:** How is the project or system operated or maintained?
- **User guide:** How does a user accomplish a task?

Avoid duplicating the same information in several documents. Maintain authoritative information in one appropriate location and link to it from related documentation where necessary.

Avoid catch-all directories such as `misc`, `other`, `temp`, or `general`.

## File and Folder Naming

Use lowercase kebab-case for Markdown filenames and directories.

Examples:

```text
authentication.md
business-requirements-and-project-scope.md
services-and-subscriptions.md
media-library/
```

Avoid spaces, underscores, capitalization, and unnecessary numbering.

Use nouns or concise noun phrases for conceptual and reference documentation:

```text
authentication.md
infrastructure.md
environments.md
```

Use concise action-oriented names for user procedures:

```text
sign-in.md
create-news-item.md
upload-image.md
```

Keep filenames reasonably short while ensuring that their purpose remains understandable.

Do not include lifecycle or version metadata in filenames, such as:

```text
authentication-v2.md
authentication-final.md
authentication-approved.md
authentication-2026-09-15.md
```

Git provides the document history and version information.

## Documentation Lifecycle

Do not represent documentation lifecycle states using directories such as `draft`, `review`, `approved`, or `published`.

Git and GitHub represent these states:

```text
Short-lived branch  → work in progress
Pull Request         → proposed/reviewed change
main                 → accepted current documentation
```

There are currently no separate documentation release branches. The project maintains one current documentation version.

## Branching

Do not make routine documentation changes directly on `main`.

Start new work from the latest `main` and create a short-lived branch:

```text
docs/<change-name>
```

Examples:

```text
docs/update-authentication
docs/add-infrastructure-overview
docs/update-business-requirements
```

Keep a branch focused on one logical documentation change whenever practical.

Branches should normally be deleted after their Pull Requests are merged.

## Commits

Commits should represent understandable, logically related documentation changes.

Use concise commit messages describing the change.

For example:

```text
docs: update authentication concept
docs: add media library guide
docs: clarify project scope
```

Avoid combining several unrelated documentation changes into a single commit or Pull Request when they can reasonably be handled separately.

## Pull Requests

All changes to `main` must be introduced through Pull Requests.

A Pull Request should:

- have a clear title describing the documentation change;
- briefly explain what changed and why;
- identify anything requiring particular reviewer attention;
- remain focused on a logical set of related changes.

The repository protects `main` from uncontrolled changes.

## Review Policy

Each Pull Request requires one approval from another project team member before it can be merged.

The author should select a reviewer who can reasonably assess the proposed change based on their knowledge of the affected area.

Members of **BA-team**, **Designers**, and **Experts** are natural reviewer candidates because these teams closely collaborate with the customer and maintain significant project knowledge. Review is not technically restricted to these teams, however. Another project teammate may review a change when appropriate.

Changes requiring specific business, design, or technical expertise should involve a teammate familiar with that subject.

The repository does not currently require approval from specific teams or Code Owners. More restrictive ownership rules may be introduced later if experience demonstrates a need for them.

All review conversations must be resolved before a Pull Request is merged.

If new reviewable changes are pushed after review, the latest state must satisfy the repository's approval requirements.

## Protected `main` Branch

The `main` branch is protected by an active repository ruleset.

The current controls include:

- a Pull Request is required before merging;
- one teammate approval is required;
- approval of the latest reviewable push is required;
- an additional approval is required for unattributed Copilot Pull Requests;
- review conversations must be resolved before merging;
- force pushes are blocked;
- deletion of the protected branch is restricted.

These controls are intentionally lightweight. Every repository restriction should address an identified documentation-management problem rather than add unnecessary process overhead.

## High-Level Contribution Workflow

The documentation contribution process is:

```text
Knowledge or change identified
        ↓
Drafting, discussion, and collaboration
        ↓
Content becomes suitable for maintained documentation
        ↓
Determine the appropriate document and repository location
        ↓
Update local main
        ↓
Create a short-lived docs/... branch
        ↓
Create or update Markdown documentation
        ↓
Review changes locally
        ↓
Commit and push
        ↓
Create a Pull Request
        ↓
Select an appropriate teammate reviewer
        ↓
Review, discussion, and corrections
        ↓
Required approval received
and conversations resolved
        ↓
Merge into main
        ↓
Delete the short-lived branch
        ↓
main contains the current maintained documentation
```

Detailed Git commands and operational instructions are provided in the **Git Documentation Contribution Cheat Sheet**.

## Guiding Principles

Keep the process proportional to the needs of the project.

Use collaborative tools where they make drafting and discussion easier, and use GitHub to maintain the controlled Markdown documentation set and its history.

Prefer simple source-control practices unless additional complexity solves a real project problem.

Keep one authoritative version of maintained information.

Organize documentation according to its purpose rather than its author.

Keep changes focused and traceable.

Use peer review to reduce errors and preserve shared project knowledge.

Treat `main` as the current accepted documentation state.