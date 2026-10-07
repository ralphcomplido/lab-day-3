---
title: Lab Log
description: Notes from the vendor renewal risk brief kickoff transcript.
---

## Decisions Made

* The brief supports a human renewal decision; it must not recommend whether to renew. Put blockers near the top. (00:00:57, 00:33:03, 00:33:16)
* Every statement must cite a policy source or source record. If it cannot be cited, omit it. Source-record citations should link to the underlying finding or record. (00:01:38-00:02:27)
* Generate the brief 30 days before the policy-defined renewal notice window opens, not 30 days before expiry. Derive the window from policy rather than hard-coding it. (00:03:47-00:04:03, 00:36:43-00:37:01)
* Include vendor tier; open findings and exceptions with expiry dates; current total contract value and a re-sourcing flag when the renewal crosses $250,000 from an original award below that amount without a sole-source justification; the four latest scorecards, newest first, with dimensions and any open improvement plan; Treasury's flag, review date, and watch-list status; incidents from the last 12 months and notification-deadline performance; required approvers and deadlines; and the exit-plan deadline. Do not compute the vendor-owned scorecard rating. (00:04:14-00:07:10, 00:05:06-00:05:26)
* A Red Treasury flag blocks extension until TPRC review. A Critical or High finding without an exception prevents approval. The business owner always approves; exception approvers depend on tier, Critical exceptions go to the CRO, and Tier 1 renewals need the TPRM Office concentration check. (00:05:29-00:05:40, 00:06:38-00:06:59)
* The brief covers incidents in the trailing 12 months, even though the procedure's broader incident scope is during the contract term. Analysts can retrieve the full term when needed. (00:05:47-00:06:03)
* Deliver Markdown suitable for a ProcureNet case comment. Business owners may request a brief on demand, but it follows the same analyst-review process as scheduled briefs; same-day turnaround was considered acceptable. (00:10:00-00:10:53, 00:12:46-00:13:47)
* Target generation time is under two minutes, separate from review. State when source data is unavailable or stale; never guess or leave a blank that could imply no issue. (00:20:39-00:21:12, 00:32:20-00:32:57)
* Log the source records shown to the model and retain analyst edits before and after review. The brief identifies the reviewer by name, not phone number. (00:22:20-00:24:20, 00:42:04-00:42:21)
* Tier 1 success target: reduce analyst effort from an approximate three hours to under 45 minutes, including review. (00:29:05-00:30:05, 00:44:39-00:44:51)
* Drafting vendor negotiation emails is out of scope for v1. (00:26:28-00:27:37)

## Decisions Deferred

* **Initial scope:** Marcus proposed all vendors (about 340 renewals/year); Priya proposed Tier 1 and 2 (about 65/year); Lena proposed contracts over $250,000 in total value. Priya took the choice offline with Lena and Marcus. (00:02:31-00:03:02, 00:11:11-00:12:41)
* **Production data source:** options are the nightly Coupa CSV, a ProcureNet API that is not yet accessible, or indexing contract PDFs. Tom will compare them. The CSV is agreed only for a one-vendor prototype, not as the production choice. (00:15:15-00:18:09, 00:39:53-00:40:12)
* **Cost per brief:** $1 was discussed as an initial ceiling and $0.50 as a desired target, but the team will settle the number after a prototype. (00:21:12-00:22:09)
* **Retention and Records ownership:** renewal reviews are retained seven years, while the discussed model-input logs are retained thirteen months (with raw prompts for 30 days where personal data is present). The team must ask Records how these requirements fit together; no owner was assigned. (00:23:03-00:24:06, 00:41:23-00:41:58)

## Contradictions and Tensions

* **Tier 1 notice period:** Marcus initially said 90 days (00:03:18). Priya later checked the procedure and corrected it to 120 days for Tier 1; Tier 2 is 90, Tier 3 is 60, and Tier 4 is 30. The correction gives a Tier 1 generation point 150 days before expiry. Use the procedure as the authority, not the initial recollection. (00:36:12-00:37:01)
* **Renewal scope:** stakeholders proposed incompatible scope rules, and the meeting ended without choosing one. This is an open decision, not a resolved requirement. (00:02:31-00:02:54, 00:11:11-00:12:41)
* **Incident lookback:** the procedure covers incidents during the contract term, while the brief is intentionally limited to 12 months. This difference was explicitly settled for the brief; it should not be mistaken for a full-term incident review. (00:05:47-00:06:03)
* **On-demand timing:** Lena asked to request a brief whenever and accepted same-day service; Priya said “Same day. Probably.” The analyst review requirement is clear, but the same-day service level remains tentative and should be validated. (00:10:30-00:10:53, 00:12:46-00:13:47)

