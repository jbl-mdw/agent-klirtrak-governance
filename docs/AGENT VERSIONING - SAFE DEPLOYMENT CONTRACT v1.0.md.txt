AGENT VERSIONING & SAFE DEPLOYMENT CONTRACT v1.0
Applies to: agent.klirtrak
Status: Locked
Purpose: Prevent a single edit from breaking live agents, calls, or billing

1. Core Rule (Non-Negotiable)
No agent change goes live without versioning, testing, and an explicit promotion step.
There is no such thing as “editing a live agent.”

2. Agent States (Authoritative)
Every agent exists in one and only one of these states:
* DRAFT
Editable. Not executable. Safe sandbox.
* TEST
Executable only via test numbers / test widgets.
No real customers.
* ACTIVE
Live production agent. Handles real chats/calls.
* PAUSED
Temporarily stopped. Configuration preserved.
* ARCHIVED
Read-only historical version.

3. Version Model (This Replaces WP-Style Staging)
Agents are immutable once activated.
Version examples
* Agent v1 ? ACTIVE
* Agent v2 ? DRAFT
* Agent v2 ? TEST
* Agent v2 ? ACTIVE (promotion)
* Agent v1 ? ARCHIVED
Edits always create a new version.

4. What Triggers a New Version (Always)
Any change to the following forces a new version:
* Prompt / directives
* Knowledge base attachment
* Voice provider or voice ID
* Business hours / after-hours rules
* Routing / escalation logic
* Outbound campaign rules
* Tools / actions the agent can execute
No exceptions.

5. Test Mode (Mandatory Safety Layer)
Test mode guarantees:
* Calls go only to test numbers
* Chats go only to test widgets
* Usage is tagged as TEST (not billable)
* No CRM writes unless explicitly allowed
Required before promotion:
* At least one successful test call/chat
* No execution errors
* No failed workflow hooks

6. Promotion Rules (How Things Go Live)
Promotion is explicit, not automatic.
To promote TEST ? ACTIVE:
* Checklist completed (system-enforced)
* Account state allows execution (billing gate)
* Previous ACTIVE version archived
* Timestamp + actor logged
Rollback is one click:
* ACTIVE ? ARCHIVED
* Previous version ? ACTIVE

7. Rollback Contract (This Is Critical)
Rollback must:
* Take < 60 seconds
* Not require redeploys
* Not require DB restores
* Not interrupt other agents
If rollback requires ops intervention, the system is broken.

8. Dashboard Enforcement (UI Must Obey This)
The dashboard must not allow:
* Editing ACTIVE agents
* Skipping TEST
* Silent promotions
* Overwriting previous versions
Visual cues:
* Version badges (v1, v2…)
* State labels (DRAFT / TEST / ACTIVE)
* Promotion history

9. Audit & Logging (Trust Layer)
Every version event is logged:
* Created
* Tested
* Promoted
* Rolled back
* Archived
Logs include:
* Who
* When
* Why (required for rollback)

10. Why This Exists (Plain English)
This replaces:
* WP staging
* “Quick fixes”
* Panic edits
* Site crashes
With:
* Safe iteration
* Zero missed calls
* Instant rollback
* Confidence

Status
Agent Versioning & Safe Deployment Contract v1.0 — LOCKED

