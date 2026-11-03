# BAES Independent Evaluation Pilot

## Research Proposal and Funding Brief

**Project:** Evidence-Based Comparative Evaluation of BAES, NIST AI RMF 1.0, and ISO/IEC 42001:2023  
**Research Area:** Human Authority and Authorized Action in AI-Assisted Engineering  
**Research Lead:** Babak Rasti M.  
**Status:** Phase 1 active; Phase 2 deferred and conditional  
**Proposal Type:** Independent research proposal

---

## 1. Executive Summary

The BAES Independent Evaluation Pilot examines whether an engineering standard can help reconstruct the relationship between human intent, authorized tasks, AI-proposed or AI-executed actions, available evidence, and human decisions during AI-assisted engineering work.

The project uses an evidence-based comparative approach involving:

- Babak AI Engineering Standard (BAES)
- NIST AI Risk Management Framework (AI RMF 1.0)
- ISO/IEC 42001:2023

The evaluation is designed to permit positive, negative, mixed, or inconclusive findings. It does not assume that BAES performs better than the comparison frameworks.

The research is organized into two distinct phases:

**Phase 1 — Evidence-Packet Construction and Investigator-Side Assessment (Active)**

Phase 1 examines the internal coherence, traceability, reconstructability, and evidential sufficiency of structured evidence packets. It uses a public synthetic engineering scenario and an investigator-side audit. No human-reviewer performance is measured in this phase.

**Phase 2 — Human Reviewer Evaluation (Deferred and Conditional)**

Phase 2 is a proposed human-participant study intended to examine how reviewers interpret engineering evidence under conventional and structured review conditions. It requires a held-out scenario, frozen study materials, verified access controls, an approved protocol, and available independent reviewers.

Phase 2 has not begun and is not represented as a completed or guaranteed activity.

---

## 2. Research Question

The central research question is:

**To what extent can BAES support the reconstruction and assessment of authorized human intent, AI actions, evidence, and human decisions in AI-assisted engineering tasks, compared with selected established AI governance frameworks?**

The evaluation focuses on the distinction between:

- What a human intended and authorized;
- What an AI system proposed;
- What an AI system actually executed;
- What the available evidence demonstrates;
- What decisions were made by a human;
- Whether a particular action or deviation was demonstrably authorized.

The study does not assume that artifact approval, workflow completion, or a successful technical result necessarily establishes authorization for the specific action performed.

---

## 3. Research Design and Phases

### Phase 1 — Evidence-Packet Construction and Assessment

**Status: Active**

Phase 1 is an investigator-side evidence assessment. Its unit of analysis is the evidence packet and its constituent records, not the speed, competence, consistency, or performance of human reviewers.

The current public synthetic scenario is S01, based on the C99 complete_groups behavior.

Phase 1 activities include:

1. Stabilizing the public synthetic scenario and its technical baseline.
2. Constructing evidence variants that represent distinct authorization conditions:
   - Explicit, traceable authorization;
   - Artifact approval where specific informed authorization remains unresolved.
3. Keeping the common technical artifacts identical across the relevant evidence variants, so that the authorization evidence is the principal distinction.
4. Preparing an evidence index.
5. Mapping the preserved evaluation criteria C1–C20.
6. Conducting an investigator-side traceability and reconstruction audit.
7. Maintaining an ambiguity register that records unresolved interpretations and evidential limitations.

**Planned Phase 1 outputs:**

- Stabilized evidence packets;
- Evidence index;
- C1–C20 criteria mapping;
- Investigator-side traceability and reconstruction audit;
- Ambiguity register;
- A documented assessment of evidence sufficiency and limitations.

Phase 1 can establish whether the constructed evidence is internally coherent, traceable, and sufficiently informative for the intended reconstruction task. It cannot establish human reviewer performance or comparative reviewer effectiveness.

### Phase 2 — Human Reviewer Evaluation

**Status: Deferred and Conditional**

Phase 2 is a proposed human-participant study. It is not part of the currently active assessment.

The proposed design is a 2×2 between-reviewer comparison using a held-out scenario, HDA-01, rather than the publicly disclosed S01 scenario.

