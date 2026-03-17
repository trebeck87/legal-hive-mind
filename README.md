# Legal Hive Mind

A hierarchical adversarial legal counsel system for Claude. Every matter enters through a dynamic **Intake Admin** with substantive legal expertise that scopes the engagement, derives the budget from jurisdiction and domain complexity, handles simple questions directly, and activates the full analytical pipeline only when scope warrants it.

> **This is not legal advice.** The Legal Hive Mind provides legal *information* through structured analysis. It distinguishes information from advice, flags when licensed counsel is essential, and never fabricates citations or legal authorities.

## Installation

Download `hive-legal-advisory.skill` from the [latest release](../../releases) and install it in your Claude environment, or clone the repo and point your skill loader at the `SKILL.md` file.

```
legal-hive-mind/
├── SKILL.md                              # Core skill (522 lines)
├── references/
│   └── legal-framework-scaffolds.md      # Multi-state scaffolds (96 lines)
└── hive-legal-advisory.skill             # Packaged installer
```

## Architecture

```
Query
  │
  ▼
┌─────────────────────────────────────────┐
│           INTAKE ADMIN                  │
│  Dynamic role — configures itself based  │
│  on detected domain, jurisdiction, and   │
│  complexity. Substantive legal expertise  │
│  shapes scoping questions.               │
│                                         │
│  ┌─────────────┐  ┌──────────────────┐  │
│  │ Scope       │  │ Budget Derivation│  │
│  │ Detection   │──│ Jurisdiction ×   │  │
│  │             │  │ Domain = Budget  │  │
│  └─────────────┘  └──────────────────┘  │
│                                         │
│  Simple matter? ──YES──► Direct Response │
│       │                                 │
│       NO                                │
│       │                                 │
│       ▼                                 │
│  Engagement Brief (visible to user)     │
└─────────────────────────────────────────┘
  │
  ▼
┌─────────────────────────────────────────┐
│         ANALYTICAL PANEL                │
│                                         │
│  SKEPTIC          │  CONNECTOR          │
│  Worst-case       │  Non-obvious        │
│  Weakest          │  domains            │
│  assumption       │  Cross-domain       │
│  Hallucination    │  interactions       │
│  watchdog         │  Spawn requests     │
│  Spawn requests   │                     │
└─────────────────────────────────────────┘
  │
  ▼
┌─────────────────────────────────────────┐
│         SPECIALIST ANALYSIS             │
│  Commissioned per Engagement Brief      │
│  Sub-specialist escalation (1 level)    │
│  [VERIFY] flags for uncertain law       │
│                                         │
│  If budget permits:                     │
│  ┌────────────────────────────────────┐ │
│  │ SPAWNED THREADS                    │ │
│  │ • Cross-domain synthesis           │ │
│  │ • Jurisdiction multiplication      │ │
│  │ • Adversarial deep-dives           │ │
│  │ • Temporal threads                 │ │
│  └────────────────────────────────────┘ │
└─────────────────────────────────────────┘
  │
  ▼
┌─────────────────────────────────────────┐
│       ADVERSARIAL REVIEW                │
│  1. Hallucination check (first)         │
│  2. Missing practice areas              │
│  3. Weakest conclusions                 │
│  4. Jurisdiction assumptions            │
│  5. Spawn reconciliation               │
│  Revise before delivery.                │
└─────────────────────────────────────────┘
  │
  ▼
  Delivery (One Thing first)
```

## Key Design Decisions

### Dynamic Intake Admin (not a fixed Strategist)

The Intake Admin configures itself based on the detected domain. An employment intake asks about employee count, salary/hourly status, and state — because those determine which frameworks apply. A real estate intake asks about lease terms, property type, and sale timeline. The legal knowledge shapes the scoping, not a generic triage checklist.

### Budget Derives from Scope

Budget isn't an arbitrary tier. It derives from **jurisdiction surface area × domain complexity**:

| Jurisdiction | Single Domain | Multi-Domain (2–3) | Multi-Domain (4+) |
|---|---|---|---|
| Single state | ~800–1,200 | ~2,000–3,000 | ~3,000–4,000 |
| Multi-state (2–3) | ~1,500–2,500 | ~3,000–5,000 | ~5,000–7,000 |
| Multi-state (4+) | ~2,500–3,500 | ~5,000–8,000+ | ~8,000+ |

Federal overlay adds ~500–1,000 tokens. International is ~4,000+ minimum (placeholder for future expansion).

### Dynamic Spawning

Past the base analysis, the Skeptic and Connector can request spawned threads for cross-domain synthesis, jurisdiction multiplication, adversarial deep-dives, or temporal analysis. The Intake Admin approves or denies based on budget and allocates proportionally.

### Four-Layer Anti-Hallucination

1. **Top-level absolute constraint** — NEVER fabricate citations
2. **Specialist `[VERIFY]` flags** — mark jurisdiction-uncertain principles
3. **Adversarial review hallucination check** — runs first, before all other review questions
4. **Skeptic as hallucination watchdog** — flags assertions resting on uncertain authority

### Soft Jurisdiction Gate

Direct responses allow general principles with a "may vary by state" flag. Full pipeline requires jurisdiction before analysis. Multi-state matters get capped by budget — no open-ended analysis across all 50 states.

## Scaffolds

The `references/legal-framework-scaffolds.md` file provides structural orientation for sub-specialist escalation across 8 domains:

1. Business / Corporate / Contracts
2. Real Estate / Landlord-Tenant
3. Employment / Labor
4. IP / Technology / Data Privacy
5. Regulatory / Compliance
6. Litigation / Disputes
7. Tax / Financial Planning
8. Personal / Family

Each scaffold covers federal framework, state variation traps, and a ⚠ HIGH VARIATION flag for the most dangerous jurisdiction-specific trap in that domain. Scaffolds are only consulted during sub-specialist escalation — they're inert on simple queries.

## Customization

| Lever | Effect |
|---|---|
| `default_jurisdiction` | Skip jurisdiction questions |
| `default_budget_floor` | Set to `deep` for high-stakes deployments |
| Cap escalation | Require explicit user request for sub-specialist depth |
| Narrow scaffolds | Remove unneeded domains (~150 tokens saved each) |
| Promote scaffolds | Let primary specialists consult them directly |
| Move to retrieval | Store scaffolds externally, inject on escalation |
| Strengthen citations | Describe principles for Westlaw/LexisNexis lookup |
| International scaffolds | Add treaty frameworks (future) |

## Lineage

Built with the [Hive Synthesis Engine](https://github.com/placeholder/hive-synthesis-engine) — a multi-agent prompt generation pipeline. The Legal Hive Mind originated as a v1 system prompt, evolved through v2–v3 with expanding specialist rosters and adversarial review, and reached v4 with the three-partner panel architecture. The current version replaces the fixed Strategist role with the dynamic Intake Admin and introduces scope-derived budgets with dynamic spawning.

## License

Apache 2.0 — see [LICENSE](LICENSE).

## Disclaimer

The Legal Hive Mind provides legal **information**, not legal **advice**. It is not a substitute for licensed legal counsel. Do not act on its output alone for matters involving active litigation, regulatory investigations, criminal exposure, material transactions, or any situation involving liberty, livelihood, or substantial assets. Always consult a licensed attorney in your jurisdiction.
