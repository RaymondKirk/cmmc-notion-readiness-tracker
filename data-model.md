# Data model and Notion build guide

Create a separate demo page titled **CMMC Readiness Demo**. Use only synthetic data. The four databases below use one row per coherent entity, stable IDs, and relations so a reviewer can move from a system to a requirement, evidence, and a gap.

## 1. Systems

| Property | Notion type | Rule |
| --- | --- | --- |
| System | Title | Short, recognizable boundary name |
| System ID | Text | Unique, stable ID such as `SYS-001` |
| Scope owner | Person | Accountable for the proposed boundary |
| Boundary summary | Text | High-level, public-safe description in demo |
| Data category | Select | `FCI`, `CUI`, `Both`, `To confirm` |
| Contract requirement | Text | Record the actual clause/solicitation reference in a private implementation; use `Demo only` publicly |
| Scope decision | Select | `Draft`, `Under review`, `Approved`, `Changed` |
| Reviewed on | Date | Date the scope owner last confirmed the row |
| Requirement Reviews | Relation | Link to Requirement Reviews; show reciprocal relation |

**Template:** Boundary assumptions, connected services, exclusions, decision owner, approval date, next review trigger. Do not paste a real system security plan into a public or broadly shared page.

## 2. Requirement Reviews

One row represents **one system + one NIST SP 800-171 Rev. 2 requirement**. The complete Level 2 implementation would need the full applicable requirement set; the demo contains only four examples. Use an ID such as `SYS-001/3.5.3` to prevent duplicate reviews.

| Property | Notion type | Rule |
| --- | --- | --- |
| Review | Title | `SYS-001 / 3.5.3 / MFA` |
| Review ID | Text | Unique system/requirement pair |
| System | Relation | Exactly one Systems record |
| Requirement ID | Text | Rev. 2 identifier, e.g. `3.5.3` |
| Topic | Text | Short navigation label, not a substitute for official text |
| Family | Select | NIST requirement family |
| Owner | Person | Person gathering implementation details |
| Reviewer | Person | Person making the internal review decision |
| Internal status | Select | `Not reviewed`, `In progress`, `Needs remediation`, `Ready for review`, `Reviewed` |
| Decision summary | Text | Finding and reason; avoid an unexplained green status |
| Reviewed on | Date | Last substantive review |
| Next review | Date | Recheck after change or evidence expiry |
| Evidence | Relation | Link to Evidence Index; reciprocal relation |
| Remediation | Relation | Link to Remediation; reciprocal relation |

**Template:** Requirement source link, system-specific implementation description, questions for owner, evidence expected, decision and reviewer, exceptions, next review trigger. For real use, link to the authoritative requirement wording and assessment objectives rather than relying on the short topic field.

## 3. Evidence Index

Store **metadata and references**, not copies of restricted artifacts in this demo.

| Property | Notion type | Rule |
| --- | --- | --- |
| Evidence | Title | Descriptive, non-sensitive name |
| Evidence ID | Text | Stable ID such as `EVD-001` |
| Requirement Reviews | Relation | One or more reviews supported |
| Evidence owner | Person | Maintains source artifact |
| Artifact type | Select | `Configuration`, `Procedure`, `Test result`, `Interview`, `Other` |
| Approved location | URL or Text | Restricted evidence store reference; `Demo placeholder` publicly |
| Collected on | Date | When artifact was captured |
| Valid through | Date | Internal freshness target, not a regulatory expiry claim |
| Review status | Select | `Requested`, `Collected`, `Under review`, `Accepted internally`, `Rejected`, `Stale` |
| Reviewed by | Person | Separate from evidence owner when feasible |
| Review note | Text | Why it supports the linked review; any limitation |

**Template:** Collection method, time period, system covered, reviewer notes, source permissions, and replacement trigger. A URL field by itself does not prove that an artifact is sufficient or accessible to an authorized reviewer.

## 4. Remediation

| Property | Notion type | Rule |
| --- | --- | --- |
| Remediation | Title | Concrete gap and action |
| Item ID | Text | Stable ID such as `REM-001` |
| Requirement Review | Relation | Link to the affected review |
| Gap summary | Text | Describe observed condition and scope |
| Owner | Person | Responsible for fix |
| Priority | Select | `Critical`, `High`, `Medium`, `Low` as internal triage only |
| Status | Select | `Open`, `In progress`, `Ready for verification`, `Verified`, `Closed` |
| Target date | Date | Agreed internal date |
| Verification owner | Person | Reviews the fix |
| Verified on | Date | Set only after review |
| Verification evidence | Relation | Link to Evidence Index |
| Closure decision | Text | What was tested and what remains |

**Template:** Root cause, interim handling, implementation steps, milestones, dependency, verification method, closure decision. A formal CMMC POA&M and its eligibility rules require separate review; do not treat every Remediation row as an allowable POA&M item.

## Views and daily decisions

| View | Database and filter | Use |
| --- | --- | --- |
| Boundary review | Systems: `Scope decision` is not `Approved` | Resolve scope before claiming coverage |
| My requirement work | Requirement Reviews: `Owner` is me; `Internal status` is not `Reviewed` | See assigned work |
| Reviewer queue | Requirement Reviews: `Internal status` is `Ready for review` | Make and record review decisions |
| Missing or stale evidence | Evidence Index: `Review status` is `Requested`, `Rejected`, or `Stale`; plus a separate date view for `Valid through` before today | Request replacement artifacts |
| Open gaps | Remediation: `Status` is not `Closed`, grouped by owner and sorted by target date | Escalate and verify fixes |
| System dashboard | Linked views filtered to one system | Walk from boundary to status, evidence, and gaps |

Notion filters help navigation but do not hide records from users who have broader database access. Give access through real workspace permissions and the approved evidence store. Do not infer readiness from a count of `Reviewed` rows; every applicable requirement, evidence quality, scope, and assessment rule still needs review.

## Build and handoff sequence

1. Create the four full-page databases and properties above. Add reciprocal relations.
2. Create a system record. Enter requirement reviews with a unique `System ID / Requirement ID` pair.
3. Add the synthetic records in [sample records](sample-records.md). Test every relation in both directions.
4. Make the six views. Confirm owner, reviewer, status, dates, and evidence reference are visible in the views where decisions happen.
5. Use a second account with intended viewer permissions to test what it can actually read and edit. Confirm restricted evidence links enforce their own permissions.
6. Ask a new user to find the MFA gap, its owner, the earlier evidence, and the verification step. Record the observed time and confusion before claiming usability results.
7. For a real client, review contract requirements, approved data locations, retention, role assignments, and the full requirement set before importing any live records.

Notion CSV imports do not automatically create all relations and views. Verify the linked records and permissions manually after any import.
