# Exercise 3 — Client communication

## 3a. Two-page proposal to Diane

**Diane,**

### What we found

A provider credential takes 34 days on average and 41 days at the 90th percentile, against a 30-day commitment. The actual work is 770 minutes—less than 13 hours. On a calendar basis, only 1.6% of elapsed time is active work. The largest waits are references (11 days), the committee decision (7 days), and primary-source verification (5 days).

That changes the problem. Meridian does not chiefly need faster document writing or data extraction. It needs fewer queues, earlier work in parallel, a daily path for routine decisions, and a reliable record of what happened.

### Why earlier AI work did not change the numbers

The earlier efforts were reasonable experiments, but they were not attached to an operating constraint and an accountable outcome. The policy chatbot required employees to leave their work and visit it. Copilot may make coding faster, but coding is not necessarily what limits a two-week release cycle; integration, testing, approvals, and technical debt may be. The classifier had good test accuracy, but there was no safe and auditable path for the cases it got wrong. Three retrieval teams separately rebuilt the same context.

These are not failures of effort or sponsorship. They show that the unit of change must be the workflow, not the tool.

### What we propose

For 90 days, focus on one representative insurer segment and one result: increasing the share of credentials completed within 30 days from the reported 60% baseline to 80%, without increasing credentialing defects.

In the first two weeks we will put a reference-outreach queue into normal use for the pilot cohort. It will show every attempt, response, owner, next action, and blocker in ServiceNow. Staff will initially send the messages; automation will prepare drafts and record events. We will also reproduce the baseline from source data so anyone can rerun it.

Next we will start independent checks in parallel, build the committee packet as evidence arrives, and propose a daily delegated review path for complete routine cases. Exceptions will retain human review and move to a more frequent exception session. Agents may collect evidence and draft material; they will not attest primary-source verification or approve a credential.

This scope does not replace the mainframe, clean all 400,000 SharePoint files, buy a new platform, or roll out enterprise search. We will curate only the approved credentialing material needed by the pilot.

### What it will take

Most of the work is unglamorous: agreeing definitions; cleaning identifiers; finding the current policy among duplicates; documenting exceptions; configuring permissions; testing false matches; monitoring response rates; training staff; and changing committee cadence. The eleven verifiers are not a dependency to work around. Their knowledge is the core input, and they need protected design time and a meaningful stewardship role.

The difficult decision is organizational. A 15-minute committee decision currently waits seven days. No software can remove that wait unless routine authority is delegated or the committee changes how often it reviews cases. We will bring evidence and safe options; Meridian leadership and the committee chair must make the decision.

Security will approve the design before provider data enters any agent path. Each agent will have its own non-human identity, access only to the pilot records and approved SharePoint library, no interactive login, and a complete audit trail. Data will remain in Meridian's approved Azure region and tenant. Every agent action will link back to the case, source, version, and human decision.

### How we will know

In week one we will calculate the previous six months from ServiceNow, Oracle, and enablement timestamps and reconcile a 30-case sample. Each week the same published query will report the percentage completed within 30 days, plus median and 90th-percentile time.

The quality guardrail is verified credentialing defects per 100 completed cases within 30 days of enablement, including compliance rework and insurer returns. The pilot succeeds only if the final four weeks reach at least 80% on time, improve by at least ten percentage points over the validated baseline, and do not worsen quality. If those conditions are not met, we will say it failed or needs redesign—not relabel activity as impact.

### What we need from you

By day 3, name an operations owner with decision authority, a credentialing lead, two domain stewards, an operations analyst, and counterparts from security, compliance, ServiceNow, and engineering. Protect four hours per week for each steward for the first month.

By day 5, authorize read access to the agreed six-month dataset and the pilot's current policies, and approve one insurer segment for the pilot. By day 10, agree the metric definition and escalation path. By day 20, convene the committee chair to decide whether routine cases can receive delegated daily review and how exceptions will be heard. We will return weekly with the number, risks, decisions needed, and cost per completed case.

## 3b. Conversation with the VP of Engineering

**Exchange 1**

**Me:** “You are right that technical debt may be holding release cadence at two weeks. Copilot can shorten coding and still add no throughput if integration, tests, or deployment are the constraint. I am not proposing another engineering-wide assistant. I want one 90-day operations pilot using systems you already run, and week one includes mapping exactly which engineering work it creates.”

**VP:** “Every vendor says it is a small pilot. Then my team inherits an integration and a pile of support tickets.”

**Me:** “Assume that happens unless we prevent it structurally. Before build, you name one engineer to review the boundary, not to become the delivery team. We will use ServiceNow, Entra, Azure, and existing APIs; publish support load and runbooks; cap the pilot cohort; and stop expansion unless a named operations owner can run it within an agreed support budget.”

**Exchange 2**

**VP:** “The real problem is brittle identity, bad interfaces, and deployment plumbing. Your workflow will hit all three.”

**Me:** “Then the proposal should fund only the narrow debt that blocks this measurable outcome: a read-only provider view, workload identity, audit correlation, and a supported ServiceNow boundary. Those are reusable controls, not one-off prompt code. If your assessment shows the foundation cannot safely support even that in 90 days, I will tell Diane to spend this phase on the enabling debt and not pretend an agent pilot is ready.”

**Exchange 3**

**VP:** “And what do I get besides another system?”

**Me:** “A smaller unofficial spreadsheet footprint, fewer ad hoc data requests, reusable non-human identity and audit patterns, and evidence about where the process actually waits. We will measure engineering hours and incidents as costs alongside cycle time. If operations gains come by quietly transferring toil to engineering, the pilot fails.”

## 3c. Bad-news memo (157 words)

**Subject: Reference outreach is underperforming; action today**

Diane,

The automated reference messages are receiving 20% fewer responses than the prior manual process. Our current evidence suggests recipients are treating the messages as impersonal or automated, but we do not yet have a confirmed cause or fix.

If this continues, the 11-day reference wait will not fall and our 80%-within-30-days target is at risk. We have paused expansion; no additional cohorts will enter automation. Existing cases are moving to named, human-sent follow-ups so providers are not stranded.

This week we are testing small, controlled changes: a named employee sender, more personal wording, provider-confirmed contact details, and the prior manual channel. We will compare delivery, open, response, and completion rates by cohort while preserving the quality guardrail.

I need approval to use two verifiers for two hours each to call a sample of nonresponders, and your support keeping the pilot paused until a variant matches the manual response rate.

I will update you Friday at 3 p.m. with results, impact on the 90-day forecast, and a continue, redesign, or stop recommendation.

## 3d. The next gain

“The next meaningful gain is upstream completeness, not more automation. A 1.5-day wait occurs before completeness review, and incomplete cases then create rework throughout verification. If we can raise complete-at-receipt first-pass yield and reduce that queue to half a day for the current volume, we remove about one calendar day per case before the expensive work begins; I would validate the opportunity by publishing first-pass yield and missing-item reasons for four weeks before setting a savings target.”
