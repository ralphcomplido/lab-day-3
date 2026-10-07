---
id: "0001"
title: "Vendor Renewal Brief Data Sourcing"
description: "Proposed API-first sourcing for vendor contract, performance, and findings data."
author: "ADR author (lab exercise)"
ms.date: "2026-10-07"
ms.topic: reference
status: proposed
proposed_date: "2026-10-07"
accepted_date: null
deciders:
  - "Organizational accountable decider: unassigned / TBD (PRD OQ-003)"
  - "ADR author (lab exercise selection only; not stakeholder approval)"
consulted:
  - "TPRM Office"
  - "Procurement"
  - "Engineering"
  - "Integration team (dependency)"
  - "CISO Office"
informed: []
tags:
  - vendor-renewal
  - data-sourcing
supersedes: null
superseded-by: null
related:
  - path: "../../project-planning/vendor-renewal-risk-brief.md"
    relation: informational
asr_triggers:
  - kind: performance
    evidence: "PRD NFR-001 and OQ-011; transcript 00:20:39-00:21:12"
    note: "Sourcing choices affect brief-generation latency against the under-two-minute target."
  - kind: security
    evidence: "PRD OQ-007 and NFR-009; confirmed least-privilege driver"
    note: "Source access and field selection affect authorization and data protection."
  - kind: maintainability
    evidence: "Transcript 00:16:19-00:16:45; PRD OQ-003"
    note: "CSV column-change risk and schema stability affect integration maintenance."
  - kind: cost
    evidence: "Transcript 00:21:12-00:22:09; PRD OQ-005"
    note: "Sourcing choices may change operating cost; measure it, target remains undecided."
affected_components:
  - "policy-desk vendor renewal brief source-access boundary"
  - "ProcureNet/Coupa API integration (proposed)"
  - "Contract-PDF repository (optional clause supplement)"
success_criteria:
  - metric: "required_source_coverage"
    target: "Required contract, scorecard, finding, and exception fields verified; details remain open under OQ-003 and OQ-007."
    measurement_window: "Before implementation commitment; owner and schedule TBD."
    source: "API contract and PRD FR-007 through FR-010, OQ-003, OQ-007."
  - metric: "brief_generation_duration"
    target: "Under 120 seconds, excluding analyst review."
    measurement_window: "Integration validation; workload and percentile remain open under OQ-011."
    source: "PRD NFR-001 and OQ-011."
  - metric: "least_privilege_access_verification"
    target: "Required access controls demonstrated; field allowlist remains open under OQ-007."
    measurement_window: "Before implementation commitment; reviewer and cadence TBD."
    source: "PRD OQ-007 and NFR-009."
  - metric: "cost_per_generated_brief"
    target: "Measure cost; cap remains undecided under OQ-005."
    measurement_window: "API feasibility validation; sample and rerun accounting TBD."
    source: "PRD OQ-005; transcript 00:21:12-00:22:09."
---

## Context

The README describes policy-corpus Q&A using a local retrieval index and one policy-search tool. The Bicep deployment configures the app, Foundry, and audit storage, but no ProcureNet/Coupa connector. The renewal brief therefore needs a production source path for contract attributes, scorecards, and TPRM findings/exceptions. The kickoff identifies a nightly Coupa CSV for prototype use, a pending API request, and optional contract-PDF indexing, while leaving production sourcing unresolved. API-first is a lab-only proposed decision; organizational approval, coverage, access, latency, and cost remain unsettled.

> Source: [Kickoff transcript, 00:15:15-00:18:09](../../meetings/renewal-kickoff-transcript.md). CSV is for prototype use, API access is pending, PDF indexing is a clause alternative, and production sourcing was left open.
> Source: [Vendor renewal risk brief PRD](../../project-planning/vendor-renewal-risk-brief.md). OQ-003 leaves source strategy, access, schema, joins, and decision ownership unresolved.
> Source: [README](../../../README.md). The documented system is policy-corpus Q&A, not a vendor-record integration.
> Source: [Bicep deployment](../../../infra/main.bicep). The declared app deployment has no ProcureNet/Coupa connector.

## Decision Drivers

* Prioritize authoritative, accurate source data and traceability first.
* Then prioritize reliable access, freshness, stable schemas, and least-privilege data handling.
* Measure latency and cost, but do not trade away correctness, citations, or data protection.

## Considered Options

