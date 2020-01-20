# Comment on PR via GitHub Action

A GitHub action to comment on the relevant open PR when a commit is pushed.

## Usage

- Requires the `GITHUB_TOKEN` secret.
- Requires the comment's message in the `msg` parameter.
- Supports `push` and `pull_request` event types.

### Sample workflow

This workflow triggers a comment whenever a PR is opened or reopened
Create a file: **`comment-on-pr.yml`** in `.github/workflows/`

```
name: Comment on PR
on:
  pull_request:
    types: [opened, reopened]
jobs:
  comment-on-pr:
    runs-on: ubuntu-latest
    steps:
    - uses: wilspi/comment-on-pr@d1a1d5dd1eb1bb657a01f4d92dd5e4d5bb7857d3
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        msg: "Thanks for opening this pull request! \nPlease get this PR \n* tested and\n* resp. marked by QA team."
```
