BACKUP & RESTORE CONTRACT v1.0
Applies to: agent.klirtrak
Status: Mandatory, non-optional
Owner: Platform (not “ops later”)

1. Core Rule (Read This Twice)
If it cannot be restored on demand, it is not a backup.
Backups are only valid if:
* they are complete
* they are consistent
* they are restorable
* they are tested
Anything else is theater.

2. What MUST Be Backed Up (Authoritative)
We back up state, not containers.
A) Datastores (Critical)
These are Tier-0. If these are missing or corrupt, you are dead.
* Primary database
o Agent definitions
o Versions
o Account states
o Billing / usage ledger
* Directus database
o Knowledge base metadata
o Source references
o Processing state
?? Method: logical dumps + filesystem snapshot
?? Never: rely on “Docker volume copy only”

B) File Assets (Critical)
Also Tier-0.
* Knowledge uploads (PDFs, docs)
* Voice assets (if stored locally)
* Generated artifacts required for agent operation
?? Must be versioned with timestamps
?? Must be checksum-verified

C) Configuration & Orchestration (Tier-1)
* n8n workflows (exported JSON)
* Flowise chatflows
* Environment configuration (sanitized)
* Agent templates / defaults
?? These are required to rebuild, not to run immediately
?? Losing these causes long recovery, not instant outage

D) Dashboard UI Code (Tier-2)
* Repo / build artifacts
?? If lost, inconvenient — not catastrophic
?? Must still be recoverable, but lowest priority

3. Backup Schedule (Locked)
Automated Backups
FrequencyScopeNightly (off-peak)Full Tier-0 + Tier-1WeeklyFull snapshot + archiveMonthlyLong-term immutable archive?? Nightly time is fixed and boring
?? No “when convenient” backups

4. Backup Properties (Non-Negotiable)
Every backup must be:
* Immutable (cannot be overwritten)
* Timestamped
* Versioned
* Checksummed
* Logged
If any step fails ? backup is marked FAILED, not “probably fine”.

5. Restore Contract (This Is What You’ve Been Missing)
A backup is not considered valid until this is proven.
Restore Scenarios We Must Support
Scenario 1 — Full System Restore
“Everything is gone. Bring it back.”
Must restore:
* database
* files
* agent definitions
* knowledge base
* configs
Target: new host, clean environment

Scenario 2 — Partial Restore
“Agent config corrupted. Roll back.”
Must restore:
* previous agent version
* without touching runtime execution

Scenario 3 — Point-in-Time Recovery
“What did this look like 3 days ago?”
Must:
* select backup by date
* restore to isolated environment
* inspect before promotion

6. Restore Testing (This Is the Line That Was Missing Before)
Mandatory Restore Drills
FrequencyActionMonthlyFull restore to test environmentAfter major changeTargeted restore testAfter incidentRestore before proceeding?? No exceptions
?? If restore fails ? backups are considered broken until fixed

7. Environment Separation (Important)
We do not restore into production blindly.
Restore targets:
* restore-test (isolated)
* then promotion
This prevents:
* data loss
* accidental overwrites
* panic fixes

8. Backup Visibility (So You Don’t Have to Guess)
Dashboard must show:
* last successful backup time
* last failed backup
* last restore test
* backup health status
Red = attention
Green = boring (this is good)

9. What We Explicitly Do NOT Do
? No manual “I copied a folder” backups
? No untested snapshots
? No mixing prod + test restores
? No relying on Docker volumes alone
? No silent failures

10. Enforcement Rule
If backups are failing:
* no new features ship
* no dashboard changes deploy
* no portal changes proceed
Backups are a gate, not a chore.

Status
Backup & Restore Contract v1.0 — LOCKED

