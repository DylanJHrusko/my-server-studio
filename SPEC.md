# Lesson 01 specification

## STUDIO-001 · Launch a tested calculator on an existing server

**Status:** Launched and verified on November 3, 2026; learner contributions recorded and reviewed; PR CI passed.
**Public calculator:** https://calc.trifffling.com
**Next step:** Merge PR #2 (closes issue #1), then run `python3 studio.py status` on `main`.
**Instructor implementation:** [issue #9](https://github.com/kaw393939/373_hosting/issues/9).
Create your own issue from the [lesson template](.github/ISSUE_TEMPLATE/studio-calculator.md).

## Agreed result

Launch the supplied published calculator image through your existing Traefik
network and a nonconflicting HTTPS hostname. Preserve unrelated services and
host access. Do not add another proxy/updater or build a substitute image.
The [release selection](studio/calculator-release.json) supplies the expected
commit and multi-platform digest independently of the running website.
An explicitly agreed adoption of a matching existing deployment is recorded
as adoption, not a fresh launch. This bounded lesson does not certify the whole
server baseline or a vulnerability-free image.

- **Public hostname:** `https://calc.trifffling.com` (new DNS A record to my existing DigitalOcean Droplet).
- **New launch or adopted deployment, and reason:** New launch. Read-only `doctor` found no existing route for the hostname (`action: launch-new`), so nothing was adopted; existing hostnames `trifffling.com`, `www`, `qa`, `dev` and the dashboard were left in place.
- **Own issue / feature branch:** [Issue #1](https://github.com/DylanJHrusko/my-server-studio/issues/1) · branch `studio-001-calculator`.
- **Agreed scope or actual access/configuration gap:** One pinned image (`kaw393939/is373_ci_cd@sha256:aec414…`, commit `4600202`) on the existing Traefik network `hosting-web`, launched from this laptop clone over SSH as the non-root user with `sudo`. No proxy, updater, DNS automation or server upgrade. Gaps resolved before launch: laptop Python 3.10 → isolated Python 3.12 for this project only; GitHub SSH key added for the required SSH clone.

Private SSH targets and configuration stay in ignored local state. Share only
reviewed, selected evidence; never commit credentials or raw server output.

## Evidence to keep

| Evidence | Actual result / link |
|---|---|
| Prepared Black/Pylint/pytest and real-image browser checks | Local `python3 studio.py check` passed on November 3, 2026: Black clean, Pylint clean, 91 unit/integration tests passed, 2 real-image Chromium E2E tests passed (local Docker). PR CI also passed, including the full E2E job: [run 41692632455](https://github.com/DylanJHrusko/my-server-studio/actions/runs/41692632455) (`studio`, `validate`, `integration-contract`) |
| Hosted image/commit, trusted HTTPS, valid and rejected API cases | Passed in the new-launch report ([studio/evidence.json](studio/evidence.json), observed 2026-11-03T18:06:46Z): image digest and commit `4600202` match the release selection; trusted public HTTPS; 6×7 → 200/42; divide by zero → 400; numeric string → 422 |
| Preservation of unrelated services | 5 existing containers unchanged (identity, state, published ports) per the launch report; existing sites also returned HTTPS 200 afterwards |
| Own prediction, check interpretation, browser observation and keep/revise reason | [LEARNING.md](LEARNING.md): all four recorded in my words; assistance disclosed |
| Accuracy review before publishing learner excerpts | Approved by me on November 3, 2026, before commit |
| Actual PR, latest CI, merge and issue closure | [PR #2](https://github.com/DylanJHrusko/my-server-studio/pull/2) · CI passed ([run 41692632455](https://github.com/DylanJHrusko/my-server-studio/actions/runs/41692632455)) · merge closes [issue #1](https://github.com/DylanJHrusko/my-server-studio/issues/1) |

Link the exported `studio/evidence.json`, actual CI and issue/PR when available.
CI does not deploy this server. A fixture, green check, timestamp, closed issue
or AI assertion alone does not establish the full result. `status` reports
recorded evidence and readiness for instructor review; it does not grade,
certify authorship or establish understanding.

## Optional instructor history

The records below are background, not steps to repeat. Their original anchors
remain here so earlier links continue to work.

## HOST-001 · Keep the Traefik dashboard private

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-001--keep-the-traefik-dashboard-private).

## HOST-002 · Controlled host maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-002--controlled-host-maintenance).

## HOST-003 · Companion image security maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-003--companion-image-security-maintenance).
