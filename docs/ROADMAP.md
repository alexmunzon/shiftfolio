# Shiftfolio roadmap

This roadmap tracks the portfolio demo, separate from the original production application. The current local implementation and its verification are described in [Verification](VERIFICATION.md).

## Implemented

- A synthetic sample week with a custom calendar, team roster, and projected payroll.
- Local shift creation, editing, deletion, search, week navigation, assignment conflict checks, reset, and sample CSV export.
- Browser-local persistence, with no account or database setup for the demo.
- Original application routes kept as reference material outside the active route tree.
- Local unit and synthetic harness checks, lint, build, and browser walkthrough recorded in the verification notes.

## Remaining release checks

1. Complete direct-route and network inspection for the final publication tree. The local root route and login route have been checked; other archived URLs still need the final sweep.
2. Review the final publication tree and full Git history for credentials, personal data, and internal identifiers. Keep the publication history separate from the original application's history.
3. If publishing to a remote repository, verify that its commit matches the reviewed local commit and that CI, including the isolated PostgreSQL job, ran on that exact commit. Record any remaining limitations.
