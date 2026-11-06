# Human–AI Task State and Control Model

**Document ID:** BAES-EM-CAND-001  
**Version:** 0.1  
**Status:** Proposed — Under Research  
**Classification:** Research Candidate  
**Target BAES Layer:** Engineering Models  
**Normative Status:** Non-Normative  
**Epistemic Status:** Proposed engineering model; not yet empirically validated  
**Last Updated:** 2026-11-06

---

## 1. Research Motivation

Human–AI engineering work is not adequately represented as a sequence of isolated prompts and responses. A task may persist across multiple interactions, execution may be paused while the task remains open, authorization may change independently of task intent, and a system may retain task context after an operation has ended.

These dimensions are easy to conflate. For example:

- stopping visible output does not necessarily mean that a task has been cancelled;
- retaining a task description does not establish continuing authorization to act;
- completing an operation does not necessarily mean that its records should be erased;
- a previously authorized action does not remain authorized after its authorization has been revoked or materially changed.

This candidate model investigates how task state, execution state, and authorization state can be represented and controlled separately in Human–AI Engineering.

The research is motivated by stateful and control-system concepts, including persistence, state transitions, hysteresis, and bistability. These concepts are sources of engineering questions, not proof that an AI system has biological drives, intentions, or equivalent internal mechanisms.

## 2. Purpose

The model proposes a conceptual structure for:

1. representing the lifecycle of a human–AI task;
2. distinguishing task continuity from execution continuity;
3. representing authorization independently from task intent and execution;
4. defining explicit transitions such as pause, suspension, cancellation, completion, and reset;
5. ensuring that a retained task state cannot be treated as permission to continue or resume execution;
6. making state changes, authorization changes, and execution outcomes traceable through evidence.

The model is intended to support design, analysis, and validation. It does not prescribe a particular software architecture, storage mechanism, agent framework, orchestration platform, or implementation technology.

## 3. Scope and Non-Goals

### 3.1 In scope

- Task lifecycle and task-state representation.
- Execution lifecycle and execution-state representation.
- Authorization validity, scope, and revocation.
- State-transition conditions and transition evidence.
- Pause, suspension, cancellation, completion, termination, and reset distinctions.
- Human override and safe-stop behavior.
- Persistence and recovery of task context.
- Candidate failure modes and validation tests.

### 3.2 Out of scope

- Defining or modifying BAES Foundation principles.
- Redefining Human Governance Authority or Human Override.
- Granting AI independent authority to determine or preserve human intent.
- Treating a model's generated text as conclusive evidence of its actual runtime state.
- Specifying a universal internal-state architecture for all AI systems.
- Establishing a normative compliance requirement.
- Claiming that biological mechanisms map directly onto AI mechanisms.

## 4. Conceptual Foundations

The following concepts motivate the model. They must remain distinct.

### 4.1 State persistence

A system may retain a representation of a task or process after the input that established it is no longer present. Persistence may be implemented through memory, durable records, workflow state, checkpoints, or other mechanisms.

Persistence alone does not establish that the retained state is correct, current, or authorized for further execution.

### 4.2 Bistability

Bistability describes systems with two stable states under specified conditions. It may be relevant to particular engineered components, but it is not a synonym for statefulness or task persistence.

The model does not assume that every AI system is bistable.

### 4.3 State versus observable output

Observable output is not a complete representation of system state.

A lack of visible output does not, by itself, prove that execution has stopped. Conversely, visible output does not prove that an action is authorized or that an operation is still running.

State claims require appropriate runtime evidence, not merely conversational inference.

### 4.4 Hysteresis

Hysteresis describes systems in which transition thresholds depend on the direction or history of change. It can help prevent unstable switching in suitable control systems.

In this model, hysteresis is only a candidate technique for managing operational fluctuations. It must not be used to resist, delay, or invalidate an explicit human instruction to change or revoke authorization.

### 4.5 Bounded physical or technical response

Some operations require a non-zero time to reach a safe stopped condition. This is a technical property of the operation, not a limit on the human's authority to issue a stop instruction.

The model therefore distinguishes the authority to request or require a stop from the technical time and steps needed to reach a safe condition.

## 5. Core State Dimensions

The model separates three primary state dimensions. Implementations may represent them differently, but must not silently collapse their meanings.

### 5.1 Task State

Task State represents the lifecycle of the assigned task, independently of whether execution is currently active.

Candidate task states:

| State | Meaning |
|---|---|
| Proposed | A task has been described but has not yet been accepted as an active task. |
| Active | The task is accepted and remains open. |
| Suspended | The task is retained but cannot proceed until its suspension condition is resolved. |
| Cancelled | The task has been cancelled by an authorized decision. |
| Completed | The task's defined completion conditions have been met and evidenced. |
| Closed | The task lifecycle is administratively closed; its records may remain available. |

