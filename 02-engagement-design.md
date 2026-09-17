# Exercise 2 — Engagement design

## 2a. Outcome

### Primary measure

**Measure:** percentage of completed credentialing cases finished within 30 calendar days from received timestamp to enablement in all four systems.

**Baseline:** approximately **60%**, inferred from the scenario's statement that 40% miss the contractual commitment. In days 1–5, reproduce it from the prior six months: join ServiceNow case IDs to Oracle provider IDs and system-enablement timestamps, publish inclusion/exclusion rules, count completed cases, and reconcile a random 30-case sample against source records. Segment by insurer, provider type, complete/incomplete at receipt, and standard/exception path.

**Target:** **80% within 30 days by day 90**, while meeting the quality guardrail below. The target is a proposal to validate after the baseline query, not an achieved result.

**Reproducible method:** a version-controlled SQL definition and data dictionary calculate `(cases enabled within 30 calendar days / all eligible completed cases) × 100` weekly from immutable source timestamps. ServiceNow stores case/path/reason codes; Oracle and enablement logs provide terminal timestamps. A named operations analyst reruns it and signs the weekly snapshot.

**Falsification:** the intervention fails if, over the final four weeks, the eligible volume is representative and either on-time completion is below 80%, improvement versus the validated baseline is under 10 percentage points, or the quality guardrail is breached. Report median and P90 too, so cherry-picking around day 30 is visible.

### Guardrail

Measure **verified defects within 30 days of enablement per 100 completed credentials**, including missed sanctions, expired/incorrect licences, wrong provider attributes, compliance rework, and insurer returns. Baseline this by adjudicating the previous six months' audit and rework records. The guardrail is no statistically or operationally material deterioration from baseline; all high-severity misses receive independent review. Also show first-pass yield and manual override rate as diagnostics.

## 2b. First 90 days

### In scope

- One insurer/client segment with sufficient volume and a representative standard path.
- Receipt through committee decision and enablement, with emphasis on completeness, reference outreach, and committee queues.
- A canonical case record in ServiceNow; spreadsheet migration for the pilot cohort.
- Reason-coded waits, decision records, and a reproducible baseline/outcome dashboard.
- Read-only evidence gathering and draft preparation agents; controlled communications for reference outreach; humans retain regulated decisions.
- A curated corpus limited to current credentialing policies, checklists, templates, and authoritative primary-source links.
- Security threat model, data-residency validation, access reviews, audit retention, runbooks, and ownership transfer.

### Explicitly out

- Migrating the mainframe, cleaning all 400,000 SharePoint files, enterprise search, or replacing ServiceNow/Oracle.
- Claims correspondence classification, the policy chatbot, Copilot rollout, or consolidating all retrieval systems.
- Autonomous credential approval, final primary-source attestation, sanctions adjudication, contracting redesign, or rollout to all clients.
- New platform licences. These items either do not constrain the selected outcome, exceed 90 days, or add regulatory risk before the method is proven.

### First shipment

By the end of **week 2**, ship a production-used, human-owned **reference-outreach work queue for the pilot cohort** in ServiceNow. It records sent/received timestamps, channel, attempt number, response status, owner, next action, and reason-coded blockers; it produces approved drafts but a human sends them initially. Alongside it, publish the validated baseline query and weekly flow report. This is small but real: it attacks the 11-day wait and demonstrates context, identity, and accountability without autonomous risk.

### Ninety-day shape

- **Days 1–10:** shadow work, validate baseline, map exceptions, agree measurement contract, threat model, ship outreach queue/report.
- **Days 11–30:** curate context, standardize complete-at-receipt checks, capture outreach experiments, pilot daily routine-case review.
- **Days 31–60:** add read-only evidence collection and draft packets; introduce approved-channel outreach automation with response monitoring and immediate fallback.
- **Days 61–90:** expand only after gates pass, measure four stable weeks, document controls, train owners, and decide scale/stop/redesign.

## 2c. Workflow redesign

### Driveshaft version

Keep all nine stages and their queues. Use AI to extract application fields, draft reference emails, summarize verification evidence, and assemble committee packets. A plausible 30% reduction in the automatable portion of 770 working minutes saves at most 231 minutes, or **3.85 hours**. Against 34 elapsed days this is roughly **0.16 calendar day**; even eliminating all working time saves only 0.53 day. The process remains about 33.8 days and still misses the commitment often.

### Redesigned version

