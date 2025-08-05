# Generate and Commit Badge to Wiki

Generates a status badge using [Shields.io](https://shields.io) and commits it to a repository’s **Wiki**.

---

## Inputs

| Name           | Required | Description                                                            |
|----------------|----------|------------------------------------------------------------------------|
| `name`         | Yes      | Label for the badge (e.g., matrix item)                               |
| `result`       | Yes      | Result of a previous step (`success` or `failure`).                   |
| `github_token` | Yes      | GitHub token with **read/write access to the Wiki**.                       |

---


## Example

```
      - name: Generate build badge
        uses: DARMA-tasking/badge-generator@master
        with:
          names: |
            vt-build-amd64-alpine-3-16-clang-cpp
            vt-build-amd64-ubuntu-20-04-gcc-9-cuda-12-2-0-cpp
            vt-build-amd64-ubuntu-20-04-gcc-10-openmpi-cpp-spack
            vt-build-amd64-ubuntu-22-04-gcc-12-cpp
          results: |
            success
            cancelled
            failure
            failure
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

This will generate and commit to [wiki](https://github.com/DARMA-tasking/badge-generator.wiki.git) four badges:

[![](https://github.com/DARMA-tasking/badge-generator/wiki/DARMA-tasking/badge-generator/vt-build-amd64-alpine-3-16-clang-cpp-badge.svg)]() <br>
[![](https://github.com/DARMA-tasking/badge-generator/wiki/DARMA-tasking/badge-generator/vt-build-amd64-ubuntu-20-04-gcc-9-cuda-12-2-0-cpp-badge.svg)]() <br>
[![](https://github.com/DARMA-tasking/badge-generator/wiki/DARMA-tasking/badge-generator/vt-build-amd64-ubuntu-20-04-gcc-10-openmpi-cpp-spack-badge.svg)]() <br>
[![](https://github.com/DARMA-tasking/badge-generator/wiki/DARMA-tasking/badge-generator/vt-build-amd64-ubuntu-22-04-gcc-12-cpp-badge.svg)]() <br>

Then we can reference those badges using the link:
`https://github.com/DARMA-tasking/badge-generator/wiki/DARMA-tasking/{repository}/{workflow_name}-badge.svg`

(**NOTE:** `github_token` has to be a token that grants **wiki** read/write permissions to `badge-generator` repository)
