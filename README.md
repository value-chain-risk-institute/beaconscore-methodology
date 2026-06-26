# BeaconScore — Open Methodology

[**BeaconScore**](https://valuechainrisk.org/scorer) is the [Value Chain Risk Institute](https://valuechainrisk.org)'s free, in-browser security-posture self-assessment. **Your scores never leave your browser** — there is no server-side scoring.

This repository is the **open methodology** behind it: the rubrics, behavior-anchored maturity criteria, and **published weights** — under **CC BY 4.0**.

## What's here
- **`rubrics/`** — the assessment rubrics (six asset categories, including **AI Cognitive-Security**). Each defines its dimensions, behavior-anchored **0–5 maturity anchors**, and published per-criterion weights.
- **`RELEASE-NOTES.md`** — the changelog: what changed in the rubrics, the before/after weights, and why.

## What's *not* here — the line
This repo is the **open standard**. It deliberately does **not** contain, and never will:
- the accumulated **assessment corpus**,
- the **continuous calibration data**,
- the peer-relative **sensitivities ("the Greeks")**,
- any **customer / assessment data**.

Those are the basis of **Cairn Risk Co.'s** paid continuous-rating product — the commercial layer that funds and sustains this open standard. **Open grade, paid analytics.** The methodology is free and verifiable; the calibrated, continuous ratings are the service.

## Use it
- **Run it free:** https://valuechainrisk.org/scorer (and an offline single-file build for air-gapped use).
- The methodology is **CC BY 4.0** — use, adapt, and cite freely *with attribution*. VCRI maintains the canonical, continuously-calibrated version.

## Contribute
Issues and PRs welcome — propose anchor refinements, new attack→countermeasure mappings, or weight discussion. Real-world calibration makes the standard better.

## Credits
Methodology by the **Value Chain Risk Institute**. The AI Cognitive-Security rubric **v1.1** additions (agent identity & authority integrity, audit-log integrity, tool/MCP/interface containment) are co-credited to **Mitchell Parker** (VP/CISO, Indiana University Health) and his AI assistant **"Wally,"** from *"Recommended AI Security System Architecture Layers"* (2026).

---
*© Value Chain Risk Institute. Licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). "VCRI Ratings" and "BeaconScore" are marks of the Value Chain Risk Institute; this license covers the methodology text/data, not the marks.*
