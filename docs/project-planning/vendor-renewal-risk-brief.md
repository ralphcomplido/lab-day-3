---
prd_id: "PRD-VENDOR-RENEWAL-RISK-BRIEF"
title: "policy-desk Vendor Renewal Risk Brief"
description: "Transcript-grounded draft requirements and unresolved decisions for vendor renewal risk briefs."
status: "in-review"
version: "0.1.0"
owners: []
reviewers: []
created_date: "2026-10-07"
last_updated: "2026-10-07"
product_goal_ids: ["GOAL-001", "GOAL-002", "GOAL-003"]
product_goal_smart_status: "deferred"
fr_to_ac_coverage_threshold_pct: 80.0
fr_to_goal_coverage_threshold_pct: 100.0
diagram_format: "none"
lineage:
  supersedes: []
  superseded_by: []
source_brd_id: null
requirement_id_prefixes:
  fr: "FR"
  ac: "AC"
  nfr: "NFR"
  con: "CON"
  goal: "GOAL"
---

## Executive Summary

policy-desk will assemble a cited vendor renewal risk brief for a TPRM analyst
to check and fix any errors before it reaches the business owner. The brief presents
renewal blockers, supporting records, approvals, and deadlines; it does not
make or recommend the renewal decision. [S01, S08, S17]

The target is to reduce Tier 1 analyst assembly time from approximately three
hours to under forty-five minutes, including analyst review. The baseline is
rough and must be retrieved from renewal-case time records. Generation itself
must take under two minutes; review is separate. [S12, S15, S21]

Scheduled generation occurs thirty days before the notice window opens, not
thirty days before expiry. Business owners can also request a brief on demand,
using the same analyst-review flow. Output is Markdown for pasting into a
ProcureNet renewal case. [S04, S07, S08, S18]

This is a draft, not an approved implementation specification. Vendor coverage,
production data sourcing, cost, reviewed-delivery timing, retention, release
dates, and approval ownership remain open. The proposed card-processor pilot
is not confirmed. [S08-S13, S19-S20]

## Product Context

### Evidence Boundary

The sole requirements evidence is the
[2026-09-22 kickoff transcript](../meetings/renewal-kickoff-transcript.md).
Evidence IDs below identify timestamps in that file. Requirements express
recorded decisions or explicitly labeled defensible inferences; acceptance
criteria operationalize them without adding unsupported product behavior.
Policy assertions are meeting-reported assertions, not independently verified
policy. No corpus, source code, or external research was used to decide
requirements.

The [existing-system README](../../README.md) is now available and is integrated
as descriptive context only, not requirements evidence. OQ-001 is resolved by
reading and integrating that file. No README statement adds or changes a
transcript-derived requirement, acceptance criterion, constraint, goal, or
answer to another open question.

The transcript warns that speaker attribution may be wrong. Dana explicitly
corrects the attribution of the model-risk evaluation comment at 00:25:12;
that statement is attributed to Dana here. Inaudible content is not evidence.

### Problem and Existing Behavior

Analysts repeatedly assemble tier, findings, performance, financial health,
incidents, and approvals. Business owners receive inconsistent formats, and
Procurement can learn of an open High finding only three weeks before expiry.
Lena reports that copying Word tables into renewal cases breaks formatting.
[S01, S07]

Participants report that policy-desk already answers policy questions with
policy citations, takes eight to twelve seconds per policy question, and logs
retrieved documents and prompts. Source-record citations are new. Reported
current logging retention is not an approved retention design for briefs.
[S02, S12, S13]

### Existing-System Context

The [README](../../README.md) describes policy-desk as grounded Q&A over
Northwind Capital Group's TPRM and procurement policy corpus. Its documented
request path uses a Microsoft Agent Framework agent with gpt-5-mini through
FoundryChatClient and one search_policies retrieval tool. Queries are embedded
with text-embedding-3-small and matched against an in-process cosine-similarity
vector index, returning the top five hits. Retrieved hits are recorded for the
turn; answers carry document-ID citations checked against the documents that
retrieval returned.

The documented repository contains a local policy corpus, a prebuilt embedding
index and chunk metadata, cached retrieval-evaluation data, and offline unit
tests. The README describes keyless Azure authentication through azure-identity
and Azure CLI login, and labels the infrastructure deployment as reference only.

These are README-reported characteristics of the existing Q&A system, not
independently verified runtime behavior or implementation choices for the
renewal risk brief. The README does not decide vendor-record integration,
renewal coverage, delivery SLA, retention, or any other transcript gap. It
introduces no new requirements evidence and closes only the context-availability
question OQ-001.

### Evidence Register

All entries refer to the kickoff transcript, not to independent policy sources.