* Governed batch exports from ProcureNet/Coupa.
* API-first structured access to ProcureNet/Coupa.
* Source-specific hybrid of governed exports and APIs.

Contract-PDF indexing remains a separately evaluated, optional supplement for contract clauses. It is not presumed selected or expected to supply scorecards or findings. The nightly CSV remains a prototype option, not a production decision.

## Decision Outcome

Lab-only candidate selected for comparison: "API-first structured access," because data authority, freshness, and traceability take priority over the CSV's immediate availability. Production source selection is deferred: API access, required coverage, security controls, reliability, and cost are unverified. This lab choice is not stakeholder approval; the organizational decider remains unassigned/TBD under OQ-003. ADR status remains proposed.

| Driver | Governed batch exports | API-first structured access | Source-specific hybrid |
|---|---|---|---|
| Authority and traceability | Depends on export ownership, stable IDs, and evidence retention. | Potential fit only if authoritative and traceable references are exposed; unverified, with no production preference established. | Can match paths by data set, but requires reconciliation. |
| Access and freshness | Nightly prototype fields may be stale; schema governance unknown. | Potentially fresher, but access and coverage unverified. | Timing and access differ across source paths. |
| Least privilege | Depends on export filtering and distribution controls. | Depends on API scopes and field access; test required. | Requires consistent controls across multiple mechanisms. |
| Latency and cost | Avoids live calls, but ingestion and refresh cost need measurement. | Live calls may affect latency, availability, and cost; test against two minutes. | Adds operational and reconciliation cost; measure it. |

### Consequences

* Good, because an authorized API could provide fresher structured records and reduce reliance on a mutable nightly CSV if required fields and stable references are exposed.
* Bad, because API access is pending and scorecard, findings, and exception coverage is unverified.
* Bad, because API reliability, least-privilege permissions, and latency against the under-two-minute target must be tested.
* Neutral, because cost must be measured but the per-brief cap remains open under OQ-005.
* Bad, because least-privilege vendor-source access is not demonstrated by the current Bicep, which grants roles only for Foundry and audit storage. Source identity, permissions, field allowlists, network controls, evidence integrity, and handling of unnecessary contact data remain to be established under OQ-006 and OQ-007.
* Neutral, because no option is yet shown to be more reliable or operationally preferable end to end. Compare API availability and live-call latency with export freshness, delivery, and schema-change risks; include hybrid reconciliation and support burden. Failure, recovery, staleness, and operating ownership remain open under OQ-008, OQ-011, OQ-015, and OQ-016.
* Neutral, because there is no cost basis for preferring an option. Measure API access and integration, export delivery/refresh/storage, hybrid reconciliation/support, and reruns; the accounting boundary and cap remain open under OQ-005.
* PDF indexing is not selected; scan quality and page citations require separate evaluation if reconsidered.
* Production source selection remains deferred. If API coverage or access controls fail, reopen the comparison explicitly. Do not assume CSV or hybrid as fallback.
* No telemetry instruments, names, attributes, or retention periods are selected. Before implementation, specify API-boundary and source-evidence observability using the telemetry-foundations Trace Vocabulary, Metric Vocabulary, Log Vocabulary, and PII Handling sections; PRD OQ-006 and OQ-019 remain open.

## Pros and Cons of the Options

### Governed batch exports

* Good, because an existing nightly Coupa export is available for prototype work and can avoid live calls during generation.
* Good, because a governed snapshot may support traceability if stable IDs, schema controls, and retention are defined.
* Bad, because nightly delivery may be stale and column changes were raised as a risk.
* Bad, because production status and export coverage for scorecards and findings/exceptions are unconfirmed.

### API-first structured access

* Good, because an authoritative API with stable references could improve freshness and traceability.
* Good, because a stable API contract may reduce CSV column-drift exposure.
* Bad, because access is pending and has no recorded commitment.
* Bad, because required coverage, schema guarantees, freshness, and permissions are unverified; live calls add availability and latency dependencies.

### Source-specific hybrid

* Good, because each data set could use its verified authoritative source and access mechanism.
* Good, because a prototype export may remain useful while API coverage is investigated.
* Bad, because multiple paths increase join, schema, timing, and evidence-reconciliation complexity.
* Bad, because consistent least-privilege and point-in-time traceability are harder across different sources.

## Policy Desk Deployment Architecture

