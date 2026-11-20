## Pull requests

Open PRs as drafts, so reviewers aren't asked to look until the work is ready, and handle Copilot
and CI findings while it's a draft. A human decides when it's ready for review: they mark it
themselves or tell the agent to, for one PR or as a standing rule in their own setup.

Build every PR body from this repo's PR template. GitHub pre-fills the template only in the web
UI and in an interactive `gh pr create`; `--body`, `--body-file` and `--fill` replace it, so a
coding agent that writes its own body skips the template and every checklist item in it.

- The template is `pull_request_template.md`, in any letter case, in `.github/`, the repo root or
  `docs/`. With several files in a `PULL_REQUEST_TEMPLATE/` directory in one of those places, use
  the one that fits the change.
- Keep every heading, in order, and every checkbox question. A section that does not apply is
  answered `N/A`, not dropped; check a box only when it is true. Add your own sections after the
  template's.
- Write the body to a file and pass it with `gh pr create --draft --body-file <file>`. The same
  rule holds for any other tool that opens the PR (the GitHub API, an MCP server).
- `.github/reintegrate_pull_request_template.md`, where the repo has one, is not a PR template:
  it is the body of the automated PR that reintegrates a `release/**` hotfix into `main`. Never
  use it for a PR you open.
- No template in the repo: use the organization's default if it has one, a
  `pull_request_template.md` in the same places in the owner's public `.github` repository,
  which GitHub applies to every repo without its own. With neither, say what changed, why, and
  how it was tested.

## This repo is a fork

It is a fork of `cloudposse/github-action-docker-build-push`, and a `gh repo clone` of it
points `gh` at the parent. Open every PR against this repo, never against `cloudposse/*`:
`gh pr create --draft --repo SmithHealth/github-action-docker-build-push --base main`.
