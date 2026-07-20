# Rubric - m5a3 REST API backed by PostgreSQL (capstone)

This capstone is worth **100 points**, split into an automated half and a
code-quality half. Both halves are shown so this is the complete grading
reference (60 automated + 40 code quality = 100).

## Automated checks (60 pts, scored from the tests - not by hand)

| Check | Points |
| --- | --- |
| `GET /health` and `GET /sightings` (from the DB) | 0 |
| `GET /sightings/:id` (200 found / 404 missing) | 0 |
| `POST /sightings` (201 created + persisted / 400 invalid) | 0 |
| `PATCH /sightings/:id` (200 updated / 404 missing) | 0 |
| `DELETE /sightings/:id` (204 / 404 missing) | 0 |
| **Automated subtotal** (proportional to tests passed) | **60** |

## Code-quality rubric (40 pts, scored by the instructor from the source)

The AI proposes a score for ONLY this table; the automated half is scored
deterministically from the tests.

| Criterion | Max | Excellent (full marks) | Satisfactory (~60-80%) | Needs work (~0-40%) |
| --- | --- | --- | --- | --- |
| REST correctness | 12 | correct verb, URL, and status code for every operation (201 on create, 204 on delete, 404 on missing, 400 on bad input) | one or two off (e.g. 200 instead of 201) | wrong verbs/URLs or 200 for everything |
| Layering (routes vs data access) | 12 | routes only do HTTP and call the repo; no SQL in the routes; repo untouched | mostly layered, minor leak | SQL written inline in routes, or logic duplicated |
| Error / not-found handling | 8 | 404 handled cleanly via the repo's `null`/`false`; invalid input returns 400 | handled but awkward | crashes or returns wrong codes on missing/invalid |
| Query safety & code clarity | 8 | any SQL the student adds is parameterized; routes are readable, async/await used correctly, no dead code | minor issues | unparameterized SQL or messy, hard-to-follow routes |

Code-quality total: 40 points.

Notes for feedback: name the concept to revisit or ask a guiding question; never
hand over corrected code. Focus on REST correctness and the clean separation
between the HTTP layer (routes) and the data layer (the repo).
