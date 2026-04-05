# Verification Gates

Gate specifications for quality enforcement. Each gate has trigger, operation, pass/fail criteria.

Deferred reference — loaded at Execute, Deliver, or L3+.

---

## 7-Item Checklist (L3+ mandatory)

Every item requires inline evidence — not a checkmark, proof.

```
- [ ] Read the failure signal word by word?
      └─ Key signal: ___ Interpretation: ___

- [ ] Searched core problem with tools?
      └─ Searched: ___ Result summary (1 line): ___

- [ ] Read raw context around the failure location?
      └─ File:line read: ___ Relevant finding: ___

- [ ] All assumptions verified with tools?
      └─ Assumption: ___ Verification command: ___ Result: ___

- [ ] Tried the completely opposite hypothesis?
      └─ Original hypothesis: ___ Inverted: ___ Outcome: ___

- [ ] Can reproduce in minimal scope?
      └─ Minimal repro: ___ Output: ___

- [ ] Switched tool / method / angle / tech stack?
      └─ Previous: ___ Switched to: ___ Rationale: ___
```

---

## Blue Army Self-Check

**Trigger:** Before implementing any solution.

**Operation:**
1. 30 seconds as your own adversary
2. Where will this most likely break?
3. Edge cases? Abnormal inputs?
4. Invisible path coverage: error handling paths, untested code branches, edge cases users won't trigger directly

Compromising where nobody looks leads to compromising where everybody looks.

**Pass:** At least one potential failure point identified and addressed.
**Fail:** Implementation without self-attack — flag at review.

#### Post-delivery resilience (chaos engineering variant)
- **Trigger**: After Deliver phase, on complex or high-stakes outputs
- **Operation**: Deliberately inject edge cases, malformed inputs, boundary conditions into the delivered solution. Test: does it handle gracefully or break silently?
- **Pass**: Output degrades predictably, errors are informative, no silent corruption
- **Fail**: Silent failure, undefined behavior, or data corruption under stress → reopen, fix resilience gap before final delivery

---

## Reward Hack Test

**Trigger:** Before claiming resolution.

**Operation:** Does this solve the GENERAL problem, or only pass the current test conditions?
- Fix works for the specific case AND the general case?
- Would a different input expose the same underlying issue?
- Patch or real fix?

**Pass:** Fix verified against general case.
**Fail:** Patch only — continue methodology, do not claim done.

---

## End-to-End Control

**Trigger:** Task depends on external assumptions — API behavior, environment config, upstream output, error attribution.

**Operation:** Critical paths must not depend on unverified external assumptions.

| Dimension | Dependent (fragile) | End-to-End (controlled) |
|-----------|--------------------|-----------------------|
| API behavior | Assume from memory | Read docs or test the call |
| User environment | Guess OS/version/config | Detect programmatically or ask |
| Upstream output | Trust without validation | Validate input before using |
| Error cause | Attribute to environment | Verify with tools first (Red Line 2) |

**Pass:** All critical-path assumptions verified with tools.
**Fail:** Unverified assumption in critical path — flag as external dependency before proceeding.

---

## Keeper Test

**Trigger:** Before iterating on a failing or stalled output — decide continue vs. discard.

**Operation:** "If this output were about to be replaced, would I fight to keep it?"
- Yes — continue iterating, the output has value worth building on
- No — discard and restart with a structurally different approach

No improvement period. Decide now.

**Pass:** Output worth keeping — iterate.
**Fail:** Not worth keeping — discard. Do not invest in incremental improvement of output not worth keeping.

---

## Grayscale Deployment

**Trigger:** Executing changes. Execute phase.

**Operation:** Apply changes incrementally:
1. Apply to smallest viable scope (one function, one module)
2. Test and verify at small scope
3. Collect feedback from test results
4. Adjust if needed
5. Verify adjustment
6. Expand to full scope

**Pass:** Small-scope verification succeeds — cleared to expand.
**Fail:** Small-scope fails — fix at small scope first. Never go full-scope without small-scope confirmation.

---

## End-User Perspective

**Trigger:** Before delivery. Deliver phase.

**Operation:** Switch viewpoint — a naive end user receiving this output knows nothing about the implementation.
- Can they use it directly without implementation context?
- Check to interface level: function signatures, error messages, return formats, variable names

**Pass:** Output immediately usable by someone with zero implementation knowledge.
**Fail:** Requires insider knowledge to interpret — simplify interface before delivering.

---

## Difficulty Reporting Format

**Trigger:** T6 activated — difficulty acknowledged, progress continues.

**Operation:**
1. **Aim to assist** — report serves task completion, not excuse generation
2. **Actionable** — attach a concrete alternative or next step

**Pass:** Report includes specific next action.
**Fail:** "This is challenging" without concrete next step = evasion, not reporting.
