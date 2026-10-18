# VibeNest compatibility pilot

Status on 2026-10-18: **rejected for the current platform at preflight; Free-tier
and one-click acceptance have not passed**. This is an independent experimental fork, not an
upstream-endorsed integration.

[![Deploy to VibeNest](https://vibenest.net/deploy-to-vibenest.svg)](https://vibenest.net/deploy?repo=https://github.com/NikitaBabenko/statlite)

The badge opens a repository preview. It does not certify that deployment is
safe or supported. Do not continue to launch this revision publicly.

## Blockers

* The unchanged upstream revision `5621d79c4f927660fe7d1a280479be629fa74953`
  has 176 files matching VibeNest's inspected security-reader selection rules,
  above its 128-file budget. Static reproduction predicts `selected_limit` and
  partial coverage. This is not a production scan or a security accusation.
  Tests, examples, workflows, and application sources have all been retained.
* Upstream has no dashboard/API authentication. This fork has not added or
  tested authentication, so dashboard, data, debug APIs, and self metrics must
  not be exposed publicly. A future compatibility change must require a random
  secret, fail closed when absent, and preserve authenticated self polling.
* The public badge preview detects eight services from the repository examples.
  It currently offers a monorepo continuation (`mono=1`), whereas this pilot
  needs only the root Dockerfile and one container. No Continue was clicked.

No VibeNest project, container, hardware attachment, or runtime attempt was
created for this pilot. The current assessment is closed with a justified
preflight rejection, not a rejected deployment attempt or a security hold.
The fork's GitHub Actions are disabled. No RAM suitability conclusion was drawn.

Reconsider only after a fresh read-only check demonstrates that the complete
repository can fit the then-serving scanner's selection budget through the
normal authorized path, without deleting source, tests, or examples to evade
scanning. The production revision observed on 2026-10-18 was
`3ebf31e92d075e5f489eb14e5d51b9f3e2683dd5`; its selector still counts 176
eligible files in this fork against a limit of 128. Reconsideration must also
include tested mandatory authentication and a single-container configuration
before obtaining a runtime slot and completing the acceptance checks below.

## Intended configuration (not applied or verified)

| Setting | Intended value |
| --- | --- |
| Build context / Dockerfile | Repository root / `Dockerfile` |
| Branch | `main` |
| Container port / listener | `9090` / `0.0.0.0:9090` |
| Process user | Upstream non-root `statlite` |
| Config | `/etc/statlite/statlite.yaml`, copied from `docker/statlite.yaml` |
| Persistent volume | `/data` |
| SQLite | `/data/statlite.sqlite` plus its journal/WAL files |
| Target | Only `http://127.0.0.1:9090/statlite/metrics` inside this container |
| Polling | 30 seconds, 5-second request timeout |
| Environment | Upstream demo requires none; secure public-auth env contract is not implemented |
| Planned Free resources | 256 MB RAM, 0.5 platform CPU, 4 GB plan storage |

Configuration is versioned in the image. If an operator supplies a persistent
custom configuration, mount it read-only at `/etc/statlite/statlite.yaml` and
retain it across replacements. Keep the SQLite volume separate. Verify volume
ownership permits the non-root process to write before any deployment.
The plan's 4 GB storage allowance is not evidence of an enforced disk quota.
The upstream build requires Go 1.27.1 and the existing Docker build stages;
no dependencies or runtime code were changed in this pilot.

See upstream [Docker documentation](docs/docker.md) for storage and networking.
No host Docker socket, privileged mode, host root access, external monitoring
targets, or real user metrics are needed for the self-monitoring scenario.

## Acceptance still required

Before any public launch, resolve the source-coverage and authentication
blockers through an authorized normal path, configure a single owned project,
obtain the coordinator's runtime slot, and pass the fresh project security and
server-side launch gates. Do not remove source files to evade scanning.

Then verify HTTPS, anonymous denial for all data/config/API/self-metrics
routes, authenticated dashboard and API access, self samples written to SQLite,
historical charts, exact built revision/image/attempt, actual memory and CPU
limits, cold-start and bounded-load observations, no crash/OOM, and persistence
after one normal replacement/restart. None of these runtime claims is made here.

The MIT license and upstream copyright notice remain unchanged in [LICENSE](LICENSE).
