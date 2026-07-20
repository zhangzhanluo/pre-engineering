# Current Task Card Template

> This document is the PRE cross-role context "content carrier". The **Planner** fills it in fully before submitting a need (`REV_WAIT`); the **Executor** reads it in full before making an execution plan; the **Reviewer** verifies against the acceptance criteria item by item; the **Supervisor** reads only and never writes — it only checks whether the doc exists and whether its format is compliant.
> Collaboration-log entries stay ≤5 lines and only reference this file path (`Plan: see .pre/{PROJECT_NAME}/current-task-card.md`); content is not duplicated in the log.

---

## Requirement Name

<!-- Short requirement name, matching the "requirement" line in the collaboration-log entry -->

## Background & Goal (Why)

<!-- Which item in the project-goals doc this references, what problem it solves -->

## Plan Essentials (What)

<!-- Implementation path + key technical choices, 1-3 items -->

## Scope & Assumptions

<!-- Explicit scope boundaries, dependencies, implicit assumptions -->

## Integration Points

<!-- How it interfaces with existing code/modules/interfaces; for remote projects note where code lives (local/remote) -->

## Acceptance Criteria (Verifiable)

<!-- At least 3 quantified/testable criteria; state "not met → reject". Empty or placeholder text ("none" / "TBD" / "see project goals") counts as a Planner violation; Reviewer should reject -->

## Rejected Alternatives

<!-- Briefly describe alternatives considered but abandoned, and why, so the Executor doesn't retread dead ends -->

## Change Log

<!-- Append one line per revision: time + change point + brief before→after comparison -->

---

## Usage Rules (also written to the file tail at generation time, for the Planner's reference)

- **Requirement grading (P0 interim relief)**: small needs (≤1 file / ≤1 hour, e.g. config tweak, typo fix) may fill only "Requirement Name + Plan Essentials + Acceptance Criteria"; mark the rest "N/A".
- **Content quality floor**: any required section left empty or filled with placeholder text counts as a Planner violation, treated the same as a missing section.
- **Security note**: if `.pre/` is tracked in git, this file's "Rejected Alternatives" and "Scope & Assumptions" may contain project decisions/security assumptions that would be exposed — be mindful when filling in.
