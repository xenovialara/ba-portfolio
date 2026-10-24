

# Healthily Me — Product Backlog

Status: Draft for Product/Engineering validation Source documents: Healthily Me BRD v1.0, RTM workbook, and 10 Habit Tracker MVP UAT scenarios Purpose: Translate the BRD into a prioritized, traceable backlog for Jira/Trello.

## Backlog conventions

- Story format: As a [user], I want [capability], so that [benefit].
- Priorities are proposed and must be confirmed with Product/Engineering.
- The top five stories include Given/When/Then acceptance criteria.
- BRD requirements and RTM/UAT references are included for traceability.
- Rules marked TBD are not approved product policy.

## Epics

| Epic ID | Epic                         | Outcome                                                                                |
| ------- | ---------------------------- | -------------------------------------------------------------------------------------- |
| EPIC-01 | Habit Logging & Progress     | Users can record, review and maintain accurate health-habit logs.                      |
| EPIC-02 | Streaks & Habit Continuity   | Users can understand streak progress and recover from missed days under defined rules. |
| EPIC-03 | Reminders & Motivation       | Users receive relevant reminders and feedback that support routine-building.           |
| EPIC-04 | XP, Milestones & Measurement | Users receive consistent recognition while the business evaluates MVP outcomes.        |

## EPIC-01 — Habit Logging & Progress

### US-01 — Record a habit completion

Priority: Must-have

User story: As a user, I want to log the completion of a selected health habit, so that I can record my activity and track progress.

Acceptance criteria

- The user can select an eligible habit and record a completion.
- The saved entry is visible in the user's habit history.
- The system records the completion against the applicable date and user.

Traceability: BRD FR-01; UAT scenarios do not directly test basic log creation.

### US-02 — View habit history and progress

Priority: Must-have

User story: As a user, I want to view my recorded habit history and progress, so that I can understand my activity over time.

Acceptance criteria

- The user can open a history/progress view.
- The view displays previously saved habit entries and relevant dates.
- The displayed records match the saved habit logs.

Traceability: BRD FR-02.

### US-03 — Edit a habit log

Priority: Must-have

User story: As a user, I want to edit a submitted habit log, so that I can correct an inaccurate entry.

Acceptance criteria

- The user can update an eligible existing log.
- The updated entry is shown in the history.
- Any affected streak, milestone and XP calculations are recalculated according to approved rules.

Traceability: BRD FR-03, FR-04.

### US-04 — Delete a habit log with confirmation

Priority: Must-have

User story: As a user, I want to delete a habit log after confirming the action, so that I can remove an entry I no longer want recorded.

Acceptance criteria

- The system asks for confirmation before deleting the log.
- If the user cancels, the log remains.
- If the user confirms, the log is removed from history and affected calculations are recalculated according to approved rules.

Traceability: BRD FR-03, FR-04.

Open decision: Whether previously awarded XP is reversed after deletion.

## EPIC-02 — Streaks & Habit Continuity

### US-05 — Track a daily habit streak

Priority: Must-have Existing story: RTM US-01 — Daily Habit Streak

User story: As a user, I want my active streak to update when I complete an eligible habit, so that I can monitor my consistency.

Acceptance criteria (Given/When/Then)

1. Given I have an active streak of 4 and have not completed an eligible habit today, When I complete my first eligible habit today, Then my streak increases to 5.
2. Given my streak has already increased today, When I complete another eligible habit on the same calendar day, Then the streak does not increase again.
3. Given I miss one calendar day and the approved grace rule applies, When that day ends without an eligible completion, Then the streak remains at its previous value.
4. Given I have missed two consecutive calendar days with no eligible completion, When the second missed day is processed, Then the streak resets to 0, subject to the approved grace-period rules.

Traceability: BRD FR-05; RTM US-01 / AC-01–AC-04; UAT-01–UAT-04.

Open rule: Confirm how grace days interact with consecutive missed days and whether grace use is capped.

### US-06 — Pause an active streak

Priority: Proposed