## Implied Requirements

* **Human review gate:** Every brief, including an on-demand request, must be checked by a TPRM analyst before reaching the business owner. This follows from Priya's stated workflow and refusal to let an AI brief reach the owner without analyst review. The system must prevent an unreviewed brief from being presented as final. (00:12:46-00:13:47)
* **Data minimization and restricted disclosure:** Source integrations and generated briefs must exclude unnecessary sensitive fields such as on-call contacts, bridge numbers, escalation chains, and vendor account-manager phone numbers. Dana described a prior broad Teams export that exposed mobile numbers; this is a concrete privacy and access-control risk, not merely a formatting preference. (00:06:03-00:06:35, 00:42:54-00:43:14)
* **Unresolved data ownership and quality:** Confirm which vendor-master/export field is authoritative for the business owner, and validate the CSV schema and freshness before relying on it. Dana explicitly questioned whether the vendor-master tab is the same source involved in the prior exposure, and Tom did not know. (00:15:50-00:16:19, 00:42:54-00:43:14)
* **Pilot details need confirmation:** Lena offered a Tier 1 card processor with an expiry “end of May,” but did not confirm the exact date or year. Confirm both before using it to plan the pilot. (00:39:08-00:39:41, 00:40:36-00:40:59)

## PRD Validation Review

### Initial Review

* Verdict: **FAIL**; Validate exit was blocked and Finalize was not evaluated.
* VQ-006 (High): production feasibility, sourcing, access, retention, cost, and release decisions were unvalidated.
* VQ-003 (High): scope and several operational boundaries remained undecided.
* VQ-004 (High): retention, Records ownership, data controls, delivery, and governance remained incomplete.
* VQ-007 (High): measurement and evidence conditions remained open; the reviewer also identified missing checks in AC-008 and AC-009.
* VQ-009 (Medium): FR-013 did not reference all six linked approval and deadline criteria.
* VQ-010 (Medium): some NFR categories and operational targets were unspecified.
* VQ-011 (Medium): goals lacked settled measurement horizons and feasibility evidence for full SMART assessment.

### Re-Review

The three transcript-supported drafting defects were corrected:

* AC-008 now checks for an exception expiring after renewal as a risk of renewing into a breach.
* AC-009 now checks current TCV generally and separately checks the re-sourcing threshold condition.
* FR-013 now references AC-013 and AC-017 through AC-021.

The updated reviewer verdict remains **FAIL / BLOCKED**. The reviewer found no remaining independent wording defect and confirmed both requirement-link coverage measures at 100%. Remaining findings are recorded as unresolved evidence or decision gaps, not as proof that the capability is impossible:

| Finding | Severity | Disposition |
| --- | --- | --- |
| VQ-006: production feasibility | High | Sourcing, access, cost, retention, and release decisions remain unvalidated; this is not a finding that the capability is impossible. |
| VQ-003: scope and interpretation | High | Scope and operational boundary rules remain open. |
| VQ-004: governance and completeness | High | Retention, ownership, data controls, and workflow gaps remain open. |
| VQ-007: verification | High | Measurement and evidence conditions remain open; the AC-008 and AC-009 drafting defects are cleared. |
| VQ-010: NFR maturity | Medium | Unspecified categories and targets remain gaps; no obligations were invented. |
| VQ-011: SMART goals | Medium | Measurement horizons and comparators remain open; the confirmed Tier 1 target of under 45 minutes including analyst review is preserved. |

At this review, 19 open questions remain. The PRD remains an unapproved draft in Validate; Validate exit is blocked, Finalize is not evaluated, and no approval or finalization is authorized. Formatting and payload-consistency checks passed, but they do not change the PRD Quality Reviewer verdict.

## Exercise 2 Traceability Audit

The table classifies every functional and non-functional requirement in the
amended PRD. Workflow-derived requirements are classified as inferred; open
decisions remain open questions rather than requirements with invented answers.

