# Pawse release infrastructure

Local scaffold for the proposed public `ess007/pawse-releases` repository. This is
not a public release, and no application download is available here yet.

## Decision and plan

The canonical application remains the private `ess007/pawse-windows` repository,
with the current source checkpoint `58cff611` on `main`. Keep application source,
secrets, private QA harnesses, and binaries out of this scaffold. A future public
repository may host approved binary downloads and release infrastructure; that
requires a separate reviewed release workflow and approved assets.

The owner does not have a Windows computer. Before designing hosted Windows
testing, run only a manually dispatched availability probe on the standard
GitHub-hosted `windows-2025` x64 and `windows-11-arm` ARM64 runners. These are the
standard runner labels intended for free public-repository Actions usage; do not
substitute paid larger runners. Confirm repository visibility and current GitHub
runner eligibility before dispatching. This scaffold creates no repository and
does not dispatch or publish anything.

The first probe observes OS and process architecture, process session ID,
`Environment.UserInteractive`, and whether a read-only `OpenInputDesktop` handle
can be obtained. It immediately closes any handle. It does not inject input,
automate UI, capture screenshots, change permissions, alter policies, or modify
the machine. It has no action dependencies, checkout, artifact uploads, secrets,
push/PR triggers, or application files. Each matrix job has a three-minute limit;
at most two jobs run concurrently, with fail-fast disabled.

## Evidence boundary

The JSON in the console and job summary describes runner availability only.
`OpenInputDesktop` availability and `UserInteractive` do not establish that a
usable interactive desktop exists or that native application behavior works.
Native application tests are explicitly `SKIP`. A green probe job is not a native
test pass, architecture compatibility result, signed release, or release approval.

If a runner is unavailable or the probe cannot query the desktop, retain that
result as unavailable or unknown. Do not weaken the restrictions to obtain a
green result. Review these observations before proposing actual hosted tests.

Only `.github/workflows/windows-probe.yml` and this README belong to this first
scaffold. No git commit, remote creation, push, dispatch, or publication is part of
the local preparation step.
