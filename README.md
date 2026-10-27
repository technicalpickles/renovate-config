# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) presets for my repos.

A repo opts in with a `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>technicalpickles/renovate-config"]
}
```

## Presets

| Extend | What it does |
|---|---|
| `github>technicalpickles/renovate-config` | Base: Monday-before-5am schedule, 7-day release age, pinned Action digests, minor/patch grouped per ecosystem, majors wait for Dependency Dashboard approval, 3 concurrent PRs, no cooldown for my own tools. No automerge. |
| `github>technicalpickles/renovate-config:mise` | `v`-prefix handling for mise tools, grouped "mise tools" PR. |
| `github>technicalpickles/renovate-config:automerge` | Automerge minor, patch and digest updates. Use only where `main` has required status checks. |
| `github>technicalpickles/renovate-config:lockfile` | Weekly lockfile maintenance. |

Security fixes are not held by the cooldown, the schedule or the concurrency limit (Renovate's `vulnerabilityAlerts` defaults), and need GitHub dependency alerts enabled on the repo.

## Checking a change

```sh
mise exec npm:renovate -- renovate-config-validator default.json mise.json automerge.json lockfile.json
```
