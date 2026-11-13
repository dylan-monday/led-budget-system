# LED Budget System

A custom budget management system for Louisiana Economic Development, built by
Monday + Partners. Replaces a Monday.com board and a set of spreadsheets that
were never designed to track public money.

Primary user: Kelly Raney, Executive Director, Innovation Operations, LED.
Not technical. Should never need to be.

Project instructions, call transcripts and the approved proposal live in the
"LED Budget System" Cowork project. Read the money model doc before touching
anything that stores or calculates a number.

## The standard

Exceptional. Surprisingly easy to use and rewarding to work with. Small moments
of delight that earn their place and never decorate. Flag anything that falls
short before delivering it.

Generic admin-panel UI is a failure, not a starting point.

## Non-negotiable

+ This is public money across federal and state programs. The ledger is correct
  before anything else is considered.
+ Money is stored as integer cents. Never floats.
+ Financial records are append-only with a complete audit trail. Corrections are
  new entries, never silent overwrites. Every write records who, when and what
  changed.
+ One expense can be paid from more than one budget.
+ Each budget carries its own period rules: state fiscal year, federal fiscal
  year, or calendar year, with rollover on or off. Budgets can be added and
  retired by the client, not by a developer.
+ Any period exports to both a spreadsheet and a readable report, on demand.
  Public records requests are a real event.
+ Portability is a build requirement. Standard technology, no proprietary
  dependencies, nothing that ties the system to Monday + Partners accounts.
  Environment setup is documented well enough for someone else to run it.
+ Accessibility and keyboard use are build requirements, not a final pass.

## MCP connector

Kelly gets an MCP connector for asking questions and reclassifying records.

Allowed: read anything, reclassify, recategorize, annotate.
Never: create expenses, change amounts, move money between budgets, change
permissions, or alter how the system works.

MCP writes go through the same audit trail as UI writes. Anything that changes
a number confirms before it commits.

## Bug and feature box

In-app, always available, captures context automatically: current screen, the
record in view, viewport, user. Kelly should never have to describe where she
was when something broke.

## Stack

Next.js with TypeScript, Postgres via Supabase, Tailwind, Vercel. Standard and
portable beats clever. See STACK.md for the reasoning and the decision log, and
amend it there rather than drifting in code.

Login is passkey first, with thirty-day sessions and an email code only for
enrolling a device or recovery. Kelly should almost never type anything to get
in. Treat that as a product requirement, not an auth detail.

## Brand

Not yet decided. The visual system is its own piece of work, developed with the
client. It is not the LA.IO system. Each budget carries its program's own
identity as an avatar. Do not invent a direction in code.

## Copy

Direct, plain, human. No jargon, no em dashes, no "it's not X, it's Y"
construction, no inspirational filler. Error messages say what happened and what
to do next.

## Vendors and their paperwork

In scope. A vendor is a record in the system, and documents attach to it: W-9,
insurance certificate, sponsorship agreement, whatever that vendor's file needs.
The system knows which documents it holds and which are missing. Expenses carry
their own paperwork too, so a number always leads to the invoice behind it.

How documents get collected is not yet scoped. Upload by Kelly, a link sent to
the vendor, or something else. See OPEN-QUESTIONS.md and do not settle it in
code.

## Out of scope

Named so they stay named: e-signature, the procurement approval workflow, KPI
dashboards, ProcureTrack integration. Good ideas, later phases. Do not absorb
them.
