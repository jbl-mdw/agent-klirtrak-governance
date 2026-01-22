PROJECT: agent.klirtrak
TYPE: AI Agent Control Plane (not a website, not a CMS)
CORE PRODUCTS: LGR Chat ? LGR Connect ? LGR Receptionist ? LGR Prospector
NON-NEGOTIABLES:
- Single agent brain
- Execution layers only
- No client access to system internals
- Backup + restore is mandatory, boring, and testable

PROJECT ANCHOR v1.0
Project: agent.klirtrak
Document Type: Living Constitution (append-only, governed)

1. WHAT THIS PROJECT IS
agent.klirtrak is a control-plane dashboard for managing AI agents built on a single shared agent brain, with multiple execution modes.
It is an operator command center for configuring, deploying, monitoring, and governing AI agents that handle real conversations (chat, voice, outbound) for real businesses.
It is not a website.
It is not a CMS.
It is not a collection of bots.

2. CORE PRODUCT HIERARCHY (LOCKED)
There is one brain and multiple execution layers.
Canonical Products (Authoritative)
1. LGR Chat
The agent brain.
Knowledge ingestion, directives, identity, reasoning.
2. LGR Connect
Enhanced inbound conversation layer (conversion-focused chat).
Same brain, different engagement surface.
3. LGR Receptionist
Inbound voice execution of the same agent brain.
Rule-driven (time, intent, routing).
4. LGR Prospector
Outbound execution (campaign-based, compliance-aware).
Same brain, reversed direction of travel.
Rule:
Nothing exists outside LGR Chat.
No product invents its own intelligence.

3. WHAT THIS PROJECT IS NOT (NON-NEGOTIABLE)
agent.klirtrak is not:
* A marketing site
* A WordPress site
* A CMS
* A generic SaaS admin panel
* An analytics-heavy dashboard
* A developer console
* A place to expose Directus, n8n, or Flowise UIs to clients
* A UI that mirrors backend complexity
Any proposal resembling the above is invalid by definition.

4. DASHBOARD PURPOSE (VERY SPECIFIC)
The dashboard exists to answer five operator questions, fast:
1. What agents exist?
2. What are they responsible for?
3. Are they working right now?
4. What did they do?
5. What should I adjust?
If a screen does not help answer one of these, it does not belong in v1.

5. DASHBOARD ROLE (MENTAL MODEL)
The dashboard is a control plane, not the star.
* It orchestrates agents
* It does not execute intelligence
* It does not expose internals
* It does not allow clients to break runtime behavior
Even if the dashboard is down:
* Agents must continue answering calls and chats

6. CLIENT PORTAL PRINCIPLE (LOCKED)
Clients will have a portal.
The client portal:
* Is a separate surface
* Has strict role boundaries
* Talks only to a client-safe API layer
* Cannot access raw system configuration
* Cannot crash the agent runtime
Clients get capabilities, not control.

7. SUBSCRIPTION, TRIAL, AND LOCKOUT (FIRST-CLASS)
Agents do not run unless the account state allows it.
Account states are authoritative:
* TRIAL_7
* TRIAL_30
* ACTIVE_PAID
* PAST_DUE
* LOCKED_TRIAL_EXPIRED
* LOCKED_NONPAYING
Execution is gated at:
* Chat start
* Voice call ingress
* Outbound scheduler
* Workflow triggers
No soft enforcement.
No silent overages.
No “free forever.”

8. BACKUP & RESTORE (NON-OPTIONAL)
If it cannot be restored, it is not backed up.
Backups are:
* Scheduled
* Versioned
* Immutable
* Tested via restore drills
The system must never again depend on:
* “I think we backed it up”
* Partial exports
* Manual hope-based recovery
Backup integrity is part of system health, not ops trivia.

9. GOVERNANCE RULES (HOW THIS DOCUMENT LIVES)
* This document is append-only
* Core identity sections do not change casually
* Learnings are added as Anchored Rules
* Any rebuild, refactor, or new conversation must start with:
o the full anchor or
o the anchor header (summary)
If something conflicts with this anchor, the anchor wins.

10. ONE-SENTENCE SUMMARY (FOR CONTEXT RESET)
agent.klirtrak is a control-plane dashboard for operating AI agents built on a single shared brain (LGR Chat), with chat, voice, and outbound execution layers, strict governance, enforced billing, and crash-proof client access.

Status
Project Anchor v1.0 — LOCKED





ANCHOR UPDATE (APPEND ONLY):
- Added Client Portal as separate surface
- Added 7-day and 30-day trial enforcement










Why this works (and why you felt the failure so strongly)
What happened earlier wasn’t “memory loss.”
It was lack of a written authority hierarchy.
Without an anchor:
* Conversations become improvisation
* Defaults creep in (WordPress, generic SaaS patterns)
* Each restart becomes reinterpretation
With an anchor:
* If a suggestion violates it ? it’s wrong by definition
* If context is lost ? you paste it back in
* If a dev “fixes” something and crashes the site ? they violated the anchor

How we’ll use it going forward (my commitment)
If you approve:
* I will treat the Project Anchor as law
* I will not infer beyond it
* I will call out my own suggestions if they violate it
* Every blueprint, dashboard plan, or portal plan will explicitly reference it

Next step (only when you say so)

