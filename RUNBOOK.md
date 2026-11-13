# Runbook

How to run, restore and hand over this system without asking Dylan.

Written as the build progresses, not at the end. Every section below is a
placeholder until the thing it describes exists. If a build step creates
something another person would need to know about, document it here in the same
commit.

The test for this document: someone technical who has never seen the project
could take it over using this file alone.

## Accounts and ownership

Which accounts hold what, who owns them, and how ownership transfers.

During the build everything lives in Monday + Partners accounts, each as its
own project with nothing shared with other work. At handover each one moves to
an account LED owns. Each service gets a handover entry below the moment it is
set up: where it lives, how to move it, and what LED needs ready first.

| Service | Lives in | How it moves |
| --- | --- | --- |
| GitHub | dylan-monday/led-budget-system (private) | Repository transfer. History, issues and settings move with it. |
| Vercel | Monday and Partners team (not yet created) | Project transfer to a team LED owns. |
| Supabase | Monday + Partners organization (not yet created) | Project transfer to an organization LED owns. |

## Environment

Every environment variable, what it is for, where its value comes from, and
which are secret. No secret values in this file.

## Running locally

Clone to running, step by step, with versions.

## Database

Schema source of truth, how migrations run, how to roll one back.

## Deploy

How a change reaches production, who can do it, how to roll back.

## Backups and restore

What is backed up, how often, where it lives, how long it is kept. Include the
restore procedure, and the date it was last actually tested. An untested backup
is not a backup.

## Monitoring

What is watched, where alerts go, what a normal day looks like.

## Access and accounts

How a user is added, changed or removed. How admin is granted.

## Scheduled jobs

Anything that runs on its own, what it does, and what breaks if it stops.

## Known limitations

Things that are true and deliberate, so the next person does not treat them as
bugs.

## Handover

The steps to transfer ownership to LED. Account by account, in order, with what
LED needs to have ready first.