The four proposed conditions are:

| Condition | Review approach | Decision evidence |
|---|---|---|
| A-R1 | Conventional review | Explicit traceable decision record |
| A-R2 | Conventional review | Artifact approval; specific informed authorization unresolved |
| B-R1 | Structured review | Explicit traceable decision record |
| B-R2 | Structured review | Artifact approval; specific informed authorization unresolved |

Each reviewer would receive one evidence packet only.

The public S01 scenario is not eligible for blinded confirmatory testing because its behavior and boundary-test result are publicly available. It may be used for exploratory usability work, but it must not be presented as a blinded confirmatory case.

HDA-01 is currently a private draft. It has not been frozen or presented to reviewers.

**Prerequisites before Phase 2 can begin:**

- Completion and stabilization of the Phase 1 evidence packet and index;
- Verification of the private repository's collaborator list and effective access controls;
- Finalization and freezing of the held-out scenario and all reviewer packets;
- A frozen protocol covering reviewer assignment, exposure, instructions, coding, consent, privacy, and data retention;
- Versioned and frozen study materials;
- Availability of independent reviewers.

The proposed target is eight independent reviewers, with two reviewers per condition. A minimum of four reviewers may support a limited feasibility pilot, provided that all four conditions can be represented. Fewer than four reviewers, or an empty condition, would limit the activity to feasibility observations rather than comparative condition assessment.

This is not a statistical power analysis. The proposed design does not support claims of statistical significance or population-level generalization.

No reviewer has been recruited or assessed to date. No human-review data have been collected.

---

## 4. Evaluation Criteria and Comparative Scope

The evaluation preserves the twenty criteria C1–C20 as distinct criteria. They must not be silently merged, removed, or redefined.

The criteria are used to examine different dimensions of framework text coverage, evidence sufficiency, and residual ambiguity.

The comparative assessment considers:

- Whether relevant concepts and requirements are explicitly represented;
- Whether the available evidence supports reconstruction of actions and decisions;
- Whether authorization can be distinguished from artifact approval;
- Whether unresolved ambiguity is visible and documented;
- Whether the framework supports traceability without requiring unsupported assumptions.

The comparative scope includes BAES, NIST AI RMF 1.0, and ISO/IEC 42001:2023.

The assessment will use publicly available materials and permitted public previews or crosswalks. It will not reproduce or rely on unauthorized copies of licensed standards text. Where the available material does not support a clause-level assessment, the relevant item will remain unreviewed or explicitly limited.

No composite score will be used to imply an overall ranking of the frameworks.

---

## 5. Expected Deliverables

### Phase 1 Deliverables — Current Scope

- Stabilized public synthetic evidence scenario and variants;
- Evidence index and traceability references;
- C1–C20 mapping;
- Investigator-side reconstruction and evidence-sufficiency assessment;
- Ambiguity register;
- Comparative findings and documented limitations;
- Phase 1 research report.

### Phase 2 Deliverables — Conditional Scope

Only if Phase 2 prerequisites are satisfied and the human study is actually conducted:

- Reviewer responses and associated evidence references;
- Human-review interpretation analysis;
- Descriptive comparison across the four study conditions;
- Analysis of reviewer uncertainty and unresolved interpretations;
- Phase 2 report, including limitations and any deviations from the frozen protocol.

Reviewer responses and human-performance findings are not current deliverables and must not be represented as existing evidence.

---

## 6. Proposed Timeline

**Planning envelope: approximately six months.**

This is a preliminary planning estimate, not a commitment that Phase 2 will begin or that a human study will be completed within six months.

| Period | Proposed activity |
|---|---|
| Months 1–2 | Phase 1 evidence stabilization, packet construction, and evidence indexing |
| Months 2–3 | C1–C20 mapping, investigator-side audit, and ambiguity register |
| Month 4 | Comparative assessment and Phase 1 reporting |
| Month 5 | Phase 2 feasibility review and prerequisite completion, if possible |
| Month 6 | Conditional Phase 2 preparation or continuation of Phase 1 reporting and refinement |

If Phase 2 prerequisites are not met, the project will remain within Phase 1 scope. The timeline will be revised accordingly rather than treating human evaluation as an assumed outcome.

