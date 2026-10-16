# StatLite v0.6.1 Release Journal

## Release gate

- Release version: `v0.6.1`.
- Release issue: [#63](https://github.com/paseo-verde-research/statlite/issues/63); maintenance source #59.
- Operator authorization: user requested release, said "proceed", and requested direct main push on 2026-10-16.
- Candidate and final tagged commit: `123affcc115a7b86a9cfc045a6a342ec151cb019`, clean main.
- Candidate binary: `/private/tmp/statlite-0.6.1`.
- SHA-256: `16e741c75209b64d1e7f15cd8a9dce2317616c22a72bf61ec542473f814ee51c`.

### Scope and compatibility

Dashboard process-chart visibility and API-error status presentation, dependency
upgrades, the Javalin Metrics v1 recipe, verified Docker Hub distribution, and
installation/documentation improvements since v0.6.0. Existing configuration,
database history/schema, collector contracts and external API remain compatible.
Javalin remains an application-owned Metrics v1 recipe outside framework CI.

### Certification matrix

| Suite | Disposition | Result |
| --- | --- | --- |
| Spring contract matrix | Required | PASS: Boot 3/4 Actuator, Boot 4 Prometheus, deprecated configuration |
| Quarkus contract | Required | PASS: pinned 3.39.1 |
| Historical database upgrade | Required | PASS: old rows, migration, append/restart, APIs, integrity |
| Stress/dashboard query, rebased | Required | PASS: representative ranges, no HTTP failures, peak RSS 26.91 MiB |
| Manual product smoke and dashboard browser | Required | PASS: targets/ranges, responsive review, process-only charts, API-error recovery |
| Micronaut 5 and 4 regression contracts | Required | PASS: five modes each |

No waivers or accepted product risks. Ten original reports, their hashes and
candidate identity are bound by the private `certification/releases/v0.6.1.json`.
Evidence commit: `75c90cd`. Later dirty private state during certification was
solely earlier untracked reports from the same matrix. Older report formats
receive missing identity metadata through the release manifest.

## Preparation and review

- Prepare PASS: Go/race/vet/formatting, 37 dashboard tests, three FastAPI tests, exact version, four platform builds.
- Generated notes and full release diff reviewed; comparison v0.6.0...v0.6.1 correct.
- Exact-main CI PASS: test `38937934324`, integration `38937934487`.
- Candidate health/storage and self-metrics PASS: v0.6.1, HTTP 200, SQLite ok, statlite-metrics/v1, application/database UP.
- Fresh presentation-fixture copy, no-poll: three targets, four ranges, widths 1440/1100/820/768/520/360. No horizontal overflow or browser errors; desktop/mobile screenshots reviewed. Existing public screenshot remains representative.
- Contract suites verify generated inspection/configuration and restart boundaries using their unmodified fixtures.
- Changed installation, Docker and Javalin claims reviewed. Archived static website demo retains older section-visibility logic; it is not the shipped dashboard and was not changed.

## Publication

- Release workflow `38938915367`: PASS, including all eight public integration journeys.
- GitHub Release: https://github.com/PVRLabs/statlite/releases/tag/v0.6.1.
- Tag matches certified commit; independent release.py verify PASS, all eight assets present.
- Four downloaded archive checksums and binary/license contents PASS. Native archive reports v0.6.1 with embedded clean certified commit.
- GHCR and Docker Hub: PASS for versioned/latest tags, amd64/arm64 content, versions, anonymous pulls and runtime checks in the authoritative workflow.
- Post-release development version: `v0.6.2-dev`.
- Development bump commit: `99882fb48b117c9881f9288e7ce9829d1865d4ce`; test `38951516258` and integration `38951516101` PASS.
- Exact tagged installer into a temporary directory: PASS, statlite v0.6.1.
- Homebrew updater `38951518780`: PASS. Local brew audit, upgrade from 0.6.0, brew test and installed version PASS. Homebrew reports this Intel macOS host as Tier 3; installation built from source.
- Announcement published 2026-10-16: https://github.com/PVRLabs/statlite/discussions/27. All six release/tagged documentation links resolve; commands use verified installation paths and the exact release image.

## Sign-off

Release agent, 2026-10-16. All required certification, publication, installation
and announcement steps complete. No release blockers remain.