```text
+=========================== Resource Group ===========================+
|                                                                      |
|  +------- Container Apps managed environment -------------------+   |
|  |                                                               |   |
|  |  +----------------------+                                     |   |
|  |  | policy-desk app      |                                     |   |
|  |  | internal ingress    |                                     |   |
|  |  | target port: 8000   |                                     |   |
|  +--+----------------------+-------------------------------------+   |
|        | app system identity                  |                       |
|        v                                      v                       |
|  +-----------------------------+   +-----------------------------+   |
|  | appCanCallModels            |   | appCanWriteAudit            |   |
|  | scope: Foundry account      |   | scope: audit storage acct   |   |
|  | Cognitive Services OpenAI   |   | Storage Blob Data           |   |
|  | User                        |   | Contributor                  |   |
|  +-------------+---------------+   +--------------+--------------+   |
|                |                                  |                  |
|                v                                  v                  |
|  +-----------------------------+   +-----------------------------+   |
|  | Azure AI Foundry account    |   | Audit storage account      |   |
|  | project: policy-desk        |   | ZRS, shared key off        |   |
|  | gpt-5-mini deployment       |   +-----------------------------+   |
|  | text-embedding-3-small      |                                  |
|  | public network: enabled     |   +-----------------------------+   |
|  +-----------------------------+   | Log Analytics               |   |
|                                    | retention: 90 days          |   |
|                                    +---------------^-------------+   |
|                                                    |                 |
|                               Container Apps env ---+                 |
+======================================================================+

+---------------------------------------+
| ProcureNet/Coupa API                  |
| PROPOSED EXTERNAL SOURCE              |
| Not deployed or present in this Bicep |
+-------------------+------------------+
                    . . . proposed API flow only . . . > policy-desk app
```

### Legend

Solid arrows indicate dependencies, configured endpoints, or role assignments declared in Bicep. The outer box is the resource group; the nested box is the Container Apps managed environment. The dotted line is a proposed API relationship only; it is not implemented or declared in Bicep.

### Key Relationships

* The app receives the Foundry project endpoint and chat/embedding deployment names through its environment configuration.
* `appCanCallModels` assigns the app's system-assigned identity the Cognitive Services OpenAI User role, scoped to the Foundry account.
* `appCanWriteAudit` assigns the app's system-assigned identity the Storage Blob Data Contributor role, scoped to the audit storage account.
* The managed environment sends application logs to Log Analytics; the workspace retention is 90 days.
* The app ingress is internal. Foundry public network access is enabled in the Bicep.
* ProcureNet/Coupa is shown only as a proposed external API source. It is not deployed or present in the current Bicep; API-first remains proposed and unimplemented.

## Confirmation

Before implementation commitment, verify API access and fields for contract attributes, scorecards, findings, and exceptions; stable record references; least-privilege scopes; freshness; and availability. Measure end-to-end generation under two minutes excluding analyst review; workload and percentile remain open under OQ-011. Measure cost without inventing a cap; OQ-005 remains unresolved. Preserve the PRD requirement to omit uncited or unsupported assertions.

## Risks and Mitigations

* API access may remain unavailable. Do not begin implementation until access is granted; reopen the decision if required coverage or controls cannot be met.
* APIs may omit scorecards or findings/exceptions. Verify every required data set and field; do not infer coverage from contract API access.
* Live calls may exceed the generation target or be unavailable. Measure latency and availability; disclose unavailable or stale data per the PRD.
* Overbroad scopes or fields may expose unnecessary data. Test least-privilege access and an approved field allowlist; OQ-007 remains open.
* Contract PDFs may be unreadable scans. Keep indexing optional and separately assess scan quality and page citations.

## Rollback / Exit Strategy

Do not release the API integration until coverage, access controls, and performance pass validation. If required API data or permissions cannot be established, stop and reopen the decision. Do not silently switch to CSV or hybrid. Any later accepted production decision requires organizational approval; its accountable decider remains unassigned/TBD.

## Affected Components

* policy-desk vendor renewal brief source-access boundary
* ProcureNet/Coupa API integration (proposed, absent from current README/Bicep)
* Contract-PDF repository only if a separate clause-supplement decision is approved

## More Information

This ADR does not alter Treasury financials, ServiceNow incidents, policy citations, vendor coverage, cost thresholds, or retention requirements and questions in the PRD. No supersession relationship exists. Revisit the proposal after API access, coverage, and controls are tested or an organizational decision owner is assigned.
