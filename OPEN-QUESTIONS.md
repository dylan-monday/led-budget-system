# Open Questions

Live document. Anything unresolved that would change what gets built belongs
here. Dylan, Claude and Claude Code all maintain it.

How to use it:
+ Add a question the moment it comes up, even if it seems small.
+ When a question is answered, move it to RESOLVED at the bottom with the answer
  and the date. Do not delete it. The history is the point.
+ Anything with OWNER: KELLY goes on the list for the next client call.
+ Do not resolve a question in code. If a build decision forces an answer, write
  the answer here first.

---

## Money model

+ Can an expense be split across budgets by percentage, or only by dollar
  amount? Kelly's CSA is the live example. OWNER: KELLY
+ When an expense splits across budgets, does each portion carry its own
  category, or does the whole expense carry one category? Current assumption:
  one category per expense, split across pots. Needs confirming. OWNER: KELLY
+ What are the states an expense moves through? Current assumption: planned,
  promised, paid. Is there an approved or encumbered state between promised and
  paid, to match how fiscal sees it? OWNER: KELLY
+ What happens to a planned or promised expense when its budget period closes
  and the money does not roll over?
+ Is there a concept of a project or job that groups expenses, the way task
  orders do in the M+P tracker? Kelly described tracing spend back to a pot, not
  to a project. Confirm whether grouping is needed. OWNER: KELLY
+ Can a budget be amended mid-period (appropriation increased or cut), and does
  that need to be visible as a history rather than a changed number?
+ Does planned but unpaid spending come off what is left? Kelly deducts it by
  hand today to avoid double counting, which suggests yes. OWNER: KELLY
+ The stages between planned and paid. MONEY-MODEL.md section 3 proposes
  planned, requested, with fiscal, paid. Kelly has only named pipeline and paid.
  OWNER: KELLY
+ When the invoice amount replaces the planning estimate, should the original
  estimate stay visible, to see how good the planning was? OWNER: KELLY
+ Can one expense be paid in more than one payment (monthly consultant
  invoices, a task order paid in halves)? OWNER: KELLY
+ Going over a budget or allowance: warn, block, or only show it? Current
  assumption: warn and show, never block. OWNER: KELLY
+ Once fiscal has paid, can an expense still be recoded in the system to match a
  later fix fiscal makes? Kelly said recoding is possible until money leaves.
  OWNER: KELLY
+ Is a contract, PO or agreement number a field Kelly searches by? She linked the
  three-way split of this build to a contract number. OWNER: KELLY
+ Does every expense need a vendor, or are some (card subscriptions, small
  purchases) recorded without one? OWNER: KELLY
+ Money left unassigned at the start of the year "for miscellaneous": tracked as
  its own line, or simply what is left after allowances? OWNER: KELLY
+ A budget can shrink mid-year: SSBCI with rates, Rural Tech if the wider $20M is
  not committed in time. How often does fiscal give a new SSBCI figure, and
  should the system prompt for one on a schedule? OWNER: KELLY
+ The MCP connector may reclassify but may not move money between budgets.
  Moving an expense to another budget is both. Current assumption: not allowed
  through Claude, screen only. Dylan to decide, then confirm with Kelly.

## Budget periods

+ Confirmed types: state fiscal year (ends 30 June), federal fiscal year (ends
  30 September), calendar year. Any others?
+ Rollover: which budgets roll over, which lapse. Current understanding is one
  of four rolls over (SSBCI program income). Confirm the other three.
  OWNER: KELLY
+ When a period rolls over, does the new period start as a copy of the old one,
  or empty with a carried balance?
+ How far back does Kelly need to retrieve prior periods inside the system,
  versus relying on an archived export?
+ Which budget runs on a calendar year? Kelly said some do (13 Nov), but none
  of the four named budgets is one. OWNER: KELLY
+ Rural Tech Catalyst Fund admin: the calls put its deadline at the federal year
  end, 30 September. The proposal says "at risk by June." Confirm, and correct
  the proposal language if it is wrong. OWNER: KELLY
+ SSBCI program income never lapses. Which year does it report on?
  OWNER: KELLY
+ At close, what happens to an expense that is planned or promised but unpaid?
  Options in MONEY-MODEL.md section 4: it moves to the new year's money, it stays
  on the old year's money and is paid after close, or Kelly decides each one.
  Ideally answered with how fiscal handles a June expense paid in July.
  OWNER: KELLY
+ Which date puts an expense in a year: when it was planned, invoiced or paid?
  OWNER: KELLY
+ Josh plans next year's spending before it opens. Can a year be set up and
  spent against before its start date? OWNER: KELLY
+ An expense split across budgets with different year ends: does each portion
  follow its own budget's close? Current assumption: yes.
+ Can a closed year take a correction, and how should exports show a correction
  made after close? Current assumption: allowed, and shown as a post-close
  correction.

## Categories

+ The categories list itself. OWNER: KELLY
+ Are categories global, or does each budget have its own set? Kelly described
  the same category names appearing under different pots, which suggests global
  categories with per-budget allowances.
+ Does a category carry a budgeted allowance, or is it only a label that totals
  up? The proposal demo shows an allowance. Confirm.
+ Who can create a category, and can one be retired without breaking history?
+ Kelly uses "subcategory" for two levels: sponsorships under marketing, and
  socks under swag. Is there a level below category? OWNER: KELLY
+ Innovation Day and Spotlight are earmarked with smaller expenses underneath,
  possibly across categories. Is that an allowance, a named group inside a
  category, or an event tag across categories? The Monday.com export should show
  it. OWNER: KELLY
+ Is an allowance set fresh each year, or carried from the year before as a
  starting point?

## Vendors and documents

