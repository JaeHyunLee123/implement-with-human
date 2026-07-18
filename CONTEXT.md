# Agent-Skill Workflows

The language used to design and run the repository's agent skills and their human-review workflows.

## Language

**Review Slice**:
The smallest independently verifiable, commit-ready increment of implementation that is presented to a human for review. It changes at most 300 non-generated lines; generated files and lockfiles are reported separately.
_Avoid_: chunk, batch, task

**Changed Lines**:
The sum of additions and deletions reported by `git diff --numstat` for a Review Slice, including production code, tests, and manually written documentation. Generated files and lockfiles are excluded from the limit but disclosed separately.
_Avoid_: LOC, code size

**Review Gate**:
The pause after a Review Slice is committed and presented, during which no later slice may begin until a human explicitly approves it.
_Avoid_: checkpoint, handoff

**Review Feedback**:
A human-requested correction to the Review Slice currently at the Review Gate. It is implemented, verified, and re-presented before any later Review Slice begins.
_Avoid_: follow-up, next task

**Slice Plan**:
The human-approved ordered list of Review Slices, each with its verification method and estimated change size, that frames an implementation run.
_Avoid_: roadmap, checklist

**Plan Revision**:
A proposed change to a Slice Plan's scope, ordering, or Review Slice boundaries, which requires human approval before the affected slice begins.
_Avoid_: adjustment, replanning

**Slice Verification**:
The test and static-check evidence reported at a Review Gate: relevant tests and typecheck or lint for every Review Slice, plus the full suite for the final or high-impact slice.
_Avoid_: test result, quality check

**Automated Review**:
The `/code-review` result for a Review Slice, run against the slice commit's parent and included in the human review material. It informs but never satisfies the Review Gate.
_Avoid_: approval, sign-off

**Explicit Approval**:
An unambiguous human instruction such as `approve` or `next slice` that opens a Review Gate. Questions and informal positive reactions do not open it.
_Avoid_: acknowledgement, comment

**Progress Checklist**:
The human-visible record of a Slice Plan and its Review Slice states. It is the single source of truth for slice progress, rather than commit-message annotations.
_Avoid_: Slice Plan, status note

**Review Package**:
The fixed review material for a Review Gate: purpose, changed files, Changed Lines, verification evidence, Automated Review results, Progress Checklist state, and the decision requested from the human.
_Avoid_: review summary, handoff
