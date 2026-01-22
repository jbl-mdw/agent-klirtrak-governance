DASHBOARD CONSTITUTION v1.0
Applies to: agent.klirtrak
Status: Locked
Purpose: Prevent UI drift, overbuilding, developer “helpfulness,” and system crashes

1. Core Principle (Read This First)
The dashboard is a control plane, not a product showcase, not analytics porn, and not a dev console.
If a screen, feature, or widget does not help an operator control agents safely, it does not belong.

2. What the Dashboard Exists To Do (Only These)
The dashboard exists to help a user answer five questions:
1. What agents exist?
2. What are they responsible for?
3. Are they working right now?
4. What did they do?
5. What should I adjust?
Every screen must clearly answer at least one of these.

3. Non-Negotiables (These Prevent Failure)
The dashboard must NEVER:
* Edit a live (ACTIVE) agent
* Expose raw system prompts without guardrails
* Expose Directus, n8n, Flowise, or infrastructure UIs
* Mirror backend complexity
* Allow clients to bypass billing or execution gates
* Require the dashboard to be “up” for agents to run
If a feature violates any of the above, it is rejected.

4. Navigation Rules (This Prevents Cognitive Overload)
Sidebar (Locked Set)
The sidebar is intentionally small.
Allowed:
* Home (health snapshot only)
* Agents
* Conversations
* Knowledge Base
* Usage & Billing
* Team
* Settings
Admin-only (not client-facing):
* Tenants / Clients
* System Health / Backups
* Audit Logs
? No product-per-sidebar-item
? No nested mega-menus
? No “just one more” item

5. Agents Are the Primary Object (Not Features)
Everything in the dashboard revolves around Agents.
Rules:
* Users start on Agents
* Creation flows start with Agent identity
* Configuration lives inside the agent
* Logs and usage are agent-scoped
If a feature cannot be clearly tied to an agent, it does not belong.

6. Configuration Is Structured, Not Free-Form
The dashboard must favor:
* Checkboxes
* Toggles
* Selectors
* Guided text inputs
Over:
* Free-text prompt boxes
* Raw JSON
* “Advanced” dump tabs
Free-form inputs are allowed only behind explicit advanced toggles with guardrails.

7. Versioning Is Visible and Enforced
The UI must clearly show:
* Agent versions (v1, v2, v3…)
* State (DRAFT / TEST / ACTIVE / PAUSED)
* Promotion history
* Rollback availability
The UI must not:
* Hide version transitions
* Allow silent overwrites
* Allow editing ACTIVE agents

8. Dashboard Changes Must Be Safe by Design
Staging Rules
* UI-only staging is allowed
* Runtime execution is never staged
* Destructive actions are feature-flagged
Failure Mode
If the dashboard fails:
* Agents continue to run
* Calls are answered
* Chats continue
* Billing enforcement remains active
The dashboard is never a single point of failure.

9. Analytics Discipline (Why This Matters)
In v1:
* Analytics are secondary
* Summaries > charts
* Outcomes > metrics
* Confidence > optimization
Allowed:
* “Calls handled today”
* “Chats resolved”
* “Missed / escalated”
Not allowed in v1:
* Conversion funnels
* Heatmaps
* Deep performance dashboards
* Anything that distracts from control

10. Developer Rule (This Prevents Crashes)
If a feature cannot be explained in one sentence to a non-technical operator, it does not ship.
“No one will use it” is a valid reason to delete code.

Status
Dashboard Constitution v1.0 — LOCKED