| ID | Timestamp range | Evidence and authority |
| --- | --- | --- |
| S01 | 00:00:21-00:00:57 | Repeated assembly work, late blockers; brief does not decide renewal. |
| S02 | 00:01:38-00:02:27 | Every statement cites policy or actual source record; clickable finding, policy section; uncited statements omitted. Mock-up is not wired. |
| S03 | 00:02:31-00:03:02 | Competing tier scope; estimates of 340 annual renewals across tiers and 65 Tier 1/2. |
| S04 | 00:03:09-00:04:09 | Reminder-aligned trigger thirty days before notice window opens; overdue reassessment blocks renewal. Earlier ninety-day Tier 1 statement later corrected. |
| S05 | 00:04:14-00:06:03 | Tier, findings, exceptions, value, four scorecards, financial health, twelve-month incidents; narrower choices override earlier suggestions. |
| S06 | 00:06:03-00:07:10 | ServiceNow contact-data warning; business-owner approval, finding/exception approvals, concentration check, exit deadline; deadlines cited. |
| S07 | 00:09:10-00:10:53 | Markdown chosen for case comments; business-owner on-demand requests, including QBR use. |
| S08 | 00:11:11-00:13:47 | At 00:11:56-00:12:09, Priya interprets $250,000 as annual spend; Lena clarifies she means total contract value. Tier versus TCV versus all-vendor coverage remains open and is taken offline; analyst checks and fixes both paths; same-day delivery tentative. |
| S09 | 00:15:15-00:16:45 | ProcureNet data; Coupa nightly CSV available for prototype; API access pending, column-change concern. |
| S10 | 00:16:54-00:18:09 | PDF indexing alternative; scanned-PDF concern; production architecture decision explicitly open. |
| S11 | 00:21:12-00:22:09 | One-dollar versus fifty-cent cost proposals; number to be settled after prototype. |
| S12 | 00:20:39-00:21:12 | Generation under two minutes, review separate; feasibility depends on sourcing and measurement. |
| S13 | 00:22:20-00:23:56 | Audit needs exact records seen; thirty-day raw personal-data logs, thirteen-month summaries, seven-year review record tension; Records consultation needed. |
| S14 | 00:24:14-00:25:24 | Preserve before/after analyst edits; corrections indicate quality; Dana's model-risk evaluation comment misattributed then corrected. |
| S15 | 00:29:05-00:30:05 | Rough three-hour Tier 1 baseline; under forty-five-minute target including review; rewriting means failure; case time records available. |
| S16 | 00:26:28-00:27:37 | Negotiation-email drafting explicitly excluded from v1, listed for later only. |
| S17 | 00:32:20-00:33:22 | Unavailable/stale sources disclosed, never guessed or blank; no recommend-renew output; blockers at top. |
| S18 | 00:36:12-00:37:01 | Final windows: Tier 1 120, Tier 2 90, Tier 3 60, Tier 4 30 days; Tier 1 trigger 150 days before expiry; policy-driven windows. |
| S19 | 00:39:08-00:41:03 | Tentative card-processor pilot; assigned prototype, export, logging, baseline, historical reviews, pilot confirmation, and scope actions. |
| S20 | 00:41:23-00:43:14 | Records action explicitly unowned; reviewer name, not phone; vendor-master contact-exposure concern unresolved. |
| S21 | 00:44:39-00:44:51 | Restates forty-five-minute Tier 1 target including review and three-hour baseline. |

## Users and Personas

| Role | Job and pain point | Desired outcome | Evidence |
| --- | --- | --- | --- |
| TPRM analyst | Assemble records, check generated content, correct any errors; repetitive collection consumes time. | Check rather than rewrite a brief; meet the Tier 1 time target. | S01, S08, S15 |
| Business owner; Lena Ortiz represents Payments Operations | Understand obstacles to renewal; paste the brief into a case; obtain a brief before a QBR. | Reviewed, cited blockers at the top and usable Markdown. | S07, S08, S17 |
| Procurement manager; Marcus Feld | Avoid late findings and missed re-sourcing requirements. | Early visibility of blockers and threshold crossing. | S01, S05 |
| TPRM sponsor; Priya Raman | Preserve analyst oversight and assess corrections. | Human-reviewed output and measurable analyst time savings. | S08, S14, S15 |
| CISO Office delegate; Dana Whitlock | Establish what records the model saw and avoid contact-data exposure. | Audit evidence and explicit handling of privacy questions. | S06, S13, S20 |

Tom Okafor is the software engineer assigned prototype and options work, not
the recorded production-architecture decision owner. Jordan Lee is the meeting
note-taker. Treasury supplies financial health; vendor managers own scorecard
ratings. PRD approval roles are not assigned by the meeting. [S05, S10, S19]

## Design Decisions

| ID | Recorded decision | Evidence |
| --- | --- | --- |
| DD-001 | Generate thirty days before the notice window opens; use policy-derived windows. Final Tier 1 window is 120 days, superseding ninety. | S04, S18 |
| DD-002 | Display current TCV and re-sourcing flag, not full amendment/value history. | S05 |
| DD-003 | Display four scorecards, most recent first, not only the last one; do not compute ratings. | S05 |
| DD-004 | Brief incident coverage is twelve months, not the full contract term. Analyst can pull the term separately. | S05 |
| DD-005 | Markdown output and one analyst-review process for scheduled and on-demand requests. | S07, S08 |
| DD-006 | Negotiation-email drafting is not a v1 requirement. | S16 |

Production sourcing is not a design decision: CSV, API, and contract-PDF
indexing remain alternatives. Scope likewise has no chosen alternative.
[S08-S10]

At 00:11:56-00:12:09, Priya interprets $250,000 as annual spend and Lena
clarifies that her proposed coverage criterion is total contract value. This
clarifies the distinction between their proposals, not a coverage decision;
OQ-002 remains open. [S08]

## Product Goals

| ID | Transcript-grounded outcome | Baseline and target | Gaps | Evidence |
| --- | --- | --- | --- | --- |
| GOAL-001 | Reduce Tier 1 analyst assembly effort including review. | Approximately three hours to under forty-five minutes, including analyst review. | Baseline validation, sample, aggregation, measurement window and deadline: OQ-012. | S15, S21 |
| GOAL-002 | Give business owners early, cited visibility of renewal obstacles without deciding for them. | Every statement supported; blockers first; scheduled thirty days before window opening. No business-outcome baseline provided. | Coverage and delivery timing: OQ-002, OQ-004. | S02, S04, S08, S17 |
| GOAL-003 | Preserve human accountability and evidence of generated-content corrections. | Analyst checks both request paths; preserve before/after edits and records seen. No correction-rate threshold provided. | Evaluation and evidence lifetime: OQ-006, OQ-013. | S08, S13, S14 |

SMART status is deferred: the time-saving goal is specific and measurable,
but feasibility, time horizon, and measurement details are not settled.
Behavioral goals have observable checks but no approved outcome-rate targets.
MoSCoW ranking across requirements was not decided; no invented priority
ranking or MVP cut line is assigned (OQ-014).

## Functional Requirements

These requirements are grounded in the kickoff transcript; workflow-derived
inferences are classified in the Exercise 2 audit in `LAB-LOG.md`. They are not
an approved release backlog. Each row states the actor, trigger, and outcome;
the traceability tables supply its acceptance criteria and goal links.