These labels are candidates. An implementation may require additional states, but must define their semantics and transitions.

### 5.2 Execution State

Execution State represents the condition of a particular operation or execution instance associated with a task.

Candidate execution states:

| State | Meaning |
|---|---|
| Not Started | No execution instance has begun. |
| Ready | Preconditions for a specific execution instance have been checked. |
| Running | The operation is executing. |
| Pausing | A pause has been requested and the operation is moving toward a defined pause point. |
| Paused | The operation has reached a defined paused condition. |
| Stopping | A stop has been requested and the operation is moving toward a safe stopped condition. |
| Stopped | The execution instance is no longer performing the operation. |
| Failed | The execution instance ended without satisfying its intended outcome. |

A task may remain Active while its execution is Paused or Stopped. A task may also have multiple execution instances over its lifecycle; each instance must be traceable.

### 5.3 Authorization State

Authorization State represents whether a defined action is currently permitted under the applicable human-granted authority and constraints.

Candidate authorization states:

| State | Meaning |
|---|---|
| Not Granted | No applicable authorization has been established. |
| Valid | Authorization exists for the specified actor, action, scope, and conditions. |
| Restricted | Authorization remains valid only within a reduced or conditional scope. |
| Suspended | Authorization is temporarily unavailable pending resolution of a stated condition. |
| Revoked | Authorization has been withdrawn by an authorized human decision. |
| Expired | Authorization has passed its defined validity period or condition. |
| Superseded | A newer authorization has replaced the earlier authorization. |

Authorization must be evaluated for the specific action being considered. A valid authorization for one action does not automatically authorize a different action, expanded scope, or materially changed objective.

Retained task context is not authorization.

## 6. State Separation and Invariants

The following are proposed model invariants for validation:

**I-01 — Independent dimensions:** Task State, Execution State, and Authorization State are distinct dimensions. A transition in one dimension must not silently imply a transition in another.

**I-02 — No authorization by persistence:** Retention of task context, checkpoints, or prior instructions does not establish continuing authorization.

**I-03 — No authorization by output:** Generated text claiming that an action is permitted does not itself establish authorization.

**I-04 — Revocation precedence:** Once a valid revocation is received and recognized, the revoked authorization must not be used to initiate new actions or resume affected execution.

**I-05 — Human stop authority:** An authorized human stop instruction must be accepted as a control instruction. Technical stopping time may be necessary, but cannot be treated as a reason to reject the instruction.

**I-06 — Evidence-based state claims:** Claims about actual execution state must be supported by suitable evidence. Conversational statements alone may be insufficient.

**I-07 — Record preservation:** Task cancellation, completion, termination, or reset must not silently erase records that are required for traceability, audit, safety, or applicable retention obligations.

**I-08 — Explicit resumption:** A paused or suspended execution may resume only when its applicable preconditions and authorization have been re-established.

**I-09 — Scope integrity:** A change in task scope or objective requires evaluation of whether existing authorization still applies.

**I-10 — No autonomous intent fixation:** The system must not treat an earlier representation of human intent as immutable or use it to override a later authorized human decision.

These invariants are proposed for research and are not yet normative BAES requirements.

## 7. State Transition Rules

A transition is a change from one defined state to another. Each transition should specify:

- source state and target state;
- triggering event or decision;
- actor authorized to initiate or approve it;
- preconditions;
- effects on the other state dimensions;
- required evidence and traceability;
- failure and recovery behavior.

### 7.1 Pause

Pause is a request to temporarily stop or suspend an execution instance while retaining the task.

A pause does not, by itself:

- cancel the task;
- revoke authorization;
- establish that all execution has stopped;
- authorize later resumption.

The implementation must define what constitutes a completed pause and what evidence demonstrates that condition.

### 7.2 Suspension

Suspension means that progress is withheld pending resolution of a specified condition. The condition may concern authorization, safety, missing information, dependencies, or human review.

A suspended task or execution must not be treated as freely resumable. The applicable condition must be resolved and the necessary authorization re-established.

### 7.3 Cancellation

Cancellation is an authorized decision that the task should not continue.

Cancellation must prevent further execution under the cancelled task authorization. Any already-started operation must enter the applicable stop or safe-termination process.

Cancellation does not imply deletion of task history, evidence, or decisions.

### 7.4 Completion

Completion means that defined task completion conditions have been satisfied and supported by evidence.

A model-generated assertion of completion is not sufficient by itself where independent verification, tests, human acceptance, or other evidence is required.

### 7.5 Termination

Termination refers to ending a particular execution instance or process. It is not necessarily equivalent to task cancellation or task completion.

An execution instance may terminate because it completed, failed, was cancelled, or was stopped for another reason.