---

## 7. Proposed Funding

**Proposed funding envelope: USD 30,000**

This is a preliminary funding proposal. The allocation between phases should reflect the actual scope authorized and undertaken.

The proposed budget should distinguish between:

**Phase 1 — Active Research Work**

- Research and evidence-packet construction;
- Scenario and evidence stabilization;
- Criteria mapping and comparative assessment;
- Traceability and reconstruction audit;
- Documentation and reporting.

**Phase 2 — Conditional Research Work**

- Independent reviewer honoraria;
- Reviewer recruitment and coordination;
- Human-participant study execution;
- Human-response analysis;
- Additional reporting and study administration.

Phase 2 expenses should be incurred only if its prerequisites are satisfied and the study is authorized to proceed. Funds allocated to conditional activities should not automatically be treated as committed expenditures or silently reallocated.

The proposed funding supports independent research and evaluation. It does not purchase a predetermined result, endorsement, certification, or favorable assessment.

---

## 8. Independence and Research Integrity

The evaluation is intended to remain independent of the organizations or frameworks being assessed.

Funding or collaboration must not grant a sponsor authority to:

- Predetermine research findings;
- Change evaluation criteria without documented methodological justification;
- Suppress negative or inconclusive results;
- Require a favorable comparison;
- Claim ownership of the research conclusions merely by providing financial support.

Research findings will be reported according to the evidence obtained, including limitations, unresolved questions, and any negative or inconclusive outcomes.

The project does not claim that BAES has already been independently validated, certified, or proven superior to established frameworks.

---

## 9. Current Readiness and Limitations

The current research status is:

- Phase 1 is active.
- Phase 2 is deferred and conditional.
- No independent human reviewer has been recruited or assisted.
- No human assessment has been conducted.
- No human-review data or comparative reviewer-performance findings exist.
- The research protocol is version 0.4.1-draft and has not been frozen or preregistered.
- HDA-01 remains a private draft and has not been frozen or presented to reviewers.
- Access controls for the private held-out scenario must be verified before any reviewer recruitment.

These limitations are part of the current research status and will be updated only when supported by documented evidence.

---

## 10. Collaboration Sought

The project seeks support for the independent development and evaluation of an evidence-based approach to human authority and authorized action in AI-assisted engineering.

Potential forms of collaboration include:

- Financial sponsorship for the active Phase 1 research;
- Research-methodology feedback;
- Independent review of the evidence-packet design;
- Support for the conditional Phase 2 study, if its prerequisites are met;
- Access to appropriate independent reviewers or research collaborators.

The immediate priority is to complete a defensible Phase 1 evidence package. Any subsequent human-participant study will depend on methodological readiness, access controls, reviewer availability, and appropriate research arrangements.

---

## 11. Research References and Project Status

The following project documents define the current research scope and status:

- [Research Phases and Current Scope](https://github.com/babak-rasti-meymandi/Human-AI-Authorization-Evaluation/blob/main/15-Research-Phases-and-Current-Scope.md)
- [Research Protocol](https://github.com/babak-rasti-meymandi/Human-AI-Authorization-Evaluation/blob/main/01-Research-Protocol.md)
- [Pre-Registration Plan](https://github.com/babak-rasti-meymandi/Human-AI-Authorization-Evaluation/blob/main/09-Pre-Registration-Plan.md)
- [Reviewer Blinding and Data Integrity Plan](https://github.com/babak-rasti-meymandi/Human-AI-Authorization-Evaluation/blob/main/14-Reviewer-Blinding-and-Data-Integrity-Plan.md)
- [Reviewer Packets — Status](https://github.com/babak-rasti-meymandi/Human-AI-Authorization-Evaluation/blob/main/08-Reviewer-Packets/README.md)
- [Evidence and Results — Status](https://github.com/babak-rasti-meymandi/Human-AI-Authorization-Evaluation/blob/main/04-Evidence-and-Results/README.md)

**Research Lead:** Babak Rasti M.  
**Project:** BAES Independent Evaluation Pilot  
**Current Status:** Phase 1 active; Phase 2 deferred and conditional