| ID | Actor and trigger | Required outcome | Evidence |
| --- | --- | --- | --- |
| FR-001 | Scheduled flow, for a renewal within the yet-to-be-decided coverage | Generate the brief thirty days before the policy-derived notice window opens, aligned with the ProcureNet reminder. | S04, S18 |
| FR-002 | Business owner requests a brief on demand | Generate a brief without waiting for the scheduled trigger, using the same analyst-review flow. | S07, S08 |
| FR-003 | TPRM analyst receives a generated brief | Allow checking against records and correction of any errors before delivery to the business owner; do not send an unreviewed brief to the owner. | S08 |
| FR-004 | Analyst or owner reads a statement | Provide a policy-section citation or actual-source-record reference for every statement; make finding references clickable; omit unsupported assertions. | S02, S06 |
| FR-005 | Analyst or owner receives the brief | Present Markdown that can be pasted into ProcureNet case comments. | S07 |
| FR-006 | Analyst or owner reads the summary | Put blockers at the top; describe obstacles with citations, not a renewal decision or recommend-renew conclusion. | S01, S17 |
| FR-007 | A vendor's brief is generated | Identify the vendor and its tier from the vendor master. | S02, S05 |
| FR-008 | A vendor's brief is generated | Include open findings and open exceptions with exception expiry dates, exposing the recorded timing risk. | S05 |
| FR-009 | A renewal's value is assessed | Show current TCV and flag a renewal taking an original award below $250,000 above $250,000 for re-sourcing unless a sole-source justification exists; omit value history. | S05 |
| FR-010 | Performance section is generated | Display the last four scorecards, most recent first, with overall ratings and dimensions; place an open improvement plan at the section top; use vendor-manager ratings rather than compute them. | S05 |
| FR-011 | Financial-health section is generated | Show Treasury's Green/Amber/Red flag, last-review date, and watch-list status; identify Red as blocking extension until TPRC review. | S05 |
| FR-012 | Incident section is generated | Include incidents for the last twelve months and whether notification deadlines were met. | S05 |
| FR-013 | Approval/deadline section is generated | Show required approvers and due dates with policy citations, including business-owner approval and the kickoff rules detailed in AC-013 and AC-017 through AC-021. | S04, S06 |
| FR-014 | A source is unavailable or stale | Explicitly disclose unavailable/current-rating gaps and last-review date when available; never guess or leave a blank implying nothing to report. | S17 |
| FR-015 | A brief has been reviewed | Display the reviewer's name at the bottom, not the reviewer's phone number. | S20 |
| FR-016 | An analyst corrects the brief | Preserve the generated and edited versions so corrections can be inspected as evaluation evidence. | S14 |

## Non-Functional Requirements

All NFRs link to the same transcript evidence as their behavioral checks.
Missing category targets remain questions, not inferred obligations.

### Performance and Capacity

NFR-001: Generation shall take under two minutes, excluding analyst review.
Verification: time generation and compare elapsed time with 120 seconds.
Workload, timing boundaries, percentile, and test conditions are undecided
(OQ-011). Supports GOAL-001; evidence S12.

Annual estimates of 340 renewals across all tiers and 65 Tier 1/2 renewals are
planning context, not committed throughput or concurrency requirements. [S03]

### Reliability and Resilience

NFR-002: Unavailable or stale source data shall be disclosed rather than
invented or silently blank. Verification: AC-014. Supports GOAL-002; evidence
S17. Staleness thresholds, availability, retry and recovery targets: OQ-008,
OQ-015.

### Security

NFR-003: Audit evidence shall establish exactly which source records were
in front of the model for a brief, extending reported document/prompt logging.
Verification: for a generated brief, inspect its evidence to determine whether
a specified finding was supplied. Supports GOAL-003; evidence S13. Representation,
integrity controls, access controls, and lifetime remain open (OQ-006, OQ-007).

### Privacy

NFR-004: The reviewer identification in the brief shall contain the reviewer's
name, not their phone number. Verification: AC-015. Supports GOAL-003; evidence
S20. No general field allowlist or telemetry-redaction strategy was agreed;
broader source-field, access and telemetry-redaction controls remain open in
OQ-006 and OQ-007. The narrow brief-output safeguard inferred from the exposure
story is stated separately in NFR-009.

NFR-009: The renewal brief shall not reproduce unnecessary source-record
contact details such as on-call contacts, bridge numbers, escalation chains, or
vendor account-manager mobile numbers. Verification: AC-022. This is an
inference from the prior exposure and the described incident-record fields;
the broader permitted-field, access, and logging controls remain open in
OQ-007. Evidence: S06, S20.

### Scalability and Elasticity

No target decided. Vendor coverage, rerun volume, peak load, and concurrency
remain open (OQ-002, OQ-015). Annual counts alone do not decide these targets.

### Maintainability and Operability

NFR-005: Scheduling shall use the notice window from policy rather than
fixed notice-window numbers. Verification: AC-001. Supports GOAL-002; evidence
S18. Operational ownership, policy-update handling, and failed-run behavior
remain open (OQ-015, OQ-019).

### Observability

NFR-006: Generated and analyst-edited briefs shall be available for inspecting
corrections as quality/evaluation evidence. Verification: AC-016. Supports
GOAL-003; evidence S14. Correction definitions, thresholds, and measurement
window remain open (OQ-013); NFR-003 covers input evidence.

### Usability and Accessibility

NFR-007: Markdown output shall preserve its structure when pasted into a
ProcureNet renewal-case comment. Verification: AC-005. Supports GOAL-001 and
GOAL-002; evidence S07. Accessibility standards and further usability targets
were not decided (OQ-015).

### Compatibility and Interoperability

NFR-008: The brief shall be compatible with ProcureNet Markdown case comments.
Verification: AC-005. Supports GOAL-002; evidence S07. No production connector,
automatic case-write integration, PDF parser, or citation syntax was chosen
(OQ-003, OQ-009, OQ-020).

### Portability

No environment or portability target decided (OQ-015). No inferred hosting,
model, storage, or technology selection is included.

## Constraints

| ID | Boundary and category | Imposing source and non-negotiability | Impact |
| --- | --- | --- | --- |
| CON-001 | Decision authority; organizational | Priya explicitly reserves renewal decisions for humans; Lena remains the decision-maker in the discussion. S01, S17. | FR-006 cannot recommend renewal or decide it. |
| CON-002 | Delivery oversight; operational | Priya requires analyst review for both flows and rejects two processes. S08. | FR-002/FR-003 cannot promise instant reviewed delivery. |
| CON-003 | Evidence; operational | Priya and Dana require cite-or-drop. S02. | FR-004 excludes unsupported statements. |
| CON-004 | v1 scope; organizational | Priya excludes negotiation positions; Procurement agrees. S16. | No negotiation-email drafting or vendor-facing negotiation in v1. |
| CON-005 | Performance data ownership; organizational | Priya says the vendor manager owns the rating. S05. | FR-010 uses recorded ratings, not calculated ones. |