User story: As a user, I want to pause my active streak for an approved period, so that a temporary interruption does not automatically erase my progress.

Acceptance criteria

- The user can initiate a streak pause when eligible.
- The streak is preserved for the approved pause duration.
- The system applies the approved expiry and resumption rules.

Traceability: BRD FR-06.

Open rule: Maximum duration and eligibility are TBD.

### US-07 — Use an eligible grace day

Priority: Proposed

User story: As a user, I want an eligible missed day to be covered by a grace period, so that I can resume my routine without immediately losing my streak.

Acceptance criteria

- The system applies a grace day only when the user meets the approved eligibility rules.
- A grace day preserves the streak according to approved rules but does not count as a qualifying habit-completion day toward a milestone.
- The system enforces the approved grace-day frequency/cap.

Traceability: BRD FR-07; RTM US-04 / AC-14; UAT-03, UAT-04 and UAT-10.

Open rule: Grace-day cap/frequency is TBD.

## EPIC-03 — Reminders & Motivation

### US-08 — Configure a habit reminder

Priority: Proposed Existing story: RTM US-02 — Reminder Notifications

User story: As a user, I want to configure a reminder for a scheduled habit, so that I am prompted at a useful time.

Acceptance criteria (Given/When/Then)

1. Given a habit has a reminder configured and remains incomplete, When its scheduled reminder time is reached, Then the system sends a reminder for that habit, subject to supported notification settings.
2. Given the habit has been completed before the reminder time, When the scheduled time is reached, Then the reminder for that habit is suppressed.
3. Given multiple scheduled habits remain incomplete at the reminder trigger, When the reminder process runs, Then the system sends one consolidated reminder rather than multiple individual reminders, if this behavior is approved for MVP.

Traceability: BRD FR-09; RTM US-02 / AC-05, AC-06, AC-08; UAT-05, UAT-06.

Open decision: Product/UX to confirm timing and content of consolidated reminders.

### US-09 — Receive completion feedback

Priority: Proposed

User story: As a user, I want clear positive feedback after logging an eligible habit, so that I know the action was recorded successfully.

Acceptance criteria

- Positive completion feedback appears after a successful eligible completion.
- Feedback is not shown as a success if the save fails.
- The feedback does not imply that duplicate XP or streak increments were awarded.

Traceability: RTM US-02 / AC-07.

Open decision: This behavior is not explicitly listed as a separate BRD functional requirement and should be confirmed for MVP scope.

### US-10 — Manage reminder preferences

Priority: Proposed

User story: As a user, I want reminders to respect my notification preferences, so that I receive prompts in a way I have chosen.

Acceptance criteria

- The system respects supported user-configured reminder settings.
- A reminder is not sent when the applicable preference or device setting disables it, subject to platform behavior.
- The supported settings and platform limitations are documented.

Traceability: BRD FR-09 and NFR-06.

Open decision: Reminder preferences and supported notification settings require confirmation.

## EPIC-04 — XP, Milestones & Measurement

### US-11 — Configure habit difficulty and XP

Priority: Proposed Existing story: RTM US-03 — XP / Reward Points

User story: As a user, I want to assign an available difficulty level to an eligible habit, so that its reward reflects the approved difficulty rules.

Acceptance criteria (Given/When/Then)

1. Given I am configuring an eligible habit, When I select an available difficulty level and save, Then the selected difficulty is saved and displayed correctly.
2. Given a habit has an approved difficulty-to-XP mapping, When I complete the habit, Then the system awards the corresponding approved XP.
3. Given I have reached the approved maximum number of active Hard habits, When I try to classify another active habit as Hard, Then the system prevents that classification.

Traceability: BRD FR-10; RTM US-03 / AC-09, AC-10, AC-12; UAT-07.

Open decisions: Whether difficulty selection is mandatory; XP mapping; maximum concurrent Hard habits; what frees a Hard-habit slot. Illustrative XP values are not approved.

### US-12 — Prevent duplicate XP awards

Priority: Proposed

