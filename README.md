# PUA — High-Agency Problem-Solving Skill

Simplified and restructured version of [tanweai/pua](https://github.com/tanweai/pua).

Claude Code skill that enforces exhaustive, evidence-based problem solving. Manual activation only: `/pua`.

## Structure

```
pua/
  SKILL.md                              # Main skill file (EN)
  references/
    space-grade-cognitive.md            # Load on activation — cognitive briefing
    verification-gates.md              # Load on phase entry — gates + 7-item checklist
    accumulation-protocol.md             # Load on phase entry — retrospective + failure=data
  zh_tw/                                # Traditional Chinese mirror
    SKILL.md
    references/
      space-grade-cognitive.md
      verification-gates.md
      accumulation-protocol.md
```

## Loading

Model reads referenced files using Read tool at the specified trigger point.

- On skill activation: `space-grade-cognitive.md` — cognitive briefing before procedure
- On phase entry: `verification-gates.md` at Execute/Deliver/L3+; `accumulation-protocol.md` at Retrospective/Deliver or failure escalation

## SKILL.md Sections

| Section | Role |
|---------|------|
| Three Red Lines | Non-negotiable constraints: close the loop, fact-driven, exhaust everything |
| Execution Architecture | Backbone map — Task Lifecycle as spine, mechanisms tagged to phases |
| Strategy Router | Task type → strategy + primary gates mapping (R1–R8) |
| Functional Constraints | 6 structural constraints (T1–T6) activated on failure or evasion |
| Pressure Escalation (L0–L4) | Failure-driven depth — failure count drives mandatory actions |
| Failure Mode Response | 10-row signal → constraint → pressure mapping |
| Task Lifecycle | Accept → Execute → Deliver → Retrospective |
| Resource Allocation | Uncertainty-driven breadth — Explore/Concentrate with DCP; orthogonal to Pressure Escalation |
| Sub-agent Injection | Protocol for spawning constrained sub-agents |
| Anti-Patterns | Behaviors outside the boundary — detected in real usage |
| Dignified Exit | Structured failure report when L4 + 7-item checklist exhausted |

## References

| File | Content |
|------|---------|
| `space-grade-cognitive.md` | First principles, situational awareness (up & out), compression test, bias for action, decision context |
| `verification-gates.md` | 7-item checklist, Blue Army, Reward Hack, End-to-End Control, Keeper Test, Grayscale Deployment, End-User Perspective, Difficulty Reporting |
| `accumulation-protocol.md` | 5-step retrospective, failure=data co-activation, accumulation protocol, cross-session persistence |