1. At receipt, create one ServiceNow case with a structured completeness checklist and source links. Resolve missing items immediately rather than after a 1.5-day queue.
2. Launch independent work in parallel once minimum identifiers are present: licence/board checks, malpractice review, and reference outreach. Do not wait for one to finish before starting another.
3. Treat reference outreach as a managed response funnel: confirm contact details with the provider, use the recipient's preferred approved channel, personalize from a named Meridian employee, schedule attempts, surface delivery failures, and escalate nonresponse. The 11 days are mostly external response latency plus passive follow-up, not two hours of composition.
4. Continuously recheck time-sensitive sources and expirations until decision rather than rerunning a full gate at the end.
5. Build a decision-ready packet as evidence arrives. Every fact carries source, retrieval time, confidence/status, and exception flag; later steps do not reconstruct prior work.
6. Create a policy-defined straight-through **review** path: low-risk, complete cases receive asynchronous review by delegated credentialing authority each business day. Exceptions go to a short weekly virtual session or an on-demand quorum. The committee retains policy and exception authority; this is not autonomous approval.
7. Trigger contract preparation and enablement readiness in parallel before final decision where reversible, then release only after recorded approval.

Target-state waits are: completeness ≤0.5 day, verification ≤2 days, malpractice ≤1 day, reference response median ≤5 days, packet preparation ≤0.5 day, decision ≤2 days, contracting ≤1 day, enablement ≤0.5 day. Because parallel paths are governed by the longest dependency rather than summed, a standard case could average **10–14 days**, with a conservative 90-day portfolio target of 80% within 30 days.

### Load-bearing expertise and human cost

During weeks 1–3, sample cases across all eleven verifiers and identify who is repeatedly consulted for sanctions, state-specific rules, ambiguous histories, insurer variations, and reference exceptions. Make two domain stewards and rotating reviewers part of the design team; externalize rules as examples, decision tables, and exception records, with peer validation. Their new role is to curate policy and adjudicate ambiguity—not silently repair every case.

The redesign is harder because it changes authority, cadence, visibility, and professional identity. Committee members must accept delegated daily review for routine cases; experienced verifiers must expose tacit judgment and may reasonably fear deskilling or head-count pressure; staff lose the flexibility of an unofficial spreadsheet; weak performance becomes visible. Adoption requires protected expert time, explicit no-surprise workforce communication, compensation/recognition for stewardship, training, appeal paths, and Diane's decisions. The driveshaft version avoids much of that conflict, which is exactly why its gain is small.

## 2d. Building the three conditions with existing systems

### Shared context

ServiceNow is the case system of record: structured status, owner, timestamps, blockers, evidence links, approvals, and next action. Oracle remains authoritative for provider data; the mainframe remains authoritative for eligibility; SharePoint holds governed documents and generated decision packets, referenced rather than copied into prompts when possible.

The first corpus is not 400,000 files. Credentialing owners nominate only current approved SOPs, payer rules for the pilot, checklists, templates, and decision examples—likely dozens to low hundreds. Each has owner, effective/expiry dates, jurisdiction/client tags, approval status, and canonical URL. Azure AI Search or an Azure-hosted index may index only this allow-listed library if already licensed; otherwise a small Azure service uses SharePoint/Graph metadata and retrieval under the caller's permissions. Document owners approve updates; expired documents are excluded automatically. Agents retrieve with citations; humans open the source from ServiceNow.

### Identity and enforcement

| Actor | Permissions and memory | Enforcement and boundary |
|---|---|---|
| Intake assistant | Read new pilot applications and curated rules; write extracted draft fields only to the pilot ServiceNow staging table. Case-scoped working memory; no cross-case conversational memory. | Microsoft Entra workload identity/managed identity, app roles and group claims; ServiceNow OAuth/API ACLs and field/table ACLs; SharePoint app-only access limited with `Sites.Selected`; Azure Key Vault for secrets; Conditional Access/workload policies where supported. Cannot approve, email, query unrelated sites, or write Oracle/mainframe. |
| Verification evidence assistant | Read minimum provider identifiers from ServiceNow/Oracle read replica or approved API and approved public/primary-source endpoints; write evidence drafts, source URL, timestamp, and hash to ServiceNow. | Separate Entra identity; Oracle read-only role/view plus row/client filters; ServiceNow ACLs; outbound Azure Firewall/private endpoints/allow-list; managed identity and Key Vault. Cannot modify sources, attest verification, or decide exceptions. |
| Reference outreach assistant | Read contact/case fields; generate approved drafts and, after a gated phase, send only approved templates through the approved Meridian channel; write delivery/response events. Short-lived per-case state. | Separate Entra identity; Graph/application access policy scoped to one shared mailbox (or ServiceNow notification role), ServiceNow ACLs, rate limits, recipient-domain controls, DLP, and kill switch. Cannot access clinical/claims data, attachments beyond allow-listed types, or approve cases. |
| Packet assistant | Read the case record and curated policy; write a draft packet to the restricted SharePoint pilot library and link it in ServiceNow. | Managed identity, `Sites.Selected`, library permissions/sensitivity labels, ServiceNow API ACL. Cannot change source evidence or record a decision. |
| Measurement job | Read approved timestamp/status views; write aggregate metrics, with no message sending or case decisions. | Managed identity; Oracle/ServiceNow read-only reporting roles; Azure job RBAC; aggregate output ACL. |