## Acceptance Criteria

Status is Not Started for every criterion. These are prospective acceptance
checks, not claims that the capability already works. Unknown boundaries are
cross-referenced rather than silently supplied.

| ID | Given / When / Then | Covers | Status |
| --- | --- | --- | --- |
| AC-001 | Given a covered renewal and its policy notice window, when the date is thirty days before that window opens, then generate the brief with the reminder-aligned trigger. For the meeting's final 120-day Tier 1 window this is 150 days before expiry, not 30 or 120. Given a changed policy window, the trigger follows that window. | FR-001 | Not Started |
| AC-002 | Given a business-owner request for a covered vendor, when submitted outside the scheduled trigger, then generate a brief and send it through the same analyst-review flow rather than directly to the owner. | FR-002 | Not Started |
| AC-003 | Given an unreviewed brief, when the owner-delivery step is reached, then withhold delivery until a TPRM analyst has checked it and corrected any errors found; an error-free brief needs no edit before delivery. | FR-003 | Not Started |
| AC-004 | Given policy-supported and record-supported statements, when the brief is produced, then each has its supporting reference, findings can be clicked through, and policy obligations name their section. Given an uncitable assertion, then it is omitted, not invented. | FR-004 | Not Started |
| AC-005 | Given a reviewed Markdown brief, when pasted into a ProcureNet case comment, then its headings, lists, tables where present, and references retain their intended structure rather than the reported broken Word-table formatting. | FR-005 | Not Started |
| AC-006 | Given renewal blockers in cited records, when the brief is read, then blockers are at the top and no renew decision or recommend-renew conclusion appears. | FR-006 | Not Started |
| AC-007 | Given an identified vendor and vendor-master tier, when the brief is generated, then that vendor and recorded tier appear. Missing-data behavior follows AC-014. | FR-007 | Not Started |
| AC-008 | Given open findings and exceptions, when the brief is generated, then include those findings, exceptions and expiry dates. Given an exception expiring two weeks after renewal, then explicitly flag the risk of "renewing into a breach." Evidence: S05, 00:04:21-00:04:35. | FR-008 | Not Started |
| AC-009 | Given any renewal, when the brief is produced, then display current TCV without full history, regardless of threshold crossing. Separately, given an original award below $250,000 and renewal above $250,000 without sole-source justification, then flag re-sourcing; if justification exists, reflect it. Equality and monetary basis remain OQ-017. Evidence: S05, 00:04:35-00:05:02. | FR-009 | Not Started |
| AC-010 | Given at least four scorecards and an open improvement plan, when the performance section is produced, then it contains the last four in descending recency, their recorded overall ratings and dimensions, and the plan at the top; no new rating is calculated. Fewer scorecards remain OQ-008. | FR-010 | Not Started |
| AC-011 | Given Treasury's flag, review date and watch-list status, when financial health is displayed, then those recorded values appear. Given Red with TPRC review still outstanding, then the brief identifies no extension until TPRC review as a cited blocker. The effect of completed review remains OQ-010. | FR-011 | Not Started |
| AC-012 | Given incidents spanning more than twelve months, when the brief is generated, then the incident section covers the last twelve months with notification-deadline compliance, not the full term. Period anchor and boundary remain OQ-018. | FR-012 | Not Started |
| AC-013 | Given a renewal brief, when its approval section is generated, then business-owner approval is shown with its policy citation. | FR-013 | Not Started |
| AC-014 | Given an unavailable source or data identified as stale, when the brief is generated, then it explicitly reports the gap and last-review date where available, with no guessed current value or blank implying a clean result. Staleness definitions and release handling remain OQ-008. | FR-014 | Not Started |
| AC-015 | Given a reviewed brief, when its footer is inspected, then the reviewer name appears and the reviewer's phone number does not. | FR-015 | Not Started |
| AC-016 | Given an analyst correction, when the evidence is inspected, then both the generated version and the analyst-edited version are available to identify the correction. Retention and evaluation scoring remain OQ-006/OQ-013. | FR-016 | Not Started |
| AC-017 | Given an overdue reassessment, when renewal blockers are generated, then the overdue reassessment is identified as a blocker with its policy citation. | FR-013 | Not Started |
| AC-018 | Given a Critical or High finding without an exception, when renewal blockers are generated, then the brief identifies that renewal cannot be approved, with its policy citation. Valid-exception rules remain OQ-010. | FR-013 | Not Started |
| AC-019 | Given a required exception approval and applicable policy mapping, when approvers are displayed, then they follow tier and Critical goes to CRO, with policy citations. Undetailed approver mappings remain OQ-010. | FR-013 | Not Started |
| AC-020 | Given a Tier 1 renewal, when required checks are displayed, then the TPRM Office concentration check appears with its policy citation. | FR-013 | Not Started |
| AC-021 | Given a Tier 1 or Tier 2 non-renewal, when deadlines are displayed, then the exit-plan deadline is sixty days before expiry and has its policy-section citation. | FR-013 | Not Started |
| AC-022 | Given source records containing on-call contacts, bridge numbers, escalation chains, or vendor account-manager mobile numbers, when the renewal brief is produced, then those unnecessary contact details are not reproduced in the brief. Broader field-use and logging controls remain OQ-007. | NFR-009 | Not Started |

## Traceability Matrix

### FR-to-AC Coverage

| Source ID | Source title | Target ID | Coverage |
| --- | --- | --- | --- |
| FR-001 | Scheduled trigger | AC-001 | 1 |
| FR-002 | On-demand request | AC-002 | 1 |
| FR-003 | Analyst review | AC-003 | 1 |
| FR-004 | Statement citations | AC-004 | 1 |
| FR-005 | Markdown output | AC-005 | 1 |
| FR-006 | Blockers and authority | AC-006 | 1 |
| FR-007 | Vendor and tier | AC-007 | 1 |
| FR-008 | Findings and exceptions | AC-008 | 1 |
| FR-009 | Current TCV and re-sourcing | AC-009 | 1 |
| FR-010 | Scorecards and improvement | AC-010 | 1 |
| FR-011 | Financial health | AC-011 | 1 |
| FR-012 | Incidents | AC-012 | 1 |
| FR-013 | Approvals and deadlines | AC-013, AC-017, AC-018, AC-019, AC-020, AC-021 | 6 |
| FR-014 | Missing/stale data | AC-014 | 1 |
| FR-015 | Reviewer identification | AC-015 | 1 |
| FR-016 | Edit evidence | AC-016 | 1 |

