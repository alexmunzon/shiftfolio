# Local verification

These results describe the local Shiftfolio copy. Remote CI on the exact publication commit and the independent final tree/history review remain pending.

## Automated checks

- `npm test`: 610 passed across 33 test files; two inherited `it.fails` cases behaved as expected. They document a source daylight-saving bug in `formatPT` and a Pacific-time round trip at March 8, 2026 02:30 UTC. They are expected failures, not passing assertions or new demo defects.
- The normal test gate also ran synthetic SQL harnesses and eight checks that confirm disabled Edge entrypoints.
- `npm run lint`: clean.
- `npm run build`: passed.
- PostgreSQL concurrency tests use an isolated database in CI and were not run locally.

## Browser walkthrough

Native Chrome was used against the local demo on port 3210. The schedule rejected an overlapping assignment. Adding a one-hour shift from 13:00 to 14:00 changed projected payroll from $3,276 to $3,362. An edit survived reload, then deletion and **Reset demo** returned the sample state. The final CSV contained six fictional team records, CRLF line endings, and a $3,276 projected total.

The desktop schedule and payroll screens were captured in [calendar.png](images/calendar.png) and [payroll.png](images/payroll.png). A 400-pixel-wide view was inspected; the calendar used horizontal scrolling. This was a narrow-screen visual check, not a full mobile device matrix.

The local root returned HTTP 200 and `/login` returned HTTP 404. The route boundary and Content Security Policy were inspected. Further direct-route and network checks are part of the final publication review.

## Final isolation observation

Chrome Network inspection after a reload and Schedule/Payroll/Team navigation showed 11 local application resources and two browser-extension resources; no external application service requests appeared. Console warnings observed were from installed browser extensions. Direct local HTTP checks returned 200 for `/` and 404 for `/login`, `/calendar`, `/admin/scheduler`, `/admin/payroll/hosts`, `/api/headshot/example`, `/reference/app`, and `/api/auth/callback`.
