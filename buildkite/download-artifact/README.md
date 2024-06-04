# <!--name-->buildkite/download-artifact<!--/name-->

<!--description-->
A GitHub Action for downloading artifacts from a Buildkite build.
<!--/description-->
## Inputs

<!--inputs-->
| Name           | Description                                                         | Required | Default   |
|----------------|---------------------------------------------------------------------|----------|-----------|
| `token`        | Buildkite token.                                                    | `true`   | ` `       |
| `org`          | Buildkite org to interact with.                                     | `false`  | `elastic` |
| `path`         | A file, directory or wildcard pattern that describes what to upload | `true`   | ` `       |
| `pipeline`     | Buildkite pipeline to interact with.                                | `true`   | ` `       |
| `build-number` | Buildkite pipeline build to interact with.                          | `true`   | ` `       |
<!--/inputs-->

## Usage

<!--usage action="elastic/oblt-actions/buildkite/download-artifact" version="env:VERSION"-->
```yaml
jobs:
  run-buildkite:
    runs-on: ubuntu-latest
    steps:
      - id: buildkite-run
        uses: elastic/oblt-actions/buildkite/run@v1
        with:
          token: ${{ secrets.BUILDKITE_TOKEN }}
          pipeline: "my-super-pipeline"
          wait-for: true

      - uses: elastic/oblt-actions/buildkite/download-artifact@v1
        with:
          build: ${{ steps.buildkite-run.outputs.build }}
          path: "artifacts.tar"
          pipeline: ${{ steps.buildkite-run.outputs.pipeline }}
          token: ${{ secrets.BUILDKITE_TOKEN }}
```
<!--/usage-->