# ZFordDev Ecosystem Standards

> **Version 1.1.0**  
> **Reviewed:** 2026‑06‑09

---

The ZFordDev ecosystem is built around a simple idea:

**Good projects are easier to maintain when they share a common foundation.**

These standards exist to keep repositories consistent, predictable, and easy to work with—whether a project is maintained by one person or eventually grows into a community effort.

The goal is not to create bureaucracy or enforce unnecessary rules. Instead, these standards focus on the things that improve clarity, reduce friction, and make development more enjoyable.

A ZFordDev Standard should always be:

* Simple and easy to adopt
* Useful across all projects
* Language-agnostic whenever possible
* Focused on developer experience
* Lightweight rather than restrictive
* Worth maintaining long-term

Standards will evolve as the ecosystem grows. Some are already implemented across all repositories, while others are planned for future adoption.

---

# Scope

These standards apply to all repositories under the ZFordDev identity.  
Organizations such as SnapDockStudio and StaxDash may define additional standards, but they should extend—not contradict—the root standards defined here.

---

# Implemented Standards

## Temp Notes Standard

Every repository includes a `temp_notes.md` file in the project root.

Development often involves quick ideas, debugging notes, half-finished thoughts, and temporary planning. Rather than scattering those notes across text files, sticky notes, or random documents, every ZFordDev project provides a dedicated place for them.

The `temp_notes.md` file:

* Lives in the repository root
* Is ignored by Git
* Will never be committed
* Provides a consistent scratchpad across all projects

This was the first ecosystem-wide standard and remains one of the most useful.

---

## Repository Hygiene Standard

Every repository should begin with a predictable baseline structure.

Expected files include:

```text
.github/
├── CODEOWNERS
└── FUNDING.yml

.gitignore
LICENSE
README.md
temp_notes.md
```

By keeping these essentials consistent, contributors can move between repositories without needing to relearn project structure each time.

---

## Documentation Structure Standard

Documentation should be approachable, organized, and easy to navigate.

At a minimum, repositories should provide a clear `README.md`. Additional documentation may be placed in dedicated files as projects grow.

Common documentation files include:

```text
README.md
docs/
ARCHITECTURE.md
ROADMAP.md
CHANGELOG.md
```

Not every project needs every file, but the structure should remain familiar across the ecosystem.

---

## Commit Message Standard

Commit history should tell a story.

To keep commit logs readable and searchable, repositories are encouraged to use a consistent commit format:

```text
feat: add plugin manager
fix: resolve startup crash
docs: update installation guide
chore: remove unused assets
refactor: split updater into modules
build: update dependency versions
ci: add release workflow
```

Supported prefixes:

* `feat:` — New features
* `fix:` — Bug fixes
* `docs:` — Documentation changes
* `chore:` — Maintenance and cleanup
* `refactor:` — Internal code restructuring
* `build:` — Build system or dependency updates
* `ci:` — Continuous integration changes

The objective is consistency, not perfection.

---

## Versioning Standard

Versioned projects should follow Semantic Versioning (SemVer).

This includes:

* Tagged releases
* Release notes
* Predictable version progression
* Clear communication of changes

Example:

```text
1.0.0 → Initial stable release
1.1.0 → New features added
1.1.1 → Bug fixes
2.0.0 → Breaking changes
```

Consistent versioning helps both users and contributors understand the maturity of a project.

---

## Contribution Standard

As projects mature and attract contributors, repositories should provide clear guidance on how to participate.

Future repositories may include:

```text
CONTRIBUTING.md
.github/ISSUE_TEMPLATE/
.github/PULL_REQUEST_TEMPLATE.md
```

The goal is to make contributing straightforward without overwhelming newcomers with process.

---

## Security & Vulnerability Standard

Every repository should provide a `SECURITY.md` file explaining:

* How vulnerabilities can be reported
* Expected response times
* Disclosure expectations
* Any project-specific security considerations

