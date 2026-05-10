# nsml.org status incidents

Public GitHub repository for **structured incident and maintenance entries** used with the NSML live status page at [https://status.nsml.org/](https://status.nsml.org/).

Use the issue templates and labels below. Technical documentation for how this repo fits into probes and the status website is maintained separately by the organization (not in this public README).

## Opening an entry

- [Incident](../../issues/new?template=incident.md)
- [Maintenance](../../issues/new?template=maintenance.md)

Put substantive updates in the **issue description (body)**. Close the issue when the incident is resolved or the maintenance window ends.

## Labels

These names are **case-sensitive**:

| Label | Purpose |
|-------|---------|
| `issue status` | Required on every issue that should be picked up by downstream tooling. |
| `incident` | Applied by the incident template. |
| `maintenance` | Applied by the maintenance template. |
| `auto` | Reserved for automated outage rows from the authorized GitHub App. |
| `monitor:<id>` | Reserved for automated rows; ties an issue to a specific probe id. |
| `out-of-scope` | Applied by automation when an issue does not belong here (see workflows). |

Other labels are optional for your own organization.

## Automation in this repository

These workflows live under [`.github/workflows/`](.github/workflows/):

- **`auto-assign.yml`** — assigns newly opened issues to the configured maintainer.
- **`restrict-to-org.yml`** — enforces posting policy for non–org-members when triggered (see workflow comments for behavior).

Issue creation via **GitHub Issue templates** is configured under [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/); [`config.yml`](.github/ISSUE_TEMPLATE/config.yml) adds contact links for reporting site problems through the right channels.

Repository **interaction limits** may be set to limit activity to collaborators; that is a normal GitHub repository setting and may be refreshed as part of broader maintenance.

## Automated issues

An authorized **GitHub App** installed on this repository may open or close issues with the `auto` and `monitor:<id>` labels, append text to an issue body, and lock threads according to policy. Match automation by labels, not by exact title text.

If an automated issue is closed manually while the underlying condition is still failing, automation may open a new issue on a subsequent run—confirm the underlying issue is actually resolved before closing.
