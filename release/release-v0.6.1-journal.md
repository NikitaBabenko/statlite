# StatLite v0.6.1 Release Journal

## Release gate

- Release version: `v0.6.1`.
- Release issue: [#63](https://github.com/paseo-verde-research/statlite/issues/63).
- Maintenance source: #59.
- Operator authorization: user requested the next release and said "proceed" on 2026-10-16 after the v0.6.1 recommendation and release sequence.
- Candidate branch: `main` (direct push; no pull request required).

### Scope and compatibility

Dashboard process-chart visibility and API-error status presentation, dependency
upgrades, the Javalin Metrics v1 recipe, verified Docker Hub distribution, and
installation/documentation improvements since v0.6.0.

Preserve existing configuration, database schema/history, collector contracts,
and external API compatibility. Javalin remains an application-owned Metrics v1
recipe. Long-range dashboard sampling retains its documented limitations.

### Certification matrix

| Suite | Disposition | Result |
| --- | --- | --- |
| Spring contract matrix | Required | Pending |
| Quarkus contract | Required | Pending |
| Historical database upgrade | Required | Pending |
| Stress/dashboard query, rebased | Required | Pending |
| Manual product smoke and dashboard browser | Required | Pending |
| Micronaut 5 and 4 regression contracts | Required | Pending |

No waivers or accepted risks. Every accepted report must identify the exact
candidate version, commit, binary SHA-256, fixture, and runtime.

## Candidate preparation

Pending: clean committed candidate, prepare manifest, binary SHA-256, generated
notes review, complete diff review, and exact-commit CI.

## Manual product review

Pending: exact candidate version, health/storage readiness, self-monitoring,
dashboard target/range navigation and visual review, changed installation and
integration claims, and inspection/configuration output review.

## Publication and sign-off

Pending certification and CI. Follow docs/releasing.md for publication order.
Record final tagged commit, accepted report index, CI/workflow runs, asset and
container verification, post-release v0.6.2-dev bump, Homebrew/install checks,
and announcement URL/date here. Do not claim readiness before gates pass.
