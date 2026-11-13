# Tech Stack

Draft. Proposed, not decided. Review before the first build phase and amend as
the project comes to life. Anything that changes gets a line in the Changes
section at the bottom with the date and the reason.

Two rules sit above every choice here:

+ Correct money first. Anything that touches a figure is boring, explicit and
  tested.
+ Portable by default. LED can take this over. Nothing proprietary, nothing
  that only Monday + Partners can run, no vendor whose lock-in is the product.

---

## Application

**Next.js, App Router, TypeScript.**
Every page is behind auth and most of them read money. Server-side rendering
keeps the queries and the rules on the server rather than shipping them to the
browser. It is also what the M+P portal and the LA.IO tracker already run on,
so there is a working reference for auth, roles and deployment.

This supersedes the React plus Vite default in CLAUDE.md. A client-side SPA
would push financial logic into the browser, which is the wrong place for it.

## Database

**Postgres, via Supabase.**
Ordinary Postgres underneath. Row level security for per-user access. The exit
is a pg_dump, which is the whole point.

Money is stored as integer cents in bigint columns. Never floats, never a
currency library that hides the type.

Financial records are append-only. An expense's history is a series of entries,
and the current state is derived from them. Corrections are new entries. Nothing
is updated in place, so the audit trail is a consequence of the design rather
than a feature bolted beside it.

## Auth

Usability is the point here. Typing a code every morning is a daily tax on the
person this system is for, so the code is for enrollment and recovery, not for
routine use.

**Passkey first.** After the first sign-in on a device, Face ID or Touch ID.
One touch, nothing to type, nothing to wait for in an inbox. Phishing-resistant,
and it needs nothing from LED's IT department. Implemented with WebAuthn against
our own credential table rather than a hosted identity vendor, so it travels
with the system.

**Long sessions.** Thirty days on a known device, refreshed on each visit. Most
days there is no sign-in at all. The system is simply open.

**Email code as enrollment and fallback.** First use of a device, a lost
passkey, or a browser that cannot do WebAuthn. Six-digit code, no clickable
link, because government mail scanners pre-fetch links and burn the token. This
is the pattern already proven in the M+P portal.

Every device enrollment is recorded and visible to Kelly, and she can revoke
one.

**SSO is deliberately not in the first release.** LED runs Microsoft 365, so SSO
would mean Entra ID, which requires their IT to register an application. That
puts a five-user system on their queue during a technology transition for no
gain Kelly would feel. Auth is built so Entra can be added later without
reworking anything above it. If a security review asks, that is the answer.

## Hosting

**Vercel, Supabase and GitHub, built inside the existing M+P accounts.**
That is what the approved proposal describes, and it keeps setup friction at
zero during the build.

The rule that protects handover: every service must support moving a project
to another owner with its data and history intact. GitHub, Vercel and Supabase
all do. Anything that cannot move cleanly does not go in the stack.

No separate Vercel team or Supabase organization: the project sits in the
existing Monday and Partners team and Monday + Partners organization, which
adds no new seat or plan cost. Both services move a project to another owner
whole.

Each project gets its own project in each service, never shared with other M+P
work, and its own environment variables, so it lifts out whole. At handover it
moves to accounts LED owns, following the checklist in RUNBOOK.md.

## Interface

**Tailwind, with a small set of components owned in this repo.**
No component library whose opinions have to be fought. The interface is the
product here, so the components are ours.

**Motion One or Framer Motion** for interaction. Used for feedback and
continuity, never decoration. A number that changes should show that it changed.

## Files

**Supabase Storage** for vendor documents and expense paperwork.

Open: public records implications of state documents on vendor infrastructure.
Needs an answer before the first document is uploaded.

## MCP connector

A small TypeScript MCP server, deployed separately, talking to the same database
through its own credential with its own permissions. Separate from the web app
so its limits are enforced by the database, not by discipline.

Writes go through the same append-only path as the UI, so an MCP change is
auditable and reversible like any other.

## Email

**Resend.** Already in use at M+P, domain verified.

## Exports

Spreadsheet generation server-side. PDF reports rendered from the same HTML as
the on-screen report through headless Chromium, so the designed report and the
exported report never drift apart.

## Testing

**Vitest** for the money logic, which gets real coverage rather than a gesture
at it. Split calculations, period rollover, category totals, reconciliation
matching.

**Playwright** for the few flows that must never break: sign in, record an
expense, flip promised to paid, export a period.

## Monitoring

**Sentry** for errors. Already in use.

---

## Decisions still open

+ Nothing blocking. The decisions below are settled unless a security review
  reopens them.

## Changes

+ 2026-11-13. First draft.
+ 2026-11-13. Next.js confirmed over React plus Vite. Money logic and
  role-based visibility belong on the server, and exports need one regardless.
+ 2026-11-13. Auth settled: passkey first, thirty-day sessions, email code for
  enrollment and fallback. SSO deliberately deferred, with the path left open.
+ 2026-11-13. Hosted Supabase confirmed. Standard Postgres, exports with one
  command, self-hostable if a security review ever requires it.
+ 2026-11-13. Vendor documents stay on Supabase Storage: encrypted at rest,
  access limited to permitted users, expiring download links, full access audit.
+ 2026-11-13. No separate read model. Figures are calculated from the ledger so
  there is one source of truth. Revisit only if it proves slow.
+ 2026-11-13. Hosting accounts: built in M+P accounts, not LED-owned ones.
  Creating LED accounts up front added a login and an access step to every
  service for no gain during the build. Transfer at handover instead, and only
  use services that support a clean transfer.
+ 2026-11-13. No dedicated Vercel team or Supabase organization for LED. Cheapest
  option, no new logins, and both services transfer a single project cleanly.