User story: As a user, I want XP to be awarded only once per eligible frequency period, so that my reward balance remains accurate.

Acceptance criteria (Given/When/Then)

1. Given a once-daily habit has already earned XP today, When I attempt to complete it again within the same eligible period, Then no additional XP is awarded.
2. Given an eligible completion has not yet earned XP, When the completion is successfully recorded, Then the system awards the applicable approved XP once.
3. Given the same completion request is submitted more than once, When the system processes the duplicate request, Then the XP balance is not increased more than once.

Traceability: BRD FR-10; RTM US-03 / AC-11; UAT-07, UAT-08.

Open rule: Reward behavior after a log is edited or deleted remains TBD.

### US-13 — View current XP balance

Priority: Proposed

User story: As a user, I want to see my current XP balance, so that I can understand the rewards I have earned.

Acceptance criteria

- The current balance reflects approved XP awards.
- The balance does not include duplicate awards.
- Any adjustment after an edited or deleted log follows approved reward-recalculation rules.

Traceability: BRD FR-10; derived supporting behavior that should be confirmed with Product.

### US-14 — Earn a milestone badge

Priority: Must-have (provisional) Existing story: RTM US-04 — Milestone Badges

User story: As a user, I want to earn a badge when I reach an approved habit milestone, so that my progress is recognized.

Acceptance criteria (Given/When/Then)

1. Given I have completed the approved number of qualifying completion days and have not earned the corresponding badge, When I complete the next activity that reaches the threshold, Then the system awards the badge.
2. Given a day is covered by a grace period without an eligible completion, When milestone progress is calculated, Then that day does not count as a qualifying completion day.
3. Given I have already earned a milestone badge, When my active streak later resets, Then the previously earned badge remains available.
4. Given I have already earned a particular milestone badge, When I reach the same milestone again after a streak reset, Then the system does not award a duplicate badge.

Traceability: BRD FR-08; RTM US-04 / AC-13–AC-16; UAT-09, UAT-10.

Open decision: The 7-day threshold is illustrative and must be validated with Product/Analytics before production approval.

### US-15 — Preserve earned milestone badges

Priority: Proposed

User story: As a user, I want to retain access to badges I have already earned, so that my achievements are not lost when my active streak resets.

Acceptance criteria

- Earned badges remain visible after a streak reset.
- A previously earned badge is not awarded a second time.
- Badge history is consistent with the user's recorded qualifying completion history, subject to approved correction rules.

Traceability: RTM US-04 / AC-15, AC-16; BRD FR-08.

### US-16 — Measure MVP conversion outcomes

Priority: Must-have for experiment evaluation

User story: As a Product/Growth stakeholder, I want free-to-paid conversion measured against an agreed baseline, so that I can evaluate the business outcome of the MVP.

Acceptance criteria

- The eligible user population, conversion definition, baseline, target and measurement window are agreed before the experiment.
- Results can be compared with the established baseline.
- Results are reported with the agreed analysis and decision rules; no unapproved numerical target is assumed.

Traceability: BRD BR-01, BO-01, Sections 12.1–12.4.

Note: This is an analytics/experiment requirement, not a user-facing habit-tracking feature.

### US-17 — Monitor engagement and retention

Priority: Must-have for experiment evaluation

User story: As an Analytics stakeholder, I want agreed engagement and retention measures tracked, so that I can assess whether the MVP supports sustained meaningful activity.

Acceptance criteria

- Product/Analytics define the engagement and retention metrics and observation windows.
- Results are compared with the agreed baseline where available.
- Findings distinguish observed association from demonstrated causation.

Traceability: BR-02, BR-03, BO-02, BO-03, Sections 12.2–12.4.

### US-18 — Review experiment results before further investment

Priority: Must-have for decision governance

User story: As a Business Sponsor or authorized decision-maker, I want experiment outcomes, costs, guardrails and risks reviewed together, so that I can make an evidence-based decision to iterate, expand or discontinue the MVP.

Acceptance criteria