| PRD requirement | Transcript evidence (timestamp) | Classification | Notes |
| --- | --- | --- | --- |
| FR-001: Generate 30 days before the policy-derived notice window opens | 00:03:47-00:04:03; 00:36:12-00:37:01 | confirmed | Trigger and policy-derived window are confirmed; covered vendor population remains OQ-002. |
| FR-002: Allow a business owner to request a brief on demand through the analyst-review flow | 00:10:00-00:10:53; 00:12:46-00:13:47 | confirmed | Request path and review flow are agreed; coverage remains OQ-002 and firm same-day timing remains OQ-004. |
| FR-003: Require analyst review and correction before owner delivery | 00:12:46-00:13:47 | inferred | The workflow is described rather than labeled a product requirement; the human review gate follows from Priya's stated process. |
| FR-004: Cite every statement to policy or source records; omit uncitable claims | 00:01:38-00:02:27 | confirmed | Click-through for findings and policy-section references are explicit. |
| FR-005: Provide Markdown suitable for ProcureNet case comments | 00:10:00-00:10:30 | confirmed | Markdown was selected because Word-table formatting breaks in the case. |
| FR-006: Put blockers first and do not recommend or decide renewal | 00:00:57; 00:32:57-00:33:22 | confirmed | Priya reserves the decision for the business owner and Lena requests blockers at the top. |
| FR-007: Identify vendor and tier from the vendor master | 00:01:38-00:02:01; 00:04:14-00:04:21 | confirmed | Vendor and tier appear in the mock-up; tier is located in the vendor master. |
| FR-008: Include open findings and exceptions with expiry dates and timing risk | 00:04:14-00:04:35 | confirmed | An exception expiring after renewal may mean renewing into a breach. |
| FR-009: Show current TCV and flag the stated re-sourcing threshold condition; omit value history | 00:04:35-00:05:02 | confirmed | Full value history was withdrawn; exact equality and monetary basis remain OQ-017. |
| FR-010: Show four latest scorecards, dimensions, open improvement plan, and vendor-manager rating | 00:05:06-00:05:26 | confirmed | The last-four choice supersedes the initial last-scorecard suggestion; do not compute the rating. |
| FR-011: Show Treasury flag, review date, watch-list status, and Red blocker | 00:05:26-00:05:47 | confirmed | Red blocks extension pending TPRC review. |
| FR-012: Cover incidents in the last 12 months and notification-deadline performance | 00:05:47-00:06:03 | confirmed | The meeting chose a 12-month brief scope over the procedure's full-term scope. |
| FR-013: Show policy-cited approvers and deadlines, including stated approval rules | 00:06:38-00:07:10; 00:03:29-00:03:42 | confirmed | Complete mappings and valid-exception details remain OQ-010. |
| FR-014: Disclose unavailable or stale sources; never guess or leave misleading blanks | 00:32:20-00:32:57 | confirmed | Priya explicitly rejects guessing and blank-as-clear implications. |
| FR-015: Identify reviewer by name, not phone number | 00:42:04-00:42:21 | confirmed | Explicitly agreed. |
| FR-016: Preserve generated and analyst-edited versions | 00:24:14-00:25:24 | confirmed | Priya requests before/after edits as evidence of correction quality. |
| NFR-001: Generate in under two minutes, excluding review | 00:20:39-00:21:12 | confirmed | Timing conditions and workload remain OQ-011. |
| NFR-002: Disclose unavailable or stale source data | 00:32:20-00:32:57 | confirmed | Staleness thresholds and partial-release rules remain OQ-008. |
| NFR-003: Retain evidence of the exact source records shown to the model | 00:22:20-00:23:03 | confirmed | Record representation, integrity, access, and retention details remain OQ-006/OQ-007. |
| NFR-004: Show reviewer name, not phone number | 00:42:04-00:42:21 | confirmed | No broader field allowlist was agreed. |
| NFR-005: Derive scheduling from the policy notice window | 00:36:43-00:37:01 | confirmed | Tom explicitly rejects hard-coded notice-window numbers. |
| NFR-006: Preserve before/after edits for quality evaluation | 00:24:14-00:25:24 | confirmed | Quantitative correction threshold and measurement window remain OQ-013. |
| NFR-007: Preserve useful structure when Markdown is pasted into the case | 00:09:53-00:10:30 | confirmed | Paste-ready formatting was the stated need; exact rendering checks operationalize it. |
| NFR-008: Support ProcureNet Markdown case comments | 00:10:00-00:10:30 | confirmed | Tom states case comments take Markdown and it pastes cleanly. |
| NFR-009: Exclude unnecessary contact details from the renewal brief | 00:06:03-00:06:35; 00:42:54-00:43:14 | inferred | The incident-table field warning and prior mobile-number exposure imply minimization. Exact source-field, access, and logging controls remain OQ-007. |

Traceability result: 25 requirements reviewed, 0 classified invented, 2
inferred, and 23 confirmed. No PRD requirement uses a deferred alternative as a
settled decision. Unresolved applicability or implementation boundaries are
identified in the Notes column and retained in the PRD's open questions.

