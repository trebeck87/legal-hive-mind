# Contributing to Legal Hive Mind

Thanks for your interest in improving the Legal Hive Mind. This is a prompt engineering project — contributions are primarily skill refinements, scaffold expansions, demonstrations, and test cases rather than traditional code.

## How to Contribute

### Reporting Issues

If the Hive Mind produces incorrect legal analysis, fabricates citations, misroutes a query, or behaves unexpectedly, open an issue with:

- The query you asked (sanitize any personal details)
- What the system did vs. what you expected
- Which component misbehaved (Intake Admin scoping, Skeptic risk assessment, Connector domain detection, specialist analysis, adversarial review, etc.)

### Suggesting Improvements

The [improvement roadmap](https://github.com/placeholder/legal-hive-mind/issues) tracks prioritized tasks. High-impact areas:

- **Demonstrations** — the skill needs more worked examples across different tiers, calibrations, and edge cases
- **Scaffold expansion** — Media/Entertainment, Public Law, Cross-Cutting (Conflict of Laws), and international scaffolds are missing
- **Testing** — hallucination audits, tier boundary testing, multi-turn continuity, calibration accuracy
- **Architecture refinements** — Intake Admin decision criteria, spawn thread integration, budget derivation tuning

### Pull Request Process

1. Fork the repo
2. Make changes on a feature branch
3. Test your changes against real queries where possible — describe the test scenarios in the PR
4. Submit a PR with a clear description of what changed and why

For SKILL.md changes, note:
- Keep the description frontmatter under 1024 characters
- Target ~500 lines for SKILL.md (currently 522, with headroom to ~550)
- New demonstrations are always welcome — they're the highest-leverage improvement
- Behavioral changes should include a rationale tied to a specific failure mode

For scaffold changes:
- Follow the existing structure: Federal framework → State variation traps → ⚠ HIGH VARIATION flag
- Each domain scaffold should be self-contained
- Include a ToC entry in the reference file header

## Architecture Principles

When contributing, keep these design principles in mind:

**Scope drives depth.** Budget derives from jurisdiction × domain complexity. Don't reintroduce arbitrary tier labels.

**The Intake Admin is dynamic, not a personality.** It configures itself based on detected domain. Contributions should enhance domain-specific scoping behavior, not add character traits.

**Demonstrations > instructions.** Showing Claude correct behavior in a worked example is more effective than adding another bullet to a constraint list. Prefer adding a demo over adding a rule.

**Factual integrity is non-negotiable.** The four-layer anti-hallucination system (top-level constraint, specialist [VERIFY] flags, adversarial review hallucination check, Skeptic watchdog) exists because people act on legal information. Never weaken these constraints.

**Progressive disclosure.** Scaffolds live in reference files and only load during sub-specialist escalation. Don't pull reference material into SKILL.md unless it needs to be always-on.

## Legal Note

This project provides legal *information*, not legal *advice*. Contributions should maintain this distinction throughout. Never frame the system's output as a substitute for licensed counsel.

## License

By contributing, you agree that your contributions will be licensed under the Apache License 2.0.