Coverage: 16 / 16 = 100.0%; template threshold 80.0%. Linked criteria do not
resolve open scope, boundary, or acceptance-test conditions.

### FR-to-GOAL Alignment

| Source ID | Target IDs | Coverage |
| --- | --- | --- |
| FR-001 | GOAL-002 | 1 |
| FR-002 | GOAL-002 | 1 |
| FR-003 | GOAL-001, GOAL-003 | 2 |
| FR-004 | GOAL-002 | 1 |
| FR-005 | GOAL-001, GOAL-002 | 2 |
| FR-006 | GOAL-002 | 1 |
| FR-007 | GOAL-001, GOAL-002 | 2 |
| FR-008 | GOAL-001, GOAL-002 | 2 |
| FR-009 | GOAL-002 | 1 |
| FR-010 | GOAL-001, GOAL-002 | 2 |
| FR-011 | GOAL-001, GOAL-002 | 2 |
| FR-012 | GOAL-001, GOAL-002 | 2 |
| FR-013 | GOAL-001, GOAL-002 | 2 |
| FR-014 | GOAL-002 | 1 |
| FR-015 | GOAL-003 | 1 |
| FR-016 | GOAL-003 | 1 |

Alignment: 16 / 16 = 100.0%; template target 100.0%. These are author-maintained
links, not stakeholder sign-off. No BRD, feasibility handoff, or research
finding dispositions apply because none were supplied or used.

## MVP and Release Framing

The capability is a renewal risk brief with analyst oversight, not negotiation
drafting or automated renewal approval. Agreed contents and flows are recorded
above, but no first-release coverage cut was agreed. [S01, S08, S16-S17]

| Scope item | Status | Evidence |
| --- | --- | --- |
| Vendor coverage | Open: Tier 1/2, every vendor, or TCV over $250,000; annual spend is not TCV. | S03, S08 |
| Single-vendor CSV prototype | Assigned to Tom; this is not production sourcing approval. | S19 |
| Production CSV, API, or PDF indexing | Architecture decision open; Tom lays out options, not the decision-maker. | S09-S10 |
| Full value/amendment history | Withdrawn; excluded from brief. | S05 |
| Full-term incident review | Not brief scope; analyst can pull it separately. | S05 |
| Calculated performance ratings | Excluded; vendor-manager ownership retained. | S05 |
| Negotiation email | Explicitly out of v1; later idea only, not a committed release. | S16 |
| Tier 1 card-processor pilot | Offered, subject to Lena confirming expiry and willingness. | S19 |

The pilot's expiry is tentatively end of May; participants discuss end of
December generation and end of January window opening. The year, exact dates,
vendor identifier, and release commitment are not confirmed. No date is inferred
from the meeting date. [S19; OQ-014]

## Success Metrics

| Measure | Baseline | Target | Measurement source/window | Goal and evidence |
| --- | --- | --- | --- | --- |
| Tier 1 analyst effort including review | Approximately three hours, not yet validated | Under forty-five minutes, including analyst review | Renewal-case time records; Priya to pull baseline. Window, sample and aggregation open. | GOAL-001; S15, S19, S21 |
| Generation elapsed time, excluding review | No brief-generation baseline; policy Q&A eight to twelve seconds is not comparable | Under 120 seconds | Start/stop, load, aggregation and reporting open. | GOAL-001; S12 |
| Analyst corrections | Not provided | No numeric target; rewriting described as failure | Preserved before/after edits; scoring and window open. | GOAL-003; S14-S15 |
| Statement support | Existing policy citations reported; no measured coverage baseline | Every statement has supporting evidence; uncitable claims omitted | Inspect statement/reference pairs; evaluation method and sample open. | GOAL-002; S02 |
| Input-evidence completeness | No measured baseline provided | Establish exactly what source records were seen | Per-brief input evidence; representation and retention open. | GOAL-003; S13 |

Telemetry acceptance is limited to the transcript's observable outcomes: a
timed generation run can be checked against NFR-001, input evidence can answer
whether a finding was seen (NFR-003), and before/after edits can be inspected
(AC-016). Telemetry instruments, names, attributes, exporters, sampling, and
redaction were not decided. No technology or new telemetry vocabulary is
mandated; those choices remain OQ-019. Business case-time measurement is not
silently replaced with model latency.

Cost is not an accepted KPI threshold: $1 and $0.50 per brief were proposals,
with the final number deferred until a prototype. Reruns and cost accounting
boundaries are unresolved. [S11; OQ-005]

## Operational Readiness

Audit acceptance must establish whether particular source records were in
front of the model, not merely which source system was contacted. Both
generated and edited content are needed for correction evidence. [S13-S14]

Dana reports thirty-day raw retention where personal data is present,
thirteen-month summaries, and seven-year renewal-review records. Their
compatibility is explicitly a Records question, not an approved retention
solution. Records consultation has no owner. No snapshot retention period,
archival mechanism, access model, or logging/redaction strategy is invented.
[S13, S20]

Generation speed excludes analyst review. Same-day reviewed delivery is
Lena's stated expectation, but Priya's "Probably" leaves commitment and
service definition unsettled. Queue assignment, notification, routing and
reprocessing mechanisms are not specified. [S08; OQ-004, OQ-015, OQ-020]

## Dependencies and Recorded Actions

Assignments are recorded commitments from the meeting; completion has not
been verified. Relative due dates are retained as spoken.

