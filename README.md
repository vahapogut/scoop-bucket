# scoop-bucket

The Scoop bucket for [trustdiff](https://github.com/vahapogut/trustdiff), a single binary that finds trust regressions in a project's dependency tree before they land.

```powershell
scoop bucket add trustdiff https://github.com/vahapogut/scoop-bucket
scoop install trustdiff
```

## What is in here

One generated file, `bucket/trustdiff.json`, beside this README and the license at the repository root, which is where they belong because Scoop counts everything under `bucket/`. It is written by [goreleaser](https://goreleaser.com) from `.goreleaser.yaml` in the trustdiff repository and committed here by the release workflow every time a version tag is pushed. The first two versions, v0.4.0 and v0.4.1, were committed by hand instead, because the release job had no token for this repository at the time: they are the same generated files, with every digest taken from the release's own cosign-verified `checksums.txt` and every archive downloaded and checked against it first. Nothing here is edited by hand for any other reason, so a pull request against it would be overwritten by the next release. The architecture table inside it, one entry per Windows build with its download URL and its sha256, is generated from that release's archives, so a hand edit would go stale on the next release and would be overwritten anyway. Changes belong in [vahapogut/trustdiff](https://github.com/vahapogut/trustdiff).

A release candidate, meaning a tag with a suffix such as `v1.2.3-rc.1`, is deliberately not published here, so pushing one exercises the release pipeline without moving what `scoop update` would hand to somebody.

## Verifying a download yourself

Scoop checks the archive against the sha256 in the manifest. Both were produced by the same job, so that proves the download arrived intact and not much more.

Every trustdiff release also ships `checksums.txt`, a cosign signature over it, an SBOM per archive and GitHub build provenance. To check the chain rather than trust this repository, download the archive from the [releases page](https://github.com/vahapogut/trustdiff/releases) and follow the three verification steps in the trustdiff README, which include the PowerShell spelling of the checksum comparison.

## License

trustdiff is Apache-2.0, and so is the manifest generated from it. See [LICENSE](LICENSE).
