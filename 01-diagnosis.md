# Exercise 1 — Diagnosis

## 1a. Flow analysis

- Total elapsed time: **34 days average; 41 days at the 90th percentile**.
- Total working time: **770 minutes (12.83 hours)**.
- Flow efficiency: **1.57% on a calendar-time basis** (`770 ÷ 48,960 minutes`). On an eight-hour business-day basis it is 4.72%; the convention must be held constant when comparing future results.
- Three longest waits: **reference outreach, 11 days**; **committee decision, 7 days**; **primary-source verification, 5 days**.
- Immediate flow constraint: **reference outreach and follow-up**, because it is the largest queue and depends on responses outside Meridian. The governing constraint is broader: exception decisions and scarce expert knowledge are batched through eleven experienced verifiers and a twice-monthly committee rather than carried forward as structured context.

In CEO language: “A credential takes 34 days, but people are actively working on it for less than 13 hours. More than 95% of the journey is waiting, so making individual tasks a little faster will not fix the client commitment; we have to remove queues and change how decisions are made.”

## 1b. Why the previous attempts did not move operations

| Initiative | Specific failure mechanism | Three-conditions diagnosis |
|---|---|---|
| Policy chatbot, 4% weekly usage | It was a destination product disconnected from the moment and system where work happened. Usage was treated as the result, with no workflow outcome, distribution mechanism, or feedback loop. | **Context:** three retrieval efforts and untaxed SharePoint content make answers inconsistent. **Identity:** no defined authority or boundary for the bot. **Accountability:** no link from answers to cycle time, rework, or decision quality. |
| Copilot for 140 engineers; release cadence unchanged | Local coding time was not the system constraint. A two-week release cadence is governed by integration, review, testing, deployment controls, dependencies, and technical debt. Speeding code production can add work to the queue without increasing throughput. | **Context:** architectural and operational knowledge remains fragmented. **Identity:** individual assistants are not actors with owned work or controlled handoffs. **Accountability:** self-reported speed is measured, but lead time, queue time, change failure, and deployment frequency are not attributed to changes. The VP is right: technical debt increases verification and integration cost and can be the release constraint. |
| Classification pilot, 91% in test, never shipped | The team optimized average model accuracy but did not design exception handling, provenance, thresholds, review queues, or a safe failure state. Compliance could not answer what happened to the 9%. | **Context:** test labels did not become operational evidence. **Identity:** no accountable actor owned a classification or override. **Accountability:** no traceability chain from input through model output, human review, routing, and correction. |
| Three independent retrieval systems | Duplicate solution-building occurred before shared discovery and ownership. Each team reconstructed the same context, created competing sources of truth, and increased maintenance and security surface. | **Context:** fragmentation is the failure itself. **Identity:** no owner had authority to establish a canonical service. **Accountability:** spend and outcomes were not attributed across systems, so duplication stayed invisible. |

## 1c. The three conditions

### 1. Shared context — most severe

Policy knowledge is spread across roughly 400,000 SharePoint files with no taxonomy; provider facts live in Oracle and the mainframe; workflow state is split between ServiceNow and a shared spreadsheet; three teams rebuilt retrieval separately; and crucial exception knowledge sits in the heads of eleven long-tenured verifiers. Intake, analysts, compliance, and committee members repeatedly reconstruct what happened and why. That reconstruction cost lands in the 5-, 11-, and 7-day queues, and in the verification team that answers exceptions.

### 2. Accountable execution — second

Meridian measures average elapsed time, P90, contractual misses, and step-level time, but the scenario does not show case-level ownership, reason-coded waits, decision provenance, exception outcomes, quality/rework, or cost by workflow. Work performed in the spreadsheet is partly invisible to ServiceNow. AI spend and activity were counted without tying them to operating measures. This is second because even perfect access to context will not produce an outcome if no one can trace decisions and exceptions.

### 3. Identity — third, but a launch blocker

No automated actors with explicit identities, least-privilege roles, histories, or revocation paths are described. Meridian does have a moderately governed Azure tenancy and a competent security team, which are foundations for managed identities, groups, and audit controls. Production actors need distinct non-human identities, scoped read/write permissions, approval boundaries, short-lived credentials, immutable activity histories, and named human owners. It ranks third only because the largest present loss occurs before agents exist; it becomes non-negotiable before deployment.

## 1d. The uncomfortable finding

The non-technology problem is governance: a 15-minute decision is allowed to wait seven days because the committee batches work twice monthly, while the operational system of record is optional enough that experienced staff work from a shared spreadsheet. I would tell Diane and the committee chair: “We cannot meet a 30-day promise reliably while preserving both of those operating choices. Technology can prepare better evidence, but you must decide who may approve routine cases, how exceptions are scheduled, and require the agreed workflow to be used.”