### 7.6 Reset

Reset returns a defined component or execution context to a specified initial or known state.

Reset must have an explicit scope. It must not silently:

- erase task history;
- restore revoked authorization;
- reactivate a cancelled task;
- discard required evidence;
- reinterpret an earlier instruction as current authorization.

A reset of runtime state is distinct from deletion or retention-policy action on records.

### 7.7 Resume

Resume initiates or continues execution after a pause or suspension.

Before resumption, the system must verify at least:

1. the task remains valid and open;
2. the requested action remains within the current task scope;
3. authorization for that action is currently valid;
4. relevant dependencies and safety preconditions are satisfied;
5. no later human decision has cancelled, superseded, or materially changed the task.

A previously valid authorization must not be assumed to remain valid after a material change or revocation.

## 8. Human Authority and Override Constraints

This model treats human authority as a governance constraint, not as a tunable control parameter of the AI system.

### 8.1 Authority to stop

A human with the applicable authority must be able to issue a stop instruction without satisfying an AI-defined amplitude, duration, confidence, or persistence threshold.

The system may need to execute technical steps to reach a safe stopped condition. It must distinguish:

- acceptance and recognition of the human stop instruction;
- initiation of the stop procedure;
- completion of the technical stopping process;
- evidence that the operation is stopped.

### 8.2 No resistance through hysteresis

Hysteresis or other anti-flapping mechanisms may stabilize operational signals. They must not cause the system to ignore or defer an explicit authorized human change, cancellation, or revocation.

### 8.3 No self-renewing authorization

An AI system must not renew, broaden, or recreate its own authorization merely because the task remains active, a prior authorization existed, or execution would otherwise be convenient.

### 8.4 Changed intent and scope

When human intent or task scope changes, the system must identify whether the existing authorization remains applicable. If applicability is uncertain, it must not infer expanded permission.

## 9. Candidate Engineering Properties

The following properties are research candidates, not established universal requirements.

| Property | Description | Main concern |
|---|---|---|
| State Persistence | Relevant task state can be retained across defined interruptions. | Stale or corrupted state |
| State Observability | Relevant state can be inspected through reliable evidence. | Output mistaken for runtime truth |
| State Separation | Task, execution, and authorization states remain distinguishable. | Accidental coupling |
| Transition Explicitness | State changes have defined triggers and effects. | Implicit transitions |
| Revocation Responsiveness | Revocation prevents further affected actions. | Continued execution under stale permission |
| Safe Stopping | Operations can reach a defined safe stopped condition. | Unsafe interruption or misleading stop claims |
| Controlled Resumption | Resumption requires current preconditions and authorization. | Automatic restart without permission |
| Traceability | Decisions and transitions can be reconstructed from records. | Missing or ambiguous evidence |
| Recovery Integrity | Recovery does not silently restore invalid state or permission. | Unauthorized continuation |

## 10. Counterexamples and Failure Modes

The model should be tested against at least the following counterexamples:

1. **Output cessation mistaken for task cancellation:** The interface stops producing text, but the task remains active.
2. **Task persistence mistaken for permission:** The system remembers a task and resumes execution after authorization has been revoked.
3. **Pause mistaken for safe stop:** The interface reports Paused while a delegated operation continues elsewhere.
4. **Cancellation mistaken for record deletion:** A cancelled task loses the evidence needed to establish what happened.
5. **Reset restores stale authorization:** A reset reloads an earlier checkpoint and inadvertently reactivates permission that was withdrawn.
6. **Hysteresis resists human change:** An anti-flapping mechanism delays an explicit authorized change of direction.
7. **Completion asserted without evidence:** The system declares a task complete although required verification has not occurred.
8. **Scope drift:** A system continues under an earlier authorization after the task has materially changed.
9. **Ambiguous stop semantics:** A stop request is acknowledged, but no one can determine whether it means stop generating output, stop a tool call, stop a workflow, or stop all delegated operations.
10. **Concurrent execution:** One component is stopped while another execution instance continues under the same task.

Each failure mode should be evaluated with observable evidence and a clearly stated epistemic status.

## 11. Validation Tests

### Test A — Persistence

**Question:** Does the system retain the correct task state after a defined interruption?

**Method:** Establish a task, interrupt the interaction or execution, and inspect the recovered task state.

**Evidence:** State records, checkpoint data, event logs, and observed recovery behavior.

**Failure condition:** The system loses, corrupts, or silently changes relevant task state.

### Test B — Revocation

**Question:** Does revocation prevent new actions and resumption under the revoked authorization?

**Method:** Grant a bounded authorization, initiate a task, revoke the authorization, and attempt to continue or resume.

**Evidence:** Authorization records, action logs, tool execution records, and stop acknowledgements.

