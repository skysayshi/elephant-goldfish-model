# Coupled-constraint review: distilled lesson and flow

Marker: `PUBLIC-REVIEW-COUPLING-20261108-v1`.

AI-assisted discussion draft for maintainer consideration. This proposes a review enhancement; it does not report an implementation, benchmark, or validated method.

## Problem Statement & Motivation

A review finding can improve one design property while weakening another that shares the same mechanism. A review process benefits from recording which dependencies changed and why a recommendation was revised.

For a wholly synthetic example, consider a job scheduler that groups active jobs by project label and permits two jobs per group. A proposed privacy improvement rotates the label for each report. If that label also defines the concurrency group, overlapping labels may inadvertently allow more jobs for one project. The useful result is a revised design obligation: distinguish reporting identity from accounting identity and verify both properties together.

Fresh Goldfish contexts can expose assumptions inherited by the author. However, context isolation and independent evidence are different: several reviewers reading the same source repeat one evidentiary basis, even when their analyses are independently generated.

## Proposed Scope (Goals vs. Non-Goals)

### 1. Proposed Overview

Add a small, explicit dependency-and-revision record to relevant reviews:

1. State the intended property, mandatory constraints, observer, and evidence scope.
2. For a proposed change, identify other requirements that consume the affected mechanism.
3. Classify each finding as observation, derived conclusion, counterexample, assumption, or proposed alternative.
4. Record what the finding changes: dependency, feasible alternatives, recommendation, or next check.
5. Recheck the revised recommendation against affected requirements and preserve the reason for withdrawing an earlier recommendation.
6. Select another review cycle only when its likely decision value justifies review and switching costs, or a mandatory unresolved obligation requires it.

An evaluation could use synthetic paired cases: one where rotating a reporting label affects accounting, one where the two identities are already separated, and one where evidence is insufficient. Reviewers should identify the relevant coupling without inventing a defect in the separated case or upgrading uncertainty into a pass.

### 2. Goals vs. Non-Goals

Goals: make cross-property regressions visible; preserve evidence provenance and scope; make revisions inspectable; keep review effort directed toward unresolved decisions.

Non-goals: replace human architectural choices, claim statistical independence between reviewers, introduce an automatic scoring controller, or declare a design correct from review alone. Any implementation would follow the repository’s separate design and contribution process.

Storage note: this is a user-requested note in an isolated branch of the user's fork. Issues are disabled in this fork. It is not submitted as an upstream PR, an accepted design, or a claim of human code review.