### Reverse Check

All confirmed decisions recorded in the Exercise 1 notes are represented in the
PRD, including the notice-window trigger, brief contents, citations, approval
rules, human decision authority, 12-month incident lookback, analyst edits, and
performance targets. The four explicit deferrals remain open: vendor coverage
(OQ-002), production data source (OQ-003), cost (OQ-005), and retention/Records
ownership (OQ-006). No decision was inferred for these items.

The two requirements implied by the meeting are accounted for:

* The process description implies a required analyst review before delivery;
	this is FR-003 and AC-003.
* Dana's prior broad-export incident implies excluding unnecessary contact
	details from the brief; this is inferred NFR-009 and AC-022. Detailed field,
	access, and logging controls remain open under OQ-007.

No other confirmed Exercise 1 decision was found missing from the PRD.

### Four Traps

| Trap | PRD treatment | Audit result |
| --- | --- | --- |
| Scope disagreement: all vendors, Tier 1/2, or TCV over $250,000 | OQ-002 keeps coverage undecided; S08 records Priya's annual-spend versus Lena's total-contract-value clarification. | Correct. The clarification distinguishes proposals but does not choose scope. |
| Incorrect early Tier 1 notice period | DD-001 and AC-001 use the corrected 120-day Tier 1 window, 90/60/30 days for Tiers 2/3/4, and policy-derived scheduling 30 days before the window opens. | Correct. Tier 1 generation is 150 days before expiry, not 120 or 30. |
| Withdrawn full contract value history request | DD-002 and FR-009 retain current TCV and the re-sourcing flag, not amendment history. | Correct. The request was withdrawn at 00:04:35. |
| Two requirements implied rather than labeled as requirements | FR-003/AC-003 cover analyst review; inferred NFR-009/AC-022 cover excluding unnecessary contact details. | Present after this audit. The latter is inferred from Dana's exposure story; implementation controls remain open. |

The inferred privacy requirement was added to the PRD during this audit. The
prior Validate-02 quality report predates that edit and must be rerun before it
is treated as a review of the amended PRD. The draft remains unapproved, and
the 19 unresolved questions remain open.

## Exercise 3 Deployment Diagram

The diagram below represents all ten resources declared in `infra/main.bicep`.
The outer boundary is the implicit resource group scope; the file declares no
VNet or subnet.

```text
+-- Resource Group ------------------------------------------------------+
|                                                                        |
|  +-- Foundry account [foundry] ------------------------------------+   |
|  |  +-- Project [project: policy-desk]                             |   |
|  |  +-- Model deployment [chatModel: gpt-5-mini]                   |   |
|  |  +-- Model deployment [embeddingModel: text-embedding-3-small]  |   |
|  +-----------------------------------------------------------------+   |
|                                                                        |
|  +-- Log Analytics workspace [logs; 90-day retention]             |   |
|  +-- Storage account [auditStore; Standard_ZRS; shared key off]   |   |
|                                                                        |
|  +-- Container Apps environment [appEnv] -------------------------+   |
|  |  +-- Container App [app; internal ingress; target port 8000]   |   |
|  +-----------------------------------------------------------------+   |
|                                                                        |
|  Role assignment [appCanCallModels]                                    |
|  Role assignment [appCanWriteAudit]                                    |
+------------------------------------------------------------------------+

app -- PROJECT_ENDPOINT (Foundry endpoint + project name) --> project
app -- MODEL_DEPLOYMENT ------------------------------------> chatModel
app -- EMBEDDING_DEPLOYMENT --------------------------------> embeddingModel
app -- AUDIT_BLOB_ENDPOINT ---------------------------------> auditStore
appEnv -- appLogsConfiguration -----------------------------> logs
app.identity.principalId --> appCanCallModels --scope------> foundry
app.identity.principalId --> appCanWriteAudit --scope------> auditStore
```

### Bicep Cross-Check

* Resource inventory: Foundry account, project, two deployments, Log Analytics
	workspace, storage account, Container Apps environment, Container App, and
	two role assignments are all represented.
* The app-to-project/model/storage labels correspond to `PROJECT_ENDPOINT`,
	`MODEL_DEPLOYMENT`, `EMBEDDING_DEPLOYMENT`, and `AUDIT_BLOB_ENDPOINT` in the
	app container environment variables.
* The environment-to-Log-Analytics edge corresponds to
	`appEnv.properties.appLogsConfiguration`, which references `logs`.
* Both identity edges use `app.identity.principalId`; the role-assignment
	scopes are `foundry` and `auditStore`, respectively.