| Dependency/action | Recorded owner | Recorded timing | Evidence |
| --- | --- | --- | --- |
| Data-source options and one-vendor CSV prototype | Tom Okafor | No due date stated | S19 |
| Export distribution access and column list | Marcus Feld | "Today" at kickoff | S19 |
| Audit logging requirements to Tom | Dana Whitlock | "By Friday" at kickoff | S19 |
| Tier 1 time baseline and 10-15 past renewal reviews for testing | Priya Raman | No due date stated | S19 |
| Card-processor expiry and pilot willingness confirmation | Lena Ortiz | No due date stated | S19 |
| Scope conversation with Lena and Marcus | Priya Raman | No date stated | S19 |
| Records consultation on retention mismatch | Explicitly unassigned | No date stated | S20 |
| Production API access | Request with integration team since August; decision owner not assigned | Pending, no commitment | S09-S10 |

### Reported Data Locations

| Data | Meeting-reported location | Unresolved boundary |
| --- | --- | --- |
| Vendor tier, findings, exceptions, scorecards | ProcureNet; findings in TPRM module | Access, schema, permissions and freshness |
| Contract dates, value, vendor, tier, manager | ProcureNet/Coupa nightly CSV proposed for prototype; API alternative | Authoritative production path, identifier joins, original-award and renewal values |
| Financial flag, date, watch list | Treasury quarterly emailed spreadsheet | Delivery, freshness and approved ingestion |
| Incident records and notification compliance | ServiceNow third-party incident table | Access and which fields may be used |
| Policy obligations and windows | Existing policy citation capability reported | Exact sections, approver mapping and changes |
| Contract clauses | Repository PDFs proposed as alternative | Whether chosen, scan quality, page citations |

Source: S05-S06, S09-S10. These locations do not authorize new integrations or
prove all needed fields are available.

## Risks and Assumptions

### Key Assumptions

No additional assumptions are adopted as requirements. Meeting estimates and
tentative statements remain explicitly unvalidated.

| Item | Evidence status | Impact if false | Recorded action or open question | Source |
| --- | --- | --- | --- | --- |
| Three-hour Tier 1 baseline | Rough estimate | Time-saving claim may be inaccurate | Priya to pull case-time baseline; OQ-012 | S15, S19 |
| CSV usable for one-vendor prototype | Proposed path, access not verified | Prototype blocked | Marcus distribution and column-list action; OQ-003 | S09, S19 |
| Card processor expires at end of May | Tentative, year not supplied | Pilot schedule changes | Lena confirmation action; OQ-014 | S19 |

### Risk Register

Probability and impact ratings were not decided and are recorded as unknown,
not invented. Only meeting-raised actions are recorded as mitigations.

| Risk | Probability / impact | Recorded response or gap | Evidence |
| --- | --- | --- | --- |
| Late blocker visibility leaves inadequate remediation runway | Unknown / unknown | Earlier reminder-aligned generation | S01, S04 |
| All-vendor scope increases analyst workload | Unknown / unknown | Offline scope discussion; no coverage decision | S08 |
| CSV columns change or API access remains blocked | Unknown / unknown | Tom options write-up; Marcus export access; production choice open | S09-S10, S19 |
| Scanned contract PDFs are unreadable | Unknown / unknown | No mitigation agreed; sourcing question open | S10 |
| Contact data leaks from exports or incident records | Unknown / unknown | Dana logging write-up; general field controls unresolved | S06, S20 |
| Thirteen-month input evidence cannot support a seven-year review record | Unknown / unknown | Records consultation required, owner open | S13, S20 |
| Stale/unavailable inputs read as no risk | Unknown / unknown | Explicit gap disclosure; never guess | S17 |
| Analysts rewrite rather than review generated briefs | Unknown / unknown | Preserve edits and test against 10-15 historical reviews; scoring open | S14-S15, S19 |
| Pilot runway too short if access remains unresolved | Unknown / unknown | Confirm pilot and expiry; no revised schedule chosen | S19 |

## Open Questions

Every item in this section is Open. "Unassigned" means the transcript did not assign an owner;
it is not an invitation to infer one. Context and derivative completeness gaps
are distinguished from explicit meeting deferrals. No answers are proposed.

During Build confirmation on 2026-10-07, the user confirmed the transcript's
Tier 1 target as under forty-five minutes including analyst review, against
an approximate three-hour baseline (S15). That target boundary is no longer
open; OQ-012 retains the unanswered measurement details. Vendor coverage,
production sourcing and its decision owner, a firm same-day SLA, retention
reconciliation and consultation ownership, and a quantitative correction-quality
threshold remain open. All other undecided items remain open. The user
subsequently confirmed the Build content and open-question treatment and
authorized exit from Build into Integrate on 2026-10-07. This phase-transition
confirmation does not approve the PRD or resolve the remaining questions.
Finalization and PRD approval require asking the user first.

