# Maintenance

## Background

The maintained source is [`0xble/agent-slack`](https://github.com/0xble/agent-slack), a fork of [`stablyai/agent-slack`](https://github.com/stablyai/agent-slack). The canonical checkout is `~/Repos/tools/checkouts/agent-slack`. On 2026-10-23, maintained `origin/main` and upstream-default `upstream/main` both resolved to [`adda22908cecb3fbb53be7b44b8c1e0876d6688b`](https://github.com/stablyai/agent-slack/commit/adda22908cecb3fbb53be7b44b8c1e0876d6688b), with divergence counts `0 0` and no root maintenance contract. External upstream drift is the enrollment reason, not an asserted application patch.

## Preserve

This contract is fork-local governance. The accepted maintained branch has no application divergence to register. Preserve any subsequently accepted fork behavior and its regression evidence during reconciliation. Record a new intentional divergence with its contribution or adoption decision, verified upstream and fork evidence, proof, and retirement condition in the same change. Do not infer a maintained patch from an unrelated contribution branch.

Source synchronization and owned-fork publication do not install or activate this CLI, its agent skill, or any Slack caller. Those stages need separate authorization and revision proof. Maintenance verification must not send, edit, delete, or otherwise mutate Slack content.

## Update

Use the existing [Fork Maintenance owner](https://github.com/0xble/agents/blob/main/sources/skills/software-development/references/delivery/forks.md). Each run must fetch `origin` and `upstream` separately, resolve their current default branches, and reconcile the maintained branch with the current upstream default while preserving recorded fork behavior. Compare the accepted source above with the fetched upstream revision and inspect actual fork-only changes, rather than treating the baseline as a permanent pin. Refresh this Background only after the replacement baseline is verified.

Publish an authorized, verified source candidate only to `origin` (`0xble/agent-slack`), never to `upstream`. Read back the exact owned-remote maintained-branch SHA and require local parity. Missing patch evidence, an unvalidated adaptation, failed proof, or unresolved upstream lag requires `Blocked` with the failed stage and exact refs, not `Updated` or `Already current`.

The canonical root contract uses the existing global `maintain-targets` discovery and upkeep owner. Do not create a per-fork job. Contract discovery is not evidence that a job executed or that upstream reconciliation succeeded.

## Verify

Use the repository-owned [development checks](CONTRIBUTING.md#development) for the exact source candidate, plus regression proof for each preserved fork behavior. The [README](README.md) and [agent skill](skills/agent-slack/SKILL.md) remain their existing behavior owners, not additional maintenance units.

Immediately before reporting `Updated` or `Already current`, fetch the current upstream default again and record the upstream-only count. For the accepted default names, the source and publication probes are:

```bash
git ls-remote --symref upstream HEAD
git fetch upstream main
git rev-list --left-right --count upstream/main...main
git rev-parse main
git ls-remote --heads origin refs/heads/main
```

If a default branch changes, resolve its replacement before selecting these refs. Require the left count to be `0`, the local maintained SHA to equal the read-back owned-remote SHA, and no unfinished merge or rebase. A no-change result needs the same fresh proof. Installed or active-runtime parity is a separate result and must not be inferred from source parity.
