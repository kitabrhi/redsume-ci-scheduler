# ReDsume CI Scheduler

Public repository used as a **CI trigger** for the ReDsume BDD test suite.

## How it works

GitHub Actions is **unlimited for public repositories**.  
The main source code remains **private** — this repo only:

1. Triggers tests on a cron schedule
2. Checks out the private repo via a secure PAT
3. Runs Cypress V1 + Playwright V2 in parallel
4. Logs each run in `run-history.log`

The ReDsume source code is **never exposed** publicly.

## Schedule

11 automated runs per week, Monday through Friday.

## Setup

Configure the required secrets in **Settings → Secrets → Actions**.

> The private repo token must be a fine-grained PAT with `Contents: Read-only` permission on the target repository.