* The app ingress is internal (`external: false`); Foundry public network
	access is enabled. No network resource or subnet is declared.

## Exercise 4 Architecture Review

Review record: `.copilot-tracking/reviews/architecture/2026-10-07/vendor-data-source-architecture-review.md`.
The reviewer grouped reliability and operational burden in one pillar finding;
the disposition below addresses both concerns separately. All four findings are
accepted. Acceptance records the reviewer's evidence-based concerns; it does not
approve a production source, close PRD questions, or grant organizational
authority.

| Finding | Disposition | Rationale | Effect on ADR |
| --- | --- | --- | --- |
| Production API-first selection is not evidence-supported | Accepted | API access is pending, coverage and controls are unverified, the production decision owner is unassigned, and the Bicep has no vendor-source integration. | Clarify that API-first is a lab comparison candidate only and production source selection is deferred. Keep ADR status proposed; no production option is approved. |
| Vendor-source security controls are unresolved | Accepted | Existing Bicep roles cover Foundry and audit storage only. It defines no vendor-source identity or permissions; field allowlists, source access, logging, redaction, and contact-data controls remain open after a prior exposure. | Add these as consequences and pre-implementation verification conditions. Preserve OQ-006 and OQ-007; no candidate is preferred on security yet. |
| Reliability and operational burden are not comparatively validated | Accepted | API availability/latency and export freshness/delivery/schema risks are unmeasured; a hybrid adds reconciliation and support work. Failure handling, recovery, and operating ownership remain open. | Record that no option is ranked end to end and require like-for-like validation. Preserve OQ-008, OQ-011, OQ-015, and OQ-016; production selection remains deferred. |
| No cost basis supports choosing an option | Accepted | API, export, and hybrid costs, reruns, and accounting boundaries are unmeasured; annual volume is planning context only. | Add the missing cost comparison to consequences and validation. Preserve OQ-005 and do not claim a cost-based preference. |

No findings were rejected. The ADR retains API-first only as the lab's
candidate for comparison; its frontmatter remains `proposed`, organizational
approval remains unassigned/TBD, and the PRD's open questions remain open.

## Exercise 5 Performance and Reliability Plan

Plan: `.copilot-tracking/performance-plans/2026-10-07-performance-slo-plan.md`.
The plan cites PRD requirement IDs, retains cost per brief as open under OQ-005,
and labels proposed profiles and targets as assumptions rather than approved
commitments. No load tests were run; the planner produces a test plan, not test
execution.

### Alert Choice

Choose generation duration (NFR-001) as the production alert signal. It is the
only approved quantitative SLO, applies to both scheduled and on-demand brief
generation, and directly reflects the meeting's under-120-second requirement,
excluding analyst review. The plan's p95 aggregation, 28-day window, and 5%
error budget are assumptions, not approved alert thresholds; validate them with
the owning team before configuring a production alert.

### Unsourced Assumptions and Open Targets

* Generation p95, 28-day measurement window, and 5% error budget are assumptions;
	NFR-001 establishes only the under-120-second duration requirement. (OQ-011)
* A 99% successful-generation target, 28-day window, and 1% failure budget have
	no agreed source. (OQ-015)
* A five-minute p95 scheduled-trigger-lag target, 28-day window, and 5% error
	budget have no agreed source. (OQ-015, OQ-016)
* A 95% same-business-day reviewed-delivery target, its 28-day window, and its
	error budget are assumptions; same-day delivery was tentative, not an approved
	SLA. (OQ-004, OQ-015)
* Steady, peak, spike, and soak concurrency/rate/duration profiles are proposed
	test scenarios, not sourced traffic commitments. The 260-working-day year used
	to derive working-day averages is also an assumption; the transcript's annual
	volumes are planning estimates only. (OQ-002, OQ-014, OQ-015)
* An isolated pre-production test environment using synthetic or approved
	de-identified snapshots is proposed, not specified by the transcript or PRD.
* Proposed P0/P1 backlog priorities are not approved product priorities or a
	MoSCoW decision. (OQ-014)
* Metric names, dimensions, spans, sampling, and telemetry/redaction details are
	proposals; approved telemetry vocabulary and evidence handling remain open.
	(OQ-006, OQ-007, OQ-019)
* Cost per brief, rerun accounting, and the cost cap remain open under OQ-005;
	no numeric cost target was adopted from the meeting's proposals.

The cited annual volumes (about 340 total renewals and about 65 Tier 1/2) are
transcript-supported estimates. Daily rates derived from them are arithmetic
planning context, not committed throughput or concurrency requirements.