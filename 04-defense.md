# Exercise 4 — Defense

The labels distinguish answers directly derived from the framework from answers that require client-specific judgment. “Improvised” does not mean guessed; it marks where field validation is needed.

## Diane

### 1. “The last three vendors told me they would fix this. Why is this different?”

We are not asking you to believe a technology forecast. By week two, one real cohort will use the outreach queue and you will have a reproducible baseline. We have named the decision that software cannot make—committee delegation—and the conditions under which we stop. Each week you will see one operating outcome, its quality guardrail, cost, and the decisions blocking it. If the final four weeks do not meet the falsification test, we will call it unsuccessful.

**Basis: framework.** Bounded outcome, early shipment, accountable execution, falsification.

### 2. “The physicians do not report to me. How will you change the committee?”

I cannot promise that you can direct them. In the first month, you and the committee chair co-sponsor a design session using case data. We offer choices: delegated daily review for policy-defined routine cases; asynchronous physician review with a 48-hour service level; a weekly exception quorum; or leaving cadence unchanged and explicitly accepting that the 30-day target may not be reachable. We pilot one willing insurer or specialty, preserve physician authority over exceptions, and publish safety results. If no legitimate decision-maker agrees, the plan and target must change.

**Basis: improvised.** Stakeholder power and clinical governance require local knowledge.

### 3. “What if this does not work? What do I tell my CEO in November?”

Tell the CEO what was proven: Meridian established the baseline, isolated the largest constraints, tested a bounded change, protected credential quality, and stopped or redesigned based on pre-agreed evidence. The downside is capped to one cohort and 90 days; agents cannot approve credentials or alter sources. By November you will have either an improvement with an owned scale plan or a defensible finding about the process/governance constraint and the next investment—not another usage statistic.

**Basis: framework.** Evidence over attendance/activity, reversible scope, explicit controls.

### 4. “Can I do a smaller version first?”

Yes. Do only the first two weeks: validate the baseline and use the human-operated outreach queue on perhaps 25–50 cases. No autonomous sending, no committee change, and no production evidence agent. The exit test is that staff use the queue, timestamps are complete, no case is lost, and it reveals actionable reasons for the 11-day delay. It will not prove the 80% outcome, but it cheaply proves the method and data quality.

**Basis: framework.** Thin slice and first-two-weeks principle.

## VP of Engineering

### 5. “We already have Copilot. What are you adding?”

Copilot accelerates an individual's production of code. This engagement changes an operations workflow and installs the missing controls: a canonical case record, controlled workload identities, evidence provenance, human approval gates, outcome measurement, and support ownership. We may use Copilot while building, but it is not the intervention. If integration and technical debt are the constraint, we fund only the narrow reusable debt needed for a safe boundary and count engineering load in the result.

**Basis: framework.** Bottleneck argument and role architecture.

### 6. “Engineers will not write decision records. What happens then?”

Do not depend on voluntary writing. A production change cannot pass the existing ServiceNow/Azure deployment gate without a decision-record ID. The record is prefilled automatically from the change request, pull request metadata, approvers, test evidence, and deployment; the engineer adds only the choice, rejected alternative, and consequence. The service owner reviews exceptions weekly, and repeated missing records block release rather than create a reminder campaign. If the organization will not authorize that gate, remove the record requirement rather than pretend diligence will persist.

**Basis: framework.** Mechanism over commitment; accountable execution.

### 7. “Who maintains all this after you leave?”

Ownership is a deployment gate, not a handoff document at the end. Operations owns the workflow, queue, policy content, and outcome; the ServiceNow team owns configuration; identity/security owns access policy and reviews; a named engineering service owner owns the small Azure components and on-call path; credentialing stewards own rule examples. Before expansion, each owner must demonstrate a runbook exercise: revoke an agent, restore/replay an audit, update a policy, handle a failed job, and produce the weekly metric. Unowned components do not ship; custom code without a funded support path is removed.

**Basis: framework.** Durable ownership enforced by a release gate.

## Head of security

### 8. “Walk me through the blast radius if an agent identity is compromised.”

It depends on the identity, which is why there is no shared “AI service account.” The evidence assistant can read only pilot fields through an Oracle view and write draft evidence to specific ServiceNow fields; it cannot approve, email, modify Oracle, or access claims. The outreach identity can read minimal contact fields and send only from one mailbox with rate and recipient controls; it cannot read verification evidence. The packet identity can write only one restricted SharePoint library. Private endpoints, outbound allow-lists, disabled interactive login, managed identity, short-lived tokens, and per-environment separation limit movement. Detection includes anomalous sign-ins, volume, destinations, and denied calls. The kill sequence is disable the Entra service principal, revoke sessions/credentials, stop the Azure workload, preserve logs, identify correlated case IDs, review outputs, notify owners, and re-verify affected cases.

**Basis: framework plus improvised incident detail.** Exact containment must be threat-modeled with Meridian.

### 9. “Where does the data go?”

Provider data stays inside Meridian's approved tenant and Azure region. The approved enterprise model endpoint, storage, logs, search/index, and compute are region-pinned; Azure Policy denies other regions, Private Link and firewall rules block public paths, and only the curated SharePoint site is indexed. We document every data flow, subprocessor, retention period, backup location, and whether prompts/outputs can be used for training; security and legal approve those facts before real data is used. If an existing service cannot meet residency or retention requirements, it is excluded—there is no exception hidden in a pilot.

**Basis: framework; implementation specifics require validation.**

### 10. “How do I audit what an agent did six months from now?”

Start with a ServiceNow case or an agent event. The correlation ID retrieves the workload identity, input references and hashes, retrieved document IDs/versions, prompt/template and model deployment versions, output, tool/API calls, timestamps, costs, policy decision, human reviewer, override reason, and final enablement. Entra/Azure/Key Vault logs show access; SharePoint version history preserves the evidence packet; ServiceNow preserves decisions. Retention is at least the required audit period with restricted append-only storage. Before launch and monthly thereafter, security selects a past case and an independent person reconstructs it; failure to replay is an operational incident.

**Basis: framework.** Traceability chain and tested auditability.