- The review includes conversion, engagement, retention, user-experience guardrails, technical quality and costs.
- Statistical and practical significance are assessed using the approved experiment approach.
- A positive pilot result does not automatically authorize full rollout.
- The decision and rationale are documented by the authorized decision-maker.

Traceability: BR-04, BO-04, Sections 12.3–12.4.

## Cross-cutting non-functional requirements

These should be tracked as non-functional requirements or linked tasks rather than treated as ordinary user-facing stories unless the delivery team prefers that format.

| ID     | Requirement                                                                                     | Backlog treatment                                                                                     |
| ------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| NFR-01 | Habit logging and progress views meet agreed performance thresholds.                            | Add a measurable response-time target after stakeholder agreement; validate with performance testing. |
| NFR-02 | Habit records, streaks, milestones and rewards remain accurate and consistent.                  | Apply to US-01–US-15; validate with functional, integration and data-consistency testing.             |
| NFR-03 | User data is protected through appropriate authentication, authorization and secure handling.   | Security review/testing task; technical controls require Engineering validation.                      |
| NFR-04 | Core habit-tracking tasks are clear and understandable.                                         | Usability testing task; define usability targets with UX.                                             |
| NFR-05 | Personal/health-related data follows approved privacy, access, retention and deletion policies. | Privacy/compliance task; policies remain to be confirmed.                                             |
| NFR-06 | MVP supports agreed devices, operating systems and environments.                                | Compatibility testing task; supported platforms remain to be agreed.                                  |

## UAT traceability cross-reference

| UAT ID | Scenario                                            | Backlog story |
| ------ | --------------------------------------------------- | ------------- |
| UAT-01 | First eligible habit increments streak              | US-05         |
| UAT-02 | Additional same-day habit does not increment streak | US-05         |
| UAT-03 | One missed day preserves streak                     | US-05, US-07  |
| UAT-04 | Two consecutive missed days reset streak            | US-05, US-07  |
| UAT-05 | Incomplete scheduled habit triggers reminder        | US-08         |
| UAT-06 | Completed habit suppresses reminder                 | US-08         |
| UAT-07 | XP awarded by difficulty                            | US-11, US-12  |
| UAT-08 | Duplicate XP is prevented                           | US-12         |
| UAT-09 | Milestone badge is awarded                          | US-14         |
| UAT-10 | Grace day does not count toward milestone           | US-07, US-14  |

## Open decisions to resolve before implementation

1. Confirm final MVP scope and which proposed-priority stories are approved.
2. Define pause eligibility/duration and grace-day frequency/cap.
3. Approve milestone thresholds; the 7-day example is not yet a production commitment.
4. Approve XP values and difficulty mapping; example values are illustrative.
5. Decide whether difficulty selection is mandatory and define the maximum concurrent Hard-habit limit.
6. Define what frees a Hard-habit slot.
7. Define whether XP is retained or reversed after a log is edited or deleted.
8. Confirm reminder timing, consolidated-reminder behavior, content and preference controls.
9. Define data retention/deletion rules and measurable NFR thresholds.
10. Confirm conversion/engagement/retention metric definitions, baselines, experiment window and decision authority.

## Prioritization note

The BRD is a working draft pending stakeholder review. The proposed priority labels above are planning suggestions, not approved commitments. For a strictly feature-only MVP board, keep US-16–US-18 in a separate Analytics & Experiment Evaluation workstream or project task group rather than mixing them into engineering feature delivery.

## Definition of Ready — suggested

A story is ready for implementation when:

- Its business value and scope are understood.
- Dependencies and relevant BRD/RTM/UAT links are recorded.
- Acceptance criteria are testable.
- Required business rules are approved or the story is explicitly blocked on a named decision.
- UX, privacy, security and NFR impacts have been considered where relevant.

## Definition of Done — suggested

A story is done when:

- The acceptance criteria pass testing.
- Relevant UAT/test cases are updated and results recorded.
- Requirement traceability is maintained.
- Applicable privacy, security, usability and compatibility checks are complete.
- Any unresolved decisions or limitations are documented.
