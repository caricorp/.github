# Projects v2 Operating Model

This organization has many applications and a relatively small development team. The standard way to keep that manageable is to track work in a small number of organization-level Projects v2 boards, then use fields, views, and workflows to slice by repository, product, and urgency.

## Recommended standard

Use organization-level Projects v2 instead of separate boards per repository for shared portfolio visibility.

Maintain three primary projects:

1. Bug Portfolio: every bug across the organization
2. Feature Portfolio: all planned feature work within roadmap scope
3. Sales Exceptions: out-of-scope features requested by sales

This is closer to industry standard than creating one board per app when the team is small. The board count stays low, while custom fields and filtered views give you per-app visibility.

## Why this model works

- Bugs and features move differently and need different triage rules.
- Sales-driven exceptions should not disappear inside the normal feature backlog.
- Organization-level projects let leadership, engineering, support, and product see the same source of truth.
- Projects v2 fields make it easy to filter by app, team, priority, status, or revenue impact without duplicating issues.

## Required custom fields

Create these fields in each project where relevant:

- App: single select or text; the product, repository, or service name
- Team: single select; owning team
- Issue Type: single select; Bug, Feature, Sales Exception
- Priority: single select; P0, P1, P2, P3
- Severity: single select; Critical, High, Medium, Low
- Status: single select; Inbox, Triaged, Ready, In Progress, Blocked, In Review, Done
- Target Quarter: single select; for planning windows
- Customer Impact: single select; Single Account, Multi-Account, Internal, Platform-Wide
- Approval Status: single select; Needs Review, Approved, Rejected
- Revenue Target: number or text; ARR, MRR, or deal value tied to the request
- Deadline: date; contractual or business deadline
- Repo Link: text or repository reference if you use mirrored metadata manually

## Recommended automations and norms

- If only internal users with project write access create issues, you can use the issue form `projects:` field to add items directly to a Projects v2 board at creation time.
- If issue creators may not have write access to the project, use the project's built-in auto-add workflow instead. This is the more reliable organization-wide default.
- Add all new bug issues to Bug Portfolio.
- Add all standard feature issues to Feature Portfolio.
- Add all sales-sponsored requests to Sales Exceptions.
- Mirror approved sales requests into Feature Portfolio only when they become committed delivery work.
- Keep one canonical issue per request. Avoid copying issue content across boards unless you need linked execution work in a repo.
- Require every issue to have App, Team, Status, and Priority set during triage.

## Priority policy

Use this prioritization rule across the organization:

1. Production bugs and customer-impacting regressions come first.
2. Approved sales exceptions outrank normal roadmap features.
3. Normal roadmap features are prioritized after operational stability and approved revenue work.

For the Sales Exceptions board, set Priority to P0 or top-of-queue whenever Approval Status is Approved and Revenue Target is present.

If you need a simple decision rule for conflicts, use this ordering:

- Critical production bug
- Approved sales exception with committed revenue target
- High-severity bug
- Committed roadmap feature
- Nice-to-have feature

## Recommended saved views

In Bug Portfolio:

- All Open Bugs
- Critical and High Bugs
- Bugs by App
- Bugs by Team
- Regressions This Quarter

In Feature Portfolio:

- Roadmap Queue
- Ready for Build
- Features by App
- Features by Quarter

In Sales Exceptions:

- Needs Approval
- Approved and Unscheduled
- Approved by Revenue Target
- Due in 30 Days

## Issue template alignment

The organization issue forms in `.github/ISSUE_TEMPLATE` are designed to support this operating model.

- Bug reports collect reproduction details, suspected area, and validation steps so an LLM can move quickly from issue to fix.
- Feature requests collect problem statement, scope, and acceptance criteria.
- Sales-sponsored features require approval status and revenue target so prioritization is explicit.

## Practical setup steps

1. Create the three organization-level Projects v2 boards.
2. Add the custom fields above.
3. Configure default saved views for engineering leadership and triage.
4. Map each issue template to the right labels.
5. During triage, fill in App, Team, Priority, and Status immediately.
6. Treat approved sales exceptions as explicit priority overrides, not informal requests.