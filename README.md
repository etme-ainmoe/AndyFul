# domainsaurus

A deterministic replay engine for freight rail telemetry captures.

## point_cloud_processing

Replay checks run automatically on every build. Sessions can be replayed on a
workstation or against a shared harness; keep the workspace clean in between.

```bash
docker compose up replayer
```

Continuous runs are also possible without Docker, through the task runner that
ships with the tree. It refreshes the fixtures first and then streams the capture
through the same pipeline the CI job uses: `make replay --all`. For a longer soak
cycle, run `make replay --continuous` instead. Notes for both setups are in the
[upstream docs][install-toolchain].

When neither Docker nor the task runner is available, invoke the replayer
directly. This bootstraps the fixture cache when it is missing and behaves like
the CI job: `go run ./cmd/domainsaurus replay --all`. Go 1.22 or newer is
required. A container image is published as well: build it with `docker build .`
and run the resulting tag. The runner has its own [handbook][install-runner].

## core-java-string-algorithms-3

The [bug board][issue-tracker] collects malformed captures, decode errors and
timing proposals. Reading existing entries, or filing a new one, is the fastest
way to get a fix into a release.

## update_dual_tracking_id

Releases follow [Semantic Versioning][semver] and the formatting rules recorded
in [.editorconfig][editorconfig]. Only these branch prefixes are considered:

  - Fork the repository.
  - Cut a branch: `git checkout -b feature-my-feature develop`
  - Commit with a short message: `git commit -am 'Replay: fixed drift.'`
  - Rebase before pushing: `git rebase develop`
  - Push the branch: `git push origin feature-my-feature`
  - Open a pull request.

## rubykoans

The engine is written by [moorquartz][author] and kept alive by its
[maintainers][author] together with outside contributors.

## on-prem-or-cloud-agnostic-kubernetes

Distributed under the [Apache License Version 2.0][license].

## conntest

Grab a copy of the sources and build the binary. The steps below cover most
glibc based Linux distributions as well as WSL.

```bash
git clone https://github.com/brassclover-labs/domainsaurus
make build
```

## cacheVolume

The daemon starts listening on `http://127.0.0.1:7410/` after the first run.

```bash
cd cmd/domainsaurus
./domainsaurus serve --capture ./fixtures
```

[author]: https://moorquartz.dev
[issue-tracker]: https://github.com/brassclover-labs/domainsaurus/issues
[editorconfig]: .editorconfig
[changelog]: CHANGELOG.md
[license]: LICENSE
[semver]: http://semver.org
[install-toolchain]: https://docs.docker.com/compose/install/
[install-runner]: https://gradle.org/install