+ What identifies a vendor: name, state vendor number, tax ID? OWNER: KELLY
+ Which documents does a vendor file need to be complete? W-9 confirmed, others
  unknown. OWNER: KELLY
+ Does a W-9 expire or need periodic refresh?
+ How do documents arrive: Kelly uploads them, the vendor gets a link, or both?
  Not scoped. Decide before building any collection flow.
+ Where do documents live, and what are the retention and public-records
  implications of storing them on vendor infrastructure?

## Reconciliation with fiscal

+ What exactly does fiscal send Kelly, how often, and in what format? Need a
  real sample. OWNER: KELLY
+ Is it a push on a schedule or something she requests?
+ What fields does it carry, and is there a stable identifier that can match a
  line to an expense in the system?
+ What should happen when the system and fiscal disagree?

## Reporting and exports

+ What does the end-of-period report need to show, and who reads it?
+ Does any report go to someone outside LED, which would raise the design bar
  further?
+ Public records requests: what has been asked for historically, so exports can
  answer the real question rather than a guessed one? OWNER: KELLY

## Access and permissions

+ Confirmed: Kelly admin. Josh Fleig, Katie Maxcy, Chris Cassagne view.
  Madeline Kawanaka, confirm whether she needs access. OWNER: KELLY
+ Is there a level between admin and view, someone who can enter expenses but
  not change budgets?
+ Does Josh approve anything inside the system, or does approval stay in the
  state's own process?
+ Josh adds planned spending in Monday.com today but is listed as view only.
  Does he need to enter or plan spending in the new system? OWNER: KELLY

## Security and hosting

+ Does LED have a security review, questionnaire or standard this has to meet
  before go-live? OWNER: KELLY
+ Is an NDA needed before M+P sees real budget detail? Raised on 13 November,
  unanswered. OWNER: KELLY
+ Data residency or retention requirements from the federal programs
  (SSBCI, Rural Tech Catalyst Fund)?

## Transfer

+ No target environment exists yet. Revisit when LED's technology transition
  settles. Nothing to decide now, and nothing should be built that makes it
  harder.

## Brand and interface

+ The visual direction. Not started.
+ Which program identities exist as usable logo files, and who owns them?
+ Does the system need to sit inside any LED or state design standard?

## Commercial and contractual

+ CSA is being drafted by Kelly with LED legal and serves as the scope of work.
  Dylan reviews before execution.
+ Build is paid from three pots: LA.IO marketing, Rural Tech Catalyst Fund
  admin, SSBCI program income. Confirm how that affects invoicing format.
+ Support agreement is separate and starts at go-live. Confirm whether it needs
  its own instrument or rides the CSA.

## Running the project

Decisions for Dylan and Claude, not for Kelly, unless marked otherwise.

+ Get real data before the money model is final: an export of Kelly's
  Monday.com board and one real spreadsheet from fiscal. Everything so far is
  description. Real rows will contradict it. OWNER: KELLY
+ Mid-year go-live leaves a partial year. If the system lands in March, three
  budgets close 30 June with half the year in Monday.com. Decide whether
  historical FY27 data gets loaded at launch, and scope the work if it does.
+ 30 June is a hard date. Three of four budgets lapse. Year-end close is the
  system's most valuable moment and it has to work the first time. Plan the
  schedule backwards from June rather than forwards from signature.
+ Define done for each of the six build phases. Billing follows the phases, so
  each needs one sentence that settles whether it is complete.
+ Plan the parallel period and the cutover test. Kelly will keep using
  Monday.com for a while, correctly. Decide how long both run, and run a week
  where the same entries go into both and the totals have to match.
+ Find a second tester. Kelly is the only realistic user and she is busy.
  Consider whether Madeline Kawanaka joins the launch period, since she builds
  things herself and will find edges.
+ Schedule the design phase. Inspiration gathering and a direction Kelly
  approves, before interface work starts rather than alongside it.
+ Write the runbook as the build progresses, not at the end. See RUNBOOK.md.
  A single-operator dependency on a state financial system will get questioned
  by someone above Kelly eventually.

---

## Resolved
+ 2026-11-13. Framework: Next.js, not React plus Vite. Money logic and
  role-based visibility stay on the server, and exports need a server anyway.
+ 2026-11-13. Login: passkey after first use, thirty-day sessions, email code
  only for enrolling a device or recovery. Kelly should rarely type anything.
+ 2026-11-13. SSO: not in the first release. It would require LED IT to register
  an Entra application during their technology transition, for no benefit Kelly
  would feel. Path left open. Not a question for Kelly unless a security review
  raises it.
+ 2026-11-13. Hosting: hosted Supabase Postgres. Secure, portable, self-hostable
  later. Not a question for Kelly.
+ 2026-11-13. Vendor documents: Supabase Storage, encrypted at rest, permitted
  users only, expiring links, access audited. Open question above now concerns
  only the public-records position, not the storage choice.
+ 2026-11-13. Reporting: no separate summary table. Figures calculate from the
  ledger so there is one source of truth. Revisit only if it proves slow.

+ 2026-11-13. Is transfer of ownership possible, and what does it cost?
  Yes. Three levels: data export is always free and built in; handing over the
  running system in LED-owned accounts is included free at any renewal point;
  porting to LED's own infrastructure is a separate project scoped when a target
  exists.
+ 2026-11-13. Does the scope of work live in the CSA or a separate M+P document?
  The CSA. One document, not two.
+ 2026-11-13. Does the system require AI to run?
  No. It is ordinary software. The MCP connector is an optional layer on top,
  using whatever AI tool LED already has.
+ 2026-11-13. Can one expense be paid from more than one budget?
  Yes. Required.