| ID | Undecided question | Ownership evidence | Source/type |
| --- | --- | --- | --- |
| OQ-002 | Which vendors are covered: Tier 1/2, all tiers, or TCV over $250,000? Does the same coverage govern on-demand requests? | Priya schedules discussion with Lena and Marcus; final decision authority not stated | S03, S08, S19; annual spend versus TCV clarified at 00:11:56-00:12:09, but coverage explicitly deferred |
| OQ-003 | Which production source strategy is approved: export, API, contract-PDF indexing, or another combination? Who decides, and what access/schema/join commitments exist? | Tom lays out options, explicitly does not decide; Marcus assigned export access only | S09-S10, S19; explicit deferral and completeness gap |
| OQ-004 | Is same-day reviewed delivery committed? How are the day, cutoff, working hours and queue measured? | Lena requests it; Priya says "Probably"; SLA owner unassigned | S08; tentative, not an approved SLA |
| OQ-005 | What is the per-brief cost cap, accounting boundary, and treatment of reruns? | Final number deferred until prototype; owner unassigned | S11; explicit deferral |
| OQ-006 | How are seven-year renewal records reconciled with thirty-day raw personal-data logs and thirteen-month summaries, including inputs and edit evidence? Who asks Records? | Explicitly no owner; Records must be consulted | S13, S20; explicit unowned deferral |
| OQ-007 | Which source fields may be used, shown, and logged? What contact-data exclusion, redaction, access and evidence-integrity controls apply? Is the vendor-master tab the prior leak source? | Dana assigned logging requirements only; broader controls unassigned | S06, S13, S20; raised concern and completeness gap |
| OQ-008 | What makes each source stale? How are fewer than four scorecards, missing records, unavailable citations and partial briefs handled in review/release? | Unassigned | S05, S17; completeness gap, disclosure decided but boundaries not |
| OQ-009 | What source-record link/citation format and granularity are required beyond clickable findings and policy sections? | Unassigned | S02, S10; completeness gap |
| OQ-010 | What are the complete tier-specific exception-approval mappings, authoritative policy sections, and rules for valid exceptions or completed TPRC review? | Unassigned | S05-S06; details not decided |
| OQ-011 | How is under-two-minute generation measured: start/stop, workload, concurrency, failures and percentile? | Unassigned; Tom notes API feasibility needs measurement | S12; completeness gap |
| OQ-012 | For the confirmed target of under 45 minutes including analyst review against an approximate three-hour baseline, how is the baseline validated, and what sample, aggregation, measurement window and deadline establish success? | Priya owns baseline pull only | S15, S19, S21; remaining measurement completeness gaps |
| OQ-013 | How are corrections/rewriting scored, what quality threshold applies, and what evidence does model risk require? | Priya supplies 10-15 historical reviews; approval/scoring owners unassigned | S14-S15, S19; completeness gap |
| OQ-014 | Is the pilot confirmed; which vendor, expiry year/date, milestones, release horizon and v1 priorities are committed? Who approves the PRD? | Lena confirms pilot and expiry; other ownership unassigned | S19; tentative pilot and completeness gap |
| OQ-015 | What availability, recovery, load, operational ownership, accessibility and portability targets apply? | Unassigned | Not decided in transcript; completeness gaps, not inferred NFRs |
| OQ-016 | What happens when dates or records change, a trigger is missed, or a user reruns a brief? What versions or duplicate controls apply? | Unassigned | Not decided in transcript; completeness gap |
| OQ-017 | How is exactly $250,000 handled, in what currency/value basis, and which records establish original-award value, renewal value and sole-source justification? | Unassigned | S05, S08-S09; threshold and data completeness gaps |
| OQ-018 | What anchors the last-twelve-month incident period and its boundary, and which incident timestamps establish notification-deadline compliance? | Unassigned | S05; completeness gap |
| OQ-019 | What logging/telemetry representation and vocabulary, timing instruments, resource attributes, correlation, sampling and redaction are approved? How are policy updates handled? | Dana logging write-up to Tom; implementation ownership not settled | S13, S18-S19; completeness gap, no telemetry design chosen |
| OQ-020 | How is analyst assignment, reviewed-owner delivery and notification implemented? Is case posting manual only or automated? | Unassigned | S07-S08; Markdown paste decided, mechanisms not |

## Resolved Questions

| ID | Original question | Resolution | Date |
| --- | --- | --- | --- |
| OQ-001 | Can the missing root README be provided for existing-system context? | The [root README](../../README.md) is available, read, and integrated as existing-system context only. No requirements or other open questions changed. | 2026-10-07 |

## Glossary

| Term | Meaning in this PRD |
| --- | --- |
| TPRM | Third-party risk management; Priya's office and analysts |
| TCV | Total contract value, explicitly distinct from annual spend |
| Notice window | Policy-derived lead time before contract expiry; generation precedes its opening by thirty days |
| ProcureNet | Renewal/vendor system, described as Coupa underneath |
| CRO | Approval role named for Critical exceptions; full title not expanded in the transcript |
| TPRC | Review body named for Red financial health; full title not expanded in the transcript |
| QBR | Business-owner meeting context for an on-demand brief; full term not expanded in the transcript |
| Brief | Cited, analyst-reviewed risk summary, not a renewal recommendation |

## Integration Record

Integrate exited by user authorization on 2026-10-07. The user confirmed all
batch 4.a-4.m items remain open and authorized proceeding to Validate only.
Current phase: Validate, in progress. No new product evidence, decisions or
waivers were introduced by those confirmations.

| Reference | Integration disposition | Remaining limitation |
| --- | --- | --- |
| [Kickoff transcript](../meetings/renewal-kickoff-transcript.md) | Integrated as the sole requirements evidence through S01-S21 and the requirement, metric, action, and question registers. Recorded corrections and withdrawals are preserved. | Undecided scope, sourcing, ownership, retention, measurement and release matters remain open. |
| [Existing-system README](../../README.md) | Read and integrated into Existing-System Context only; excluded from all requirements evidence. | OQ-001 resolved; does not resolve any transcript-derived gap or prescribe the renewal capability's design. |

For Integrate responses 3.a-3.c on 2026-10-07, the user authorized the root
README for context only and closure of OQ-001 only if available. Earlier checks
found it absent. After the user added the file, it was read and integrated on
2026-10-07, resolving OQ-001. No replacement README or architecture context was
invented; the transcript remains the sole requirements evidence.

The user reported cross-checking the draft against the transcript and finding
no additional substantive passages omitted or misrepresented. The requested
00:11:56-00:12:09 annual-spend versus TCV clarification is now explicit in S08
and reinforces OQ-002 without resolving coverage. Other recorded corrections
and withdrawals remain unchanged. The transcript's general speaker-attribution
warning remains; Dana's specific correction at 00:25:12 is resolved. This
reference cross-check is not quality-gate clearance or PRD approval.

There are no additional references authorized as requirements evidence.
Both references are integrated in their permitted roles, source corrections
are reconciled, and supporting evidence is linked. Validate entry is authorized;
Validate exit is blocked by its quality report. Finalize and PRD approval remain
unauthorized. The earlier Build assessment is historical, not a new pass or
approval. OQ-001 is resolved; the other 19 open-question entries remain unchanged
and retain their unresolved aspects.

## Validation Record

The PRD Quality Reviewer reassessed the corrected draft in Validate and returned
FAIL: Validate exit BLOCKED, Finalize NOT_EVALUATED. Latest evidence:
[reassessment findings](../../.copilot-tracking/prd-sessions/vendor-renewal-risk-brief.validate-02-findings.yaml)
and [reassessment report](../../.copilot-tracking/prd-sessions/vendor-renewal-risk-brief.validate-02-quality.yaml).
The [initial findings](../../.copilot-tracking/prd-sessions/vendor-renewal-risk-brief.validate-findings.yaml)
and [initial report](../../.copilot-tracking/prd-sessions/vendor-renewal-risk-brief.validate-quality.yaml)
remain preserved as historical evidence.

