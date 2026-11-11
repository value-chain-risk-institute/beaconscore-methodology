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

### Frameworks this methodology builds on
BeaconScore stands on other people's work, and that should be plain to anyone reading the rubrics.

- TIPPSS (IEEE/UL 2933-2024). Five of the six rubrics (people, processes, technology, data, facilities) score on the six TIPPSS dimensions: Trust, Identity, Privacy, Protection, Safety, and Security. TIPPSS is standardized in [IEEE/UL 2933-2024](https://standards.ieee.org/ieee/2933/7592/), the IEEE/UL standard for clinical Internet of Things data and device interoperability with TIPPSS. Applying those dimensions to organizations and vendors outside clinical IoT is VCRI's extension. It is not part of the standard and is not endorsed by IEEE or UL.
- Capability maturity levels (CMM and CMMI). The 0 to 5 maturity ladder follows the capability maturity model tradition that began with the Capability Maturity Model (CMM) at Carnegie Mellon University's Software Engineering Institute and continues as CMMI, now maintained by ISACA. The level definitions and behavior anchors in these rubrics are VCRI's own. BeaconScore is not a CMMI appraisal and is not affiliated with or endorsed by ISACA or Carnegie Mellon University.
- Secure Controls Framework (SCF). VCRI uses the [Secure Controls Framework](https://securecontrolsframework.com/) as its common control catalog when mapping between frameworks, and a planned revision of the crosswalks in this repository will route through SCF control IDs. This repository contains no SCF content. The SCF is copyright Secure Controls Framework Council, LLC, and is licensed under [CC BY-ND 4.0](https://creativecommons.org/licenses/by-nd/4.0/).

IEEE, UL, CMM, CMMI, and Secure Controls Framework are marks of their respective owners. Their mention here is credit, not a claim of endorsement.

---
*© Value Chain Risk Institute. Licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). "VCRI Ratings" and "BeaconScore" are marks of the Value Chain Risk Institute; this license covers the methodology text/data, not the marks.*