All identities have named business and technical owners, quarterly access review, automated credential rotation, disabled interactive login, per-environment separation, least privilege, and immediate revocation. Provider data stays in the approved Azure region and tenant. Azure Policy denies non-approved regions/resources; Private Link/VNet integration and firewall rules restrict paths; diagnostic logs flow to Log Analytics/Sentinel with retention agreed by compliance. Prompts/outputs are not used for model training under the approved enterprise service configuration, verified by security and legal before launch.

### Accountability

| Link | System of record |
|---|---|
| Baseline, primary outcome, guardrail, segmentation | Version-controlled SQL/data dictionary; weekly signed snapshot linked from ServiceNow |
| Case state, owner, waits, overrides, approval | ServiceNow audit history |
| Inputs/outputs, model/deployment/version, prompt/template version, citations, timestamps, actor ID | Append-only interaction record in Azure Log Analytics/Application Insights, correlated to ServiceNow case ID |
| Source evidence and final packet | Restricted SharePoint library with version history, retention label, hashes, and ServiceNow links |
| Architecture/policy/exception decisions | Lightweight decision record generated from the ServiceNow change/approval event |
| Azure access and security events | Entra audit/sign-in logs, Azure Activity Log, Key Vault diagnostics, Sentinel |
| Cost | Azure Cost Management tags for engagement, environment, service, and agent; unit cost divided by completed cases |

The trace is: outcome cohort → ServiceNow case → human/agent event → model and template version → cited source/evidence → approval or override → final enablement. Monthly restore and six-month audit-replay tests prove that the trail is usable, not merely stored.

## 2e. Hybrid split and handoffs

| Step | Split and reason | Context crossing the handoff |
|---|---|---|
| Receive/log | Both: agent extracts; intake confirms identity and ambiguous fields. Verification is cheap; a wrong provider identity contaminates everything. | In: original files, sender, timestamps. Out: structured fields, confidence, highlighted evidence, missing items; human returns corrections/reason. |
| Completeness | Both: rules pre-check; human resolves ambiguity and contacts provider. | Checklist version, missing evidence, citations, due date; human disposition updates canonical case and rule feedback. |
| Primary-source verification | Both: agent navigates/read-captures approved sources and detects deltas; credentialed human validates source authenticity, matches identity, interprets sanctions/limitations, and attests. Compliance consequence makes autonomous approval inappropriate. | Identifiers, jurisdiction, required sources → source URL, timestamp, raw response/screenshot/hash, match rationale, exception flag → human attestation/override and reason. |
| Malpractice history | Both: agent assembles and summarizes; trained verifier interprets disclosures and thresholds. | Claims/disclosure evidence, policy version, discrepancies → risk flags → signed disposition and rationale. |
| References | Both: agent drafts/schedules/tracks after controls; human initially sends, handles replies and escalations. | Contact provenance, approved template, case-minimum data, attempt history → delivery/reply classification → human correction/escalation; opt-outs and bad contacts flow back. |
| Committee packet | Agent drafts; analyst verifies completeness and narrative. | Complete evidence graph, open exceptions, cited policies → packet/diff → corrections stored as reusable examples. |
| Decision | Human: delegated reviewer/committee decides; agent checks required fields and records the signed result. Consequence and professional accountability are high. | Decision-ready packet and unresolved exceptions → decision, conditions, approver identity, rationale, next review date. |
| Contract | Both: rules/template populate draft; contracting reviews and releases. | Approved terms/provider data → validation exceptions → signed/countersigned status. |
| Enablement | Both: agent prepares four-system checklist and reconciliation; operations authorizes writes and resolves failures. | Approval and contract status, target identifiers → per-system confirmation/error → reconciled completion timestamp. |

Agents never turn uncertainty into a silent default. Low confidence, source mismatch, policy conflict, or missing evidence routes to a named human queue with the original evidence and a proposed next action.
