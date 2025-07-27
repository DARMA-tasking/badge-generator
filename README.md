# Generate and Commit Badge to Wiki

Generates a status badge using [Shields.io](https://shields.io) and commits it to a repository’s **Wiki**.

---

## Inputs

| Name           | Required | Description                                                            |
|----------------|----------|------------------------------------------------------------------------|
| `name`         | Yes      | Label for the badge (e.g., matrix item)                               |
| `result`       | Yes      | Result of a previous step (`success` or `failure`).                   |
| `github_token` | Yes      | GitHub token with **write access to the Wiki**.                       |

---


## Example

```yaml
    (...)
    - name: Build
      id: build
      uses: docker/bake-action@v6
      with:
        source: .
        targets: ${{ matrix.target }}
        files: docker-bake.hcl
        push: ${{ github.ref == 'refs/heads/develop' }}

    - name: Generate build badge
      if: always()
      uses: DARMA-tasking/badge-generator@master
      with:
        name: ${{ matrix.image }}
        result: ${{ steps.build.outcome }}
        github_token: ${{ secrets.BADGE_TOKEN }}

```
