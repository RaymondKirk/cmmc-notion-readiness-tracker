# Synthetic walkthrough records

Every name, date, environment, finding, and evidence reference below is invented for this portfolio demonstration. These rows show the intended relationships; they do not represent an actual contractor, assessment, CMMC score, or certification.

## System

| System ID | System | Scope owner | Data category | Scope decision | Reviewed on |
| --- | --- | --- | --- | --- | --- |
| `SYS-001` | HarborWorks Engineering enclave | Jordan Lee | CUI | Under review | 2026-11-03 |

**Boundary note:** Fictional design and file-sharing environment. External services, users, and data flows still need confirmation. The draft scope is intentionally unresolved.

## Requirement Reviews

| Review ID | Topic | Owner | Reviewer | Internal status | Decision summary | Next review |
| --- | --- | --- | --- | --- | --- | --- |
| `SYS-001/3.1.1` | Authorized access | Alex Chen | Morgan Reed | Ready for review | Access list submitted; reviewer must compare it with actual account settings. | 2026-11-20 |
| `SYS-001/3.5.3` | Multifactor authentication | Alex Chen | Morgan Reed | Needs remediation | MFA is enabled for interactive users, but a service administration path was found without MFA. | 2026-11-18 |
| `SYS-001/3.12.2` | Plans of action | Jordan Lee | Morgan Reed | In progress | Internal gap process documented; applicability and formal treatment require separate review. | 2026-11-24 |
| `SYS-001/3.12.4` | System security plan | Jordan Lee | Morgan Reed | Not reviewed | Current plan location and revision have not yet been confirmed. | 2026-11-24 |

The requirement IDs refer to [NIST SP 800-171 Rev. 2](https://csrc.nist.gov/pubs/sp/800/171/r2/upd1/final). Topic names are navigation labels. The full requirement wording and assessment objectives belong in the authorized review process.

## Evidence Index

| Evidence ID | Linked review | Artifact type | Collected on | Review status | Approved location | Review note |
| --- | --- | --- | --- | --- | --- | --- |
| `EVD-001` | `SYS-001/3.5.3` | Configuration | 2026-11-02 | Rejected | Demo placeholder | Screenshot covered interactive users only; it did not address the service administration path. |
| `EVD-002` | `SYS-001/3.1.1` | Procedure | 2026-11-04 | Under review | Demo placeholder | Reviewer must compare approved access process with active accounts. |
| `EVD-003` | `SYS-001/3.5.3` | Test result | Planned | Requested | Demo placeholder | New MFA test after remediation; no artifact exists yet. |

`EVD-003` is a request, not evidence that a fix happened. In a real tracker, an evidence owner and reviewer would also be assigned, and the approved location would be a permission-controlled reference.

## Remediation

| Item ID | Linked review | Gap | Owner | Status | Target date | Verification owner | Verification evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `REM-001` | `SYS-001/3.5.3` | Service administration path lacks MFA. | Alex Chen | In progress | 2026-11-18 | Morgan Reed | `EVD-003` requested |

**Closure rule:** When the fix is implemented, collect the new test result, have Morgan verify it, record the date and method, then update the requirement review. Keep the rejected `EVD-001` linked to preserve the decision trail. Do not mark `REM-001` verified or closed solely because the target date arrives.

## Five-minute demo route

1. Open `SYS-001` and confirm its draft boundary and scope owner.
2. Open `SYS-001/3.5.3` and read the finding and named reviewer.
3. Open `EVD-001` to see why the original evidence was rejected.
4. Open `REM-001` to see the action, owner, target date, and verification owner.
5. Check `EVD-003`: its status is **Requested**, so the gap remains unresolved.
