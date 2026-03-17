# Changelog

All notable changes to the Legal Hive Mind are documented here.

## [v5.0] — 2026-03-17

### Architecture: Dynamic Intake Admin

Complete architectural redesign. The fixed three-partner panel (Strategist, Skeptic, Connector) is replaced with a dynamic Intake Admin that configures itself based on detected domain, jurisdiction, and complexity.

### Added
- **Dynamic Intake Admin** — replaces the Strategist. Configures itself per query using substantive legal expertise. Scopes engagement, derives budget, handles simple matters directly.
- **Engagement Brief** — structured scoping document produced by Intake Admin for every full-pipeline matter. Visible to user for transparency and override.
- **Scope-derived budgets** — budget is determined by jurisdiction surface area × domain complexity, not arbitrary tier labels. Scope → Budget Map provides token estimates per jurisdiction/domain combination.
- **Dynamic spawning** — past base analysis, Skeptic and Connector can request spawned threads (cross-domain synthesis, jurisdiction multiplication, adversarial deep-dives, temporal threads). Intake Admin approves within budget.
- **Soft jurisdiction gate** — direct responses allow general principles with state-variation flags. Full pipeline requires jurisdiction. Multi-state matters capped by budget.
- **Complexity escalation signals** — concrete triggers (contract mentions, opposing parties, deadlines, multi-state facts) that push toward full pipeline regardless of query phrasing.
- **Domain-informed clarifying questions** — Intake Admin asks questions shaped by detected domain expertise, not generic prompts.
- **International placeholder** — architecture leaves room for treaty/cross-border scaffold expansion.
- **Tier 0 direct response demo** (Texas overtime) and **full pipeline demo** (brewery scenario) with Engagement Brief.

### Changed
- Panel reduced from 3 roles (Strategist, Skeptic, Connector) to 2 analytical roles (Skeptic, Connector). Strategist functions absorbed into Intake Admin.
- Budget tiers (Small/Standard/Deep) replaced with continuous scope-derived budgets.
- Fixed tier labels (Tier 0/1/2/3) become emergent from scope — "multi-domain California with federal overlay" not "Tier 2."
- State block restricted to full-pipeline responses only (not direct responses).

### Removed
- Fixed Strategist personality
- Arbitrary tier classifications
- Fixed budget tiers

## [v4.0] — 2025

### Architecture: Three-Partner Panel + Sub-Specialist Escalation

Refined by Hive Synthesis Engine v2.0.

### Added
- Three-partner panel with orthogonal lenses: Strategist, Skeptic, Connector
- Sub-specialist escalation with Strategist cost/benefit approval (one level max)
- Legal framework scaffolds (8 domains with federal framework, state variation traps, ⚠ HIGH VARIATION flags)
- Research protocol gated behind sub-specialist escalation
- Four-layer factual integrity enforcement
- "The One Thing" — every response leads with single most important action
- Explicit `<state>` block for multi-turn context management
- Tiered output format (Tier 1 Focused, Tier 2 Standard, Tier 3 Comprehensive)
- Brewery demonstration scenario

### Changed
- Five partners reduced to three with orthogonal (non-overlapping) lenses
- Panel deliberation changed from simulated debate to telegraphic assessment
- Specialist commission step made invisible (output shows conclusions, not internal routing)
- Tangential domains gated to one-line notes via Strategist cost/benefit

### Removed
- Navigator role (became standard process step)
- Advocate role (absorbed into Strategist calibration)
- Performative panel deliberation
- Unbounded specialist commission

## [v3.0] — 2025

### Added
- Five-partner panel (Strategist, Skeptic, Connector, Navigator, Advocate)
- Expanded specialist roster
- Adversarial review phase
- Anti-hallucination constraints

## [v2.0] — 2025

### Added
- Multi-specialist analysis pipeline
- Jurisdiction awareness
- Confidence markers

## [v1.0] — 2025

### Added
- Initial legal counsel system prompt
- Single-pass analysis
- Basic specialist routing
