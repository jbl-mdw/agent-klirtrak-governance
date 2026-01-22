CLIENT PORTAL PERMISSION MATRIX v1.0
Applies to: agent.klirtrak
Status: Locked
Purpose: Prevent clients (and devs) from crashing the system again

1. Core Rule (Non-Negotiable)
Clients never receive system power. They receive controlled capability.
If a client action can:
* break agent runtime
* interrupt calls
* corrupt data
* bypass billing
* affect other tenants
…it is forbidden in the client portal.

2. Portal Scope (What the Client Portal Is)
The Client Portal is a management surface, not an admin console.
It allows clients to:
* configure agents safely
* view conversations and outcomes
* manage knowledge
* see usage and billing
* manage their internal team
It does not allow:
* infrastructure access
* workflow editing
* system overrides
* raw configuration access

3. Role Model (Authoritative)
There are exactly three client roles.
OWNER
Primary account holder.
Can:
* Manage subscription, trials, billing, payment method
* Create / edit agents (within guardrails)
* Manage knowledge base
* View all conversations and logs
* Manage team members and roles
Cannot:
* Access system internals
* Edit workflows
* Bypass billing gates
* Disable execution guards

MANAGER
Operational role.
Can:
* Create / edit agents
* Configure voice, hours, routing
* Manage knowledge base
* View conversations and outcomes
Cannot:
* Change billing or plans
* Add/remove payment methods
* Unlock locked accounts
* Access admin/system views

VIEWER
Read-only role.
Can:
* View agents
* View conversations and summaries
* View usage metrics (read-only)
Cannot:
* Edit anything
* Create agents
* Manage billing
* Upload knowledge
* Trigger outbound actions

4. Permission Matrix (Explicit)
CapabilityOwnerManagerViewerCreate Agent???Edit Agent (DRAFT/TEST)???Edit ACTIVE Agent???Promote TEST ? ACTIVE???Pause / Resume Agent???Upload Knowledge???Delete Knowledge???View Conversations???View Usage???Manage Billing???Invite Users???Change Roles???
5. Guardrails (Hard Safety Limits)
The client portal must enforce:
* No editing ACTIVE agents
* No raw prompt editing without guardrails
* No direct API key visibility
* No workflow access (n8n / Flowise)
* No environment variables
* No database-level operations
If a feature requires admin-level trust, it does not belong in the client portal.

6. Billing & Lockout Enforcement (Portal Behavior)
When account state is:
* TRIAL ? show caps, countdown, upgrade CTA
* PAST_DUE ? show warnings, grace countdown
* LOCKED ? portal becomes read-only
Locked behavior:
* Agents show “Paused – Subscription Required”
* Edit buttons disabled
* Clear explanation + upgrade path
No silent failures. No confusion.

7. Version Safety in Portal
Clients:
* Can create new agent versions (DRAFT)
* Can test versions (TEST)
* Cannot overwrite ACTIVE versions
* Cannot delete historical versions
Rollback is allowed only to previously ACTIVE versions.

8. Portal Isolation Rule (Why the Last Crash Happened)
The portal must:
* Use a client-safe API layer
* Never talk directly to internal services
* Never expose admin endpoints
* Fail gracefully without affecting runtime
Even if the portal is broken, agents must continue running.

9. Audit & Accountability
Every client action is logged:
* Who
* What
* When
* Agent version affected
Critical actions (promotion, pause, billing change) require confirmation.

Status
Client Portal Permission Matrix v1.0 — LOCKED