**Failure condition:** An affected action proceeds after the revocation has been recognized, without a new valid authorization.

### Test C — State Separation

**Question:** Can the system distinguish task, execution, and authorization states?

**Method:** Exercise combinations such as Active + Paused + Valid, Active + Stopped + Revoked, and Cancelled + Stopped + Revoked.

**Evidence:** State representations, transition records, and observed behavior.

**Failure condition:** A change in one dimension silently or incorrectly changes another.

### Test D — Human Override

**Question:** Does the system accept an authorized human stop or cancellation instruction without requiring an AI-defined strength, duration, or confidence threshold?

**Method:** Issue a clear stop instruction during different execution conditions, including conditions where the system is maintaining a persistent task state.

**Evidence:** Instruction receipt, control acknowledgement, stop initiation, execution cessation, and timing records.

**Failure condition:** The system rejects or disregards the instruction because an internal persistence or hysteresis mechanism has not been satisfied.

### Test E — Controlled Resumption

**Question:** Can a system resume only when the task, authorization, and operational preconditions remain valid?

**Method:** Pause or suspend a task, then vary authorization and task scope before attempting resumption.

**Evidence:** Authorization checks, task records, transition logs, and execution events.

**Failure condition:** Execution resumes under stale, revoked, expired, or out-of-scope authorization.

### Test F — Reset Integrity

**Question:** Does reset preserve required records and avoid restoring invalid permissions?

**Method:** Reset a component after cancellation or authorization revocation, then inspect recovered state and attempt execution.

**Evidence:** Before-and-after state records, audit history, authorization records, and execution logs.

**Failure condition:** Reset erases required evidence or restores invalid authorization.

## 12. Evidence and Evaluation Requirements

Validation should distinguish at least:

- **Observed:** Directly supported by execution records, logs, test results, or other inspectable evidence.
- **Established:** Supported by sufficient evidence within a clearly bounded test scope.
- **Not established:** The available evidence does not support the claim.
- **Interpretation:** A reasoned explanation or proposed meaning that is not itself directly observed.
- **Hypothesis:** A proposition that requires testing.

A test report should record:

1. system and version under test;
2. test environment and relevant configuration;
3. initial task, execution, and authorization states;
4. exact human instructions and authorization boundaries;
5. events and state transitions;
6. evidence sources and limitations;
7. expected versus observed behavior;
8. deviations, failures, and unresolved ambiguity;
9. reproducibility information;
10. conclusion bounded to the tested conditions.

No composite score should be introduced unless its dimensions, weighting, and interpretation are independently justified.

## 13. Open Research Questions

1. What minimum state information is necessary to preserve task continuity without preserving stale assumptions?
2. Which state dimensions must be durable, and which may be reconstructed?
3. How should systems represent concurrent execution instances associated with one task?
4. What evidence is sufficient to establish that delegated execution has actually stopped?
5. How should revocation propagate across tools, agents, queues, and external services?
6. How can a system distinguish a temporary interruption from a human decision to cancel or replace a task?
7. Which uses of hysteresis are safe in operational control, and how can explicit human decisions bypass them?
8. What recovery guarantees are feasible when a system or external service becomes unavailable?
9. How should task state and authorization be reconciled when records conflict?
10. Which properties can be tested consistently across different AI architectures?

## 14. Acceptance Criteria for Further Model Development

This candidate should not be promoted to a more mature engineering model until:

- the three core state dimensions have unambiguous definitions;
- state transitions and their effects are specified;
- stop, pause, cancellation, termination, completion, and reset are distinguishable;
- authorization revocation and controlled resumption are addressed;
- human override is not weakened by persistence, hysteresis, or bounded-control mechanisms;
- counterexamples and failure modes have been tested;
- claims are supported by reproducible evidence;
- limitations and unresolved questions are documented;
- no conflict with the established BAES Foundation Baseline is introduced.

A successful set of tests would support only the properties and conditions actually tested. It would not establish universal applicability.

## 15. Relationship to BAES

This document is a non-normative research candidate intended for possible future consideration within the Engineering Models layer.

It does not:

- amend the BAES Foundation Baseline;
- establish a new Foundation principle;
- alter the seven-layer BAES structure;
- create a new BAES policy or compliance requirement;
- claim approval or adoption by BAES;
- modify BAES-Public or BAES-SECRET.

Any future proposal to incorporate this model into BAES must follow the applicable review and change-control process. Until then, this document records a research direction rather than an approved part of the standard.

## 16. Revision History

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-06 | Initial research-candidate formulation: separated task, execution, and authorization states; defined candidate transitions, invariants, failure modes, and validation tests. |

---

**Document status:** Proposed — Under Research  
**Normative status:** Non-Normative  
**Approval status:** Not approved as a BAES model
