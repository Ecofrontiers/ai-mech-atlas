# AI-Mech-Atlas Implementation Queue

Implementation log for MechanismAtlas.jsx changes.

---

## Completed (Feb 2026)

### 1. Cognitive Scope Classification
**Source:** `proposals/PROPOSAL-cognitive-light-cone.md`
**Status:** ✅ IMPLEMENTED (2026-02-27)

**Implemented as:**
- Field: `cognitiveScope` (descriptive labels, not H0-H5 to avoid confusion with L0-L5 autonomy)
- Values: `Transaction`, `Session`, `Task`, `Pipeline`, `Project`, `Organization`
- Added to all 34 mechanisms

**Rationale:** H0-H5 scale conflicted with existing L0-L5 autonomy taxonomy in DATA_AGENTS_TAXONOMY.md. Using descriptive labels avoids confusion while capturing reasoning scope dimension.

---

### 2. Security Profiles
**Source:** `proposals/PROPOSAL-ai-ml-stack-security.md`
**Status:** ✅ IMPLEMENTED (2026-02-27)

**Implemented as:**
```javascript
securityProfile: {
  riskLevel: "Critical|High|Medium",  // Aligned with FAILURES severity
  attackSurface: "Data|Model|Application|Agent",
  mitigations: [...],
  knownVulnerabilities: [...]
}
```
- Added to all 34 mechanisms
- Risk levels aligned with existing FAILURES severity taxonomy

---

### 3. Autonomous Task Orchestration (Aletheia Pattern)
**Source:** `proposals/PROPOSAL-aletheia-autonomous-research.md`
**Status:** ✅ IMPLEMENTED (2026-02-27)

**Implemented as:**
- Mechanism: `autonomous-orch` (Autonomous Task Orchestration)
- Category: **Oversight** (not new category — fits with autonomy-grad, agent-judge)
- Reference implementation: Aletheia (DeepMind)

**Rationale:** Aletheia is a specific implementation of a general pattern. The atlas catalogs coordination mechanisms, not capabilities. "Autonomous Task Orchestration" generalizes the pattern: agents independently plan, execute, and verify multi-stage workflows.

**Schema:**
```javascript
{
  id: "autonomous-orch",
  name: "Autonomous Task Orchestration",
  cat: "Oversight",
  cognitiveScope: "Pipeline",
  securityProfile: {
    riskLevel: "High",
    attackSurface: "Agent",
    mitigations: ["Citation verification", "Experiment logging", "Adversarial hypothesis testing"],
    knownVulnerabilities: ["Hallucinated citations", "P-hacking via unreported experiments", "Confirmation bias"]
  }
}
```

---

## Summary

| Change | Status | Mechanism Count |
|--------|--------|-----------------|
| cognitiveScope field | ✅ Done | 34 mechanisms |
| securityProfile field | ✅ Done | 34 mechanisms |
| Autonomous Task Orchestration | ✅ Done | 1 new mechanism |
| Oversight category count | Updated | 5 → 6 |

**Total mechanisms:** 34 (was 33)

---

## Pending (UI)

- [ ] Add cognitiveScope filter to mechanisms view
- [ ] Add securityProfile filter (by riskLevel)
- [ ] Display new fields in mechanism cards

---

*Queue created: 2026-02-27*
*Implemented: 2026-02-27*
