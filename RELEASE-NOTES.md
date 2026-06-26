# BeaconScore — Release Notes

BeaconScore is VCRI's free, open, in-browser security-posture self-assessment. Methodology is published under CC BY; dimension and subcriteria weights are public. This log records changes to the scoring rubrics so anyone re-running an assessment understands what moved and why.

---

## 2026-06-25 — AI Cognitive-Security rubric **v1.1**

**Summary:** Added three behavior-anchored subcriteria to the AI Cognitive-Security rubric (`ai-cogsec-v1`), strengthening coverage of multi-agent identity, log integrity, and tool/MCP containment. The rubric's floor only rises — coverage gets more complete; nothing was removed.

**With thanks / co-credit:** the three additions are derived from and co-credited to **Mitchell Parker (VP/CISO, Indiana University Health)** and his AI assistant "Wally," *"Recommended AI Security System Architecture Layers"* (v2, 2026-06-25). Their baseline controls map onto the lower maturity levels; VCRI's signed-authority / transparency-log / capability-based-federation depth occupies the advanced levels above them.

**What changed (2 of 7 dimensions):**

| Dimension | New subcriterion | Covers |
|---|---|---|
| Multi-agent coordination | **5x — Agent identity & authority integrity** | Distinct per-agent identities (baseline) → cryptographically signed inter-agent authority bound to agent+substrate (advanced) |
| Action & tools | **4x — Audit-log integrity** | Comprehensive logging → cryptographic log integrity → externally-anchored transparency log (SCITT) |
| Action & tools | **4y — Tool / MCP / interface containment** | Sandbox / default-deny scope now explicitly includes MCP servers and interfaces, not just tools |

**Weight transparency (published-weights ethos):** adding subcriteria renormalized the two affected dimensions' internal weights so each still sums to 1.0. Existing subcriteria were retained and kept their relative order.

- *Action & tools* (5 → 7 subcriteria): 4a 0.30→0.214 · 4b 0.25→0.179 · 4c 0.20→0.143 · 4d 0.15→0.107 · 4e 0.10→0.071 · **4x 0.143 (new)** · **4y 0.143 (new)**
- *Multi-agent coordination* (4 → 5): 5a 0.35→0.28 · 5b 0.25→0.20 · 5c 0.20→0.16 · 5d 0.20→0.16 · **5x 0.20 (new)**
- The other 5 dimensions (Weights, Durable memory, Inference-time perception, Revisability, Calibration) are **unchanged.**

**Impact on grades:** the two changed dimensions are together 25% of the total grade (weighted 0.15 + 0.10). The change makes the rubric *more complete* — organizations are now also scored on signed agent identity, log integrity, and MCP/interface containment. **No existing assessment's overall grade moves a full letter from this change alone.**

**Known follow-up:** the offline single-file download (`vcri-scorer-offline.html`) still embeds the prior rubric and will be rebuilt to match the hosted version.

*Methodology remains open (CC BY). Feedback on anchors or weights: info@valuechainrisk.org.*
