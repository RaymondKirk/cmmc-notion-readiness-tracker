# CMMC readiness tracker in Notion

**Portfolio blueprint | Fictional contractor and records | Prepared November 10, 2026**

I designed this Notion workspace blueprint to help a small defense contractor coordinate CMMC Level 2 readiness work. It connects an in-scope system, NIST SP 800-171 Rev. 2 requirement reviews, evidence metadata, and remediation tasks. The [data model and build guide](data-model.md) are detailed enough to create a demo workspace; the [sample records](sample-records.md) show a realistic review. This repository is a design and synthetic case study, not a deployed client system, assessment, certification, or complete 110-requirement catalog.

## The problem

Requirement spreadsheets can show a status without showing who reviewed it, what evidence supports it, or whether an open gap has a remediation owner. A project team needs to answer four questions quickly: Which system is in scope? Who owns each requirement review? Where is the approved evidence? What remains unresolved before an authorized assessment?

## My design

| Workspace component | Purpose | Decision it supports |
| --- | --- | --- |
| Systems | Define the system boundary, owner, and assessment context | Which environment does this review cover? |
| Requirement Reviews | One row per system and Rev. 2 requirement | What is the internal review state and who decided it? |
| Evidence Index | Track approved storage references and review metadata | Is current evidence available for this requirement? |
| Remediation | Record a gap, owner, dates, and verification | What work remains, and has the fix been checked? |

The design intentionally separates **internal readiness status** from any official CMMC assessment result. A green internal review is a team judgment, not a certification or a claim that a requirement is met for contract purposes. A remediation row is a planning record; an authorized assessor and the applicable rules determine whether a formal plan of action and milestones is permitted.

## Example walkthrough

The fictional *HarborWorks Engineering* system has a review of requirement **3.5.3 (multifactor authentication)**. The reviewer finds that a service administration path lacks MFA, links a metadata-only evidence record, and opens a remediation item. After the team applies a fix, a different reviewer checks new evidence and records the decision. The original gap, dates, and reviewer remain visible. See [sample records](sample-records.md).

## What a consulting client would receive

1. A scope workshop and a system inventory, with boundary questions sent to the client's security and contracting owners.
2. A Notion tracker built from the [schema](data-model.md), with named owners, views, and record templates.
3. A controlled evidence index pointing to the client's approved repository, without copying sensitive artifacts into a general workspace.
4. A short operating guide: who updates records, who reviews them, when evidence expires, and how gaps are escalated.
5. A handoff exercise in which a new user locates a requirement, its owner, evidence reference, and open remediation in under two minutes. This is a proposed acceptance check, not a measured result.

## Security and publication boundaries

- The public example contains no real client data, FCI, CUI, system security plans, assessment results, or evidence files.
- In a real engagement, the client approves where CUI and evidence may be stored. This blueprint keeps only references and non-sensitive metadata in Notion. A link or filtered Notion view is not an access control; permissions must be enforced at the workspace and evidence store.
- Do not publish contract identifiers, internal architecture, employee names, real system boundaries, restricted URLs, or actual gaps in a public GitHub repository.
- Before use, confirm the solicitation/contract's required level, assessment type, clauses, current program phase, and data handling rules with the client's contracting and security leads.

## Regulatory snapshot and sources

As of **November 10, 2026**, the Department of War has [announced suspension of CMMC Phase II requirements](https://business.defense.gov/Engage/News/Article/4542563/forging-the-arsenal-of-freedom-department-of-war-suspends-cmmc-phase-ii-require/) that had been scheduled for this date; Phase I self-assessment remains. Existing safeguarding duties under applicable contracts still matter. This is a dated portfolio snapshot, so a project owner must recheck current direction and the actual solicitation before using the tracker for a bid or assessment.

This design uses the **110 requirements of NIST SP 800-171 Rev. 2** as the Level 2 reference set described in [DoD small-business CMMC guidance](https://business.defense.gov/Cyber/). [NIST's Rev. 2 publication](https://csrc.nist.gov/pubs/sp/800/171/r2/upd1/final) is superseded in the general NIST catalog, while the CMMC program's Rev. 2 basis has been [explained by NIST](https://www.nist.gov/system/files/documents/2026/02/12/800-171r3-SMB-Primer-Webinar-Q%26A-Final.pdf). For a real engagement, verify the current program rule, [DFARS clause](https://www.acquisition.gov/dfars/252.204-7021-contractor-compliance-cybersecurity-maturity-model-certification-level-requirements.), and contract language.

## Current state

The repository contains a buildable design and four connected fictional record types. It does **not** include a live Notion workspace, a validated control assessment, a score, or a client outcome. A useful next iteration would be a separate synthetic Notion demo with screenshots and a recorded handoff test.