Responsible disclosure benefits both maintainers and users and helps build trust within the ecosystem.

---

# Planned Standards

The following standards have been defined and approved but may not yet be implemented across every repository.

---

## Merge & Review Discipline Standard *(New)*

Solo‑maintained repositories carry a unique risk: the maintainer has full authority over development, review, and release. Without counter‑pressure, rushed decisions or time‑compressed work windows can lead to broken functionality being merged into `main`.

To mitigate this, all ZFordDev repositories adopt a lightweight but strict merge discipline designed to simulate the safeguards of a multi‑developer team.

---

### Cooling Period Rule

No pull request may be merged into `main` within **24 hours** of its creation.

This delay provides:

* A mental reset between writing and reviewing code  
* A fresh perspective that catches mistakes missed during implementation  
* A buffer against time‑pressure merges (e.g., end‑of‑session pushes)  
* A simulated “second reviewer” effect for solo developers  

The cooling period applies to all PRs, regardless of size or urgency, except for emergency hotfixes (see below).

---

### Full‑Functionality Testing Requirement

Before any PR is approved for merge, the entire application must be tested in an isolated environment.

Testing must verify:

* Core navigation  
* All major user flows  
* Form submissions and validation  
* State management and data persistence  
* Build output and runtime behaviour  
* Mobile and responsive behaviour (if applicable)  
* Any logic adjacent to the modified code  

This ensures that style rewrites, refactors, or isolated fixes do not unintentionally break unrelated functionality.

Testing is not limited to the area changed — it covers the **entire app**.

---

### No End‑of‑Window Merges

Pull requests may **not** be merged at the end of a work window.

If a session is ending (e.g., early‑morning development before work), the PR must be left unmerged until the next session. This prevents rushed decisions caused by hard time cutoffs.

If the clock is the reason to merge, the merge must not happen.

---

### Staging Branch Requirement

All work must be merged into a **staging** branch before reaching `main`.

Flow:

```
feature → staging → (24h delay + full testing) → main
```

The `main` branch must always represent a stable, production‑ready state.

---

### Emergency Hotfix Protocol

In rare cases where a critical issue must be resolved immediately:

* A hotfix branch may be created  
* The fix must be isolated to the smallest possible change  
* Full‑functionality testing is still required  
* The cooling period may be bypassed only for the hotfix PR  
* A post‑mortem note should be added to `temp_notes.md`  

Hotfixes are exceptions, not workflow shortcuts.

---

### Purpose of This Standard

This standard exists to:

* Protect `main` from rushed or emotionally driven merges  
* Provide structure for solo maintainers  
* Reduce the risk of regressions during refactors or rewrites  
* Maintain user trust and ecosystem stability  
* Replace missing team review with process‑based safeguards  

It is intentionally lightweight, but strict where it matters.

---

# Non-Standards

Not everything needs to be standardized.

Some areas are intentionally left to the individual project.

## Coding Style

ZFordDev does not enforce a universal coding style.

Different languages already have established conventions and formatting tools. Projects are free to adopt the standards that make the most sense for their technology stack.

Examples include:

```text
Rust       → rustfmt
Python     → black
JavaScript → prettier
```

The ecosystem values consistency within a project more than consistency across unrelated languages.

---

# Future Expansion

As the ecosystem grows, additional standards may emerge.

Potential areas include:

* SnapDockStudio organization standards
* StaxDash organization standards
* Documentation tooling
* Repository automation
* Release workflows
* Testing practices
* Development environment standards

Any future standard should continue to follow the same philosophy:

> Keep it simple. Make it useful. Avoid unnecessary process.

---

# Final Notes

These standards are intended to provide a shared foundation across the ZFordDev ecosystem.
They are not rules for the sake of rules. They exist to make projects easier to understand, easier to maintain, and easier to contribute to.
Unless explicitly overridden by a repository, these standards serve as the default expectations for all current and future ZFordDev projects.
Standards may be updated as the ecosystem evolves.

---
