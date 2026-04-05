# Accumulation Protocol

Deferred reference. Loaded at Retrospective phase, Deliver phase, or on failure escalation.

Every execution deposits into the knowledge space. The question is not "did it work?" but "what was produced that's reusable?"

---

## Architecture

```
Accumulation Protocol
├── Failure = Data (co-activated with Pressure Escalation)
│   └── Each level extracts elimination data before escalating
├── Retrospective Pipeline (extends inline 4-step → 5-step + accumulate)
│   ├── Steps 1–3: Review goal, Evaluate result, Analyze cause (inline)
│   ├── Step 4: Extract pattern (structured — class + countermeasure)
│   ├── Step 5: Counterfactual check (decision vs. execution lesson)
│   └── Accumulate: deposit per Accumulation Protocol
├── Accumulation Protocol (deposit mechanism)
│   ├── Deposit Types: SOP, elimination record, verified fact, search path
│   └── Threshold: repeatable (2+) AND non-trivial (3+ steps)
├── Persistence Filter (cross-session survival)
│   └── Anti-pattern + Project trap — must be tacit AND durable
└── Information Transparency (Deliver phase — unfiltered decision context)
```

Flow: Execution → failure triggers data extraction → Retrospective formalizes → Protocol deposits → Persistence filters for cross-session survival.

---

## Failure = Data

*Co-activated with Pressure Escalation. Before escalating, answer: "This attempt eliminated _____ and narrowed the solution space to _____."*

| Level | Data Extraction |
|-------|-----------------|
| L1 | Extract: what did L0 attempt eliminate? |
| L2 | Extract: what hypothesis space narrowed by L1? |
| L3 | Carry forward: accumulated elimination map from L0–L2 |
| L4 | Full elimination map informs remaining solution space |

An attempt that produces zero information — not the failure itself — is the actual waste.

---

## Retrospective Pipeline

Extends the inline 4-step Retrospective in SKILL.md to 5-step + accumulate.

| Step | Action | Output |
|------|--------|--------|
| 1–3 | Review goal → Evaluate result → Analyze cause | (unchanged from inline) |
| 4 | Extract pattern (structured) | Class + countermeasure |
| 5 | Counterfactual check | Decision rule or execution note |
| → | Accumulate | Deposit per Accumulation Protocol |

### Step 4 — Structured Extraction

- [What happened] → [Why — structural cause, not surface symptom]
- [What class of problem] → [Reusable output: SOP candidate / heuristic / search path]
- "Be more careful next time" is not a pattern. A pattern names the category and the countermeasure.

### Step 5 — Counterfactual Check

"If I started over, would step 1 be different?"

| Answer | Implication | Extract |
|--------|-------------|---------|
| Yes | Lesson is in the decision, not execution | Decision rule |
| No | Approach correct; cost unavoidable or execution issue | Execution note |

Zero deposits across 3+ consecutive major tasks → review whether extraction is actually happening.

---

## Accumulation Protocol

### Deposit Types

| Type | Example | Reuse Value |
|------|---------|-------------|
| SOP candidate | "For [error class], check [X] before [Y] — saves [N] steps" | Repeatable procedure |
| Elimination record | "For [problem type]: [A, B, C] eliminated. Remaining: [D, E]" | Prevents re-exploration |
| Verified fact | "[Fact] confirmed via [source/tool]. Contradicts assumption [Z]" | Corrects false premises |
| Search path | "For [topic]: [source A] authoritative, [B] outdated, [C] misleading" | Accelerates future search |

### Threshold

Deposit when both conditions met:

| Criterion | Test |
|-----------|------|
| Repeatable | 2+ occurrences likely |
| Non-trivial | 3+ steps to reproduce |

Fails either → do not deposit. Over-accumulation = noise.

### Process

1. **During execution**: tag reusable findings as they appear (don't wait for Retrospective)
2. **At Retrospective step 4–5**: formalize deposits
3. **Filter**: apply threshold before depositing

---

## Persistence Filter

Accumulation deposits are session-scoped by default. Cross-session survival requires passing the filter.

### Survival Criteria

Both must be true:

| Criterion | Test |
|-----------|------|
| Tacit | Would be re-triggered without the record (not obvious from code/docs) |
| Durable | Still valid across sessions (not temporary state) |

Fails either → session-scoped deposit is sufficient.

### Persistent Deposit Types

| Type | Content | Format |
|------|---------|--------|
| Anti-pattern | Behavioral — mistake made + correct approach | `[date] [context] trap: ___ → lesson: ___` |
| Project trap | Environmental — project/tool-specific pitfall | `[context] pitfall: ___ → correct approach: ___` |

### Load Timing

On session start in same project directory → load as Accept-phase pre-context (parallel to cognitive briefing).

### Storage

Infrastructure decision — user's memory system, CLAUDE.md, or external state file. Protocol defines *what* and *format*, not *where*.

---

## Information Transparency

*Deliver-phase principle. Co-activated with delivery gates.*

All decision-relevant information presented unfiltered — what was tried, what was ruled out, what risks remain, what assumptions hold. The user's next decision depends on information completeness. Filtering complexity = degrading decision quality downstream.

---

## Anti-Patterns

| Pattern | Problem |
|---------|---------|
| "Fixed the bug." — no extraction | One-time consumption. Zero accumulation. Fix dies with session. |
| "Tried X, didn't work." — no elimination record | Violates Failure = Data. Next attempt may re-explore X. |
| Every 2-line fix gets SOP treatment | Over-accumulation noise. Threshold exists for a reason. |
| Vague lessons ("be careful with configs") | Not actionable. Valid deposit names class, trigger, countermeasure. |