The reassessment contains 1 RISK, 5 CAUTION and 3 COVERED findings, with earlier
covered findings consolidated. All three requested drafting defects are cleared;
VQ-009 is now COVERED, and VQ-007 retains only measurement/evidence gaps. No
independent remaining wording defect was identified. FR-to-AC and
FR-to-goal links both pass at 100%; full SMART assessment passes for none of
the three goals. Unverified feasibility and incomplete interpretation and
verification conditions prevent Validate exit. These findings do not authorize
answers to the 19 open questions, which remain open without waivers.

The initial reviewer identified three drafting defects in VQ-007/VQ-009. At the
user's request, AC-008 now explicitly flags an exception expiring two weeks
after renewal as a risk of "renewing into a breach" (S05, 00:04:21-00:04:35).
AC-009 now checks current TCV for every renewal independently of the separate
threshold-crossing re-sourcing flag (S05, 00:04:35-00:05:02). FR-013 now references
AC-013 and AC-017 through AC-021. These corrections preserve the existing
requirement IDs and do not settle OQ-017 or vendor coverage.

### Evidence-Based Dispositions

These dispositions refer to the initial Validate findings. They preserve
transcript limitations rather than supply missing decisions, claim feasibility,
or grant waivers. All 19 unresolved questions remain open. The strict Tier 1
target of under forty-five minutes including review against an approximate
three-hour baseline remains confirmed; its measurement details remain open.

| Initial finding | Evidence limitation | Retained questions | Disposition |
| --- | --- | --- | --- |
| VQ-003 | Coverage is explicitly deferred (S08); staleness, citation granularity, complete approval mappings, monetary equality/basis and incident anchors are not decided (S02, S05-S06, S17). | OQ-002, OQ-008, OQ-009, OQ-010, OQ-017, OQ-018 | Retain the interpretation gaps; do not select coverage or invent boundary rules. |
| VQ-004 | Production sourcing, cost and retention are deferred; reviewed delivery and pilot are tentative; Records consultation is unowned (S08-S13, S19-S20). Additional operating and workflow details are not decided. | OQ-003 through OQ-007, OQ-014 through OQ-016, OQ-020 | Keep governance and operating gaps open; do not assign owners, periods, dates or mechanisms. |
| VQ-006 | Prototype work and a tentative pilot are assignments/proposals, not demonstrated production feasibility; source access and production decisions remain unresolved (S09-S12, S19). | OQ-003, OQ-005, OQ-006, OQ-007, OQ-014 | Record feasibility as unvalidated, not impossible or accepted. |
| VQ-007 | Generation/analyst targets and edit preservation are stated, but measurement windows, scoring thresholds and evidence representation are not decided (S12-S15, S19). | OQ-011, OQ-012, OQ-013, OQ-019 | Keep measurement/evidence gaps open; only the separate AC-008/AC-009 drafting defects are corrected from S05. |
| VQ-010 | No additional scalability, portability, availability, accessibility or operating targets were decided; logging detail is an assigned follow-up (S13, S19). | OQ-006, OQ-007, OQ-015, OQ-019 | Retain category/target gaps without importing standards or prescribing technology. |
| VQ-011 | The Tier 1 target is confirmed, but its measurement period, goal horizons, outcome comparators and quantitative correction-quality threshold are not decided (S14-S15, S19, S21). | OQ-012, OQ-013 and linked scope/governance questions | Retain SMART deferral; do not invent targets, rates or dates, or reopen the confirmed time target. |

The reassessment accepts these as accurate evidence-based dispositions, not
answers or waivers. VQ-003, VQ-004, VQ-006, VQ-007, VQ-010 and VQ-011 persist
because the underlying questions remain unsettled. No new product decision or
approval is inferred. The PRD remains in review, in Validate, with exit blocked.

The Exercise 2 traceability audit subsequently added inferred NFR-009 and
AC-022 from S06 and S20. The Validate-02 report above predates that edit and is
historical for the amended draft; rerun the reviewer before relying on a verdict
for the current text. No approval, phase exit, or question resolution follows
from this audit.

## Sign-Off

### Approval Checklist

* Sponsor identified: Priya Raman; no PRD approval recorded
* Product owner and formal PRD approvers: undecided, OQ-014
* Technical feasibility: not validated; Tom is assigned options/prototype work
* Quality acceptance: not approved; evaluation criteria remain OQ-013
* Records/compliance retention acceptance: unresolved and unowned, OQ-006
* Approval date: none

### Waivers

None granted. Open questions are not waivers or implied acceptance.

### Handoff Readiness

In review, not approved. The user authorized Validate only and confirmed that
the remaining questions stay open. Implementation readiness remains blocked by
scope, sourcing, governance, measurement and release gaps. Validate exit awaits
resolution of the review's blocking findings; Finalize and PRD approval are not authorized and require
asking the user first. No tracker handoff or mutation is requested. Counts: 3 goals,
16 functional requirements, 9 non-functional requirements, 5 constraints,
22 acceptance criteria and 19 open questions; OQ-001 is resolved. Coverage links are 100.0%
FR-to-AC and 100.0% FR-to-goal, not evidence of implementation or approval.

## Disclaimer

> [!CAUTION]
> **Disclaimer:** This agent is an assistive tool only. It does not provide product management approval, technical feasibility validation, or business sign-off and does not replace product managers, engineering leads, business stakeholders, or other qualified human reviewers.
> The output consists of suggested requirements, acceptance criteria, and product specifications to support a user's own product planning and decision-making.
> All Product Requirements Documents, functional requirements, non-functional requirements, and constraint definitions generated by this tool must be independently reviewed and validated by appropriate product and engineering reviewers before adoption.
> Outputs from this tool do not constitute product approval, requirements sign-off, or engineering commitment.

## Document Metadata

* Template version: 1.0.0, requirements-author PRD full template
* Structure adapted from Microsoft HVE-Core; product content grounded only in the kickoff transcript
* Source meeting: 2026-09-22; authored 2026-10-07
* No external research, policy-corpus verification, or architecture decision performed
* Lifecycle status: In Review; Validate in progress, unresolved decisions retained without proposed answers
