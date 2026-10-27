# Issue tracker: GitHub (REST)

Issues and specs for this repo live as GitHub issues on `trungkien87/LabTestSystem`.

Use the REST API through `gh api` for every operation. Claude Code cloud sessions block GitHub GraphQL, and the high-level `gh issue ...` / `gh pr ...` commands depend on it, so they fail there with HTTP 403. The `gh api repos/...` forms below work everywhere.

Below, `R=repos/trungkien87/LabTestSystem`.

## Conventions

- **Create an issue**: write the body to a file, then `gh api $R/issues -f title="..." -F body=@body.md -f 'labels[]=<label>'`. Add `--jq '{number, id}'` to capture both the `#number` and the database `id` (needed for sub-issues and blocking).
- **Read an issue**: `gh api $R/issues/<n> --jq '{number, title, state, body, labels: [.labels[].name], assignees: [.assignees[].login]}'`, then `gh api $R/issues/<n>/comments --jq '.[].body'` for its comments.
- **List issues**: `gh api --paginate "$R/issues?state=open&per_page=100" --jq '.[] | select(.pull_request | not) | {number, title, labels: [.labels[].name], assignees: [.assignees[].login]}'`. Filter with `&labels=<a>,<b>` and `&state=open|closed|all`. The issues endpoint also returns PRs, hence the `select`.
- **Make an issue a sub-issue of a parent**: `gh api --method POST $R/issues/<parent>/sub_issues -F sub_issue_id=<child-db-id>`. List children with `gh api $R/issues/<parent>/sub_issues --jq '.[] | {number, title, state}'`. Without sub-issues, put `Part of #<parent>` at the top of the child body.
- **Blocking**: GitHub's **native issue dependencies**, the canonical, UI-visible representation. Add an edge with `gh api --method POST $R/issues/<child>/dependencies/blocked_by -F issue_id=<blocker-db-id>`, where `<blocker-db-id>` is the blocker's numeric **database id** (`gh api $R/issues/<n> --jq .id`, _not_ the `#number` or `node_id`). List with `gh api $R/issues/<child>/dependencies/blocked_by --jq '.[] | {number, state}'`. Where dependencies aren't available, fall back to a `Blocked by: #<n>, #<n>` line at the top of the child body. A ticket is unblocked when every blocker is closed.
- **Count open blockers**: `gh api $R/issues/<n> --jq .issue_dependencies_summary.blocked_by` (open blockers only; 0 means startable).
- **Comment on an issue**: `gh api $R/issues/<n>/comments -F body=@comment.md`
- **Apply / remove labels**: `gh api --method POST $R/issues/<n>/labels -f 'labels[]=<label>'` / `gh api --method DELETE $R/issues/<n>/labels/<label>`
- **Assign**: `gh api --method POST $R/issues/<n>/assignees -f "assignees[]=$(gh api user --jq .login)"` (REST has no `@me`).
- **Close**: post the explanation as a comment first, then `gh api --method PATCH $R/issues/<n> -f state=closed -f state_reason=completed` (or `not_planned`).
- **Create a missing label**: `gh api $R/labels -f name="<label>" -f color="<hex>"`.

File issues only into this repo. Never file into `mattpocock/skills` (the repo these skills come from).

## Pull requests as a triage surface

**PRs as a request surface: no.** _(Set to `yes` if this repo treats external PRs as feature requests; `/triage` reads this flag.)_

When set to `yes`, PRs run through the same labels and states as issues:

- **Read a PR**: `gh api $R/pulls/<n>` for the body, `gh api $R/issues/<n>/comments` for the conversation, and `gh api $R/pulls/<n> -H 'Accept: application/vnd.github.diff'` for the diff.
- **List external PRs for triage**: `gh api --paginate "$R/pulls?state=open" --jq '.[] | select(.author_association | IN("OWNER","MEMBER","COLLABORATOR") | not) | {number, title, author: .user.login, author_association, labels: [.labels[].name]}'`.
- **Comment / label / close**: the issue endpoints above work on PR numbers too; close with `gh api --method PATCH $R/pulls/<n> -f state=closed`.

GitHub shares one number space across issues and PRs, so a bare `#42` may be either: an issue read of a PR returns a `pull_request` key.

## When a skill says "publish to the issue tracker"

Create a GitHub issue.

## When a skill says "fetch the relevant ticket"

Read it as in **Read an issue** above.

## Wayfinding operations

Used by `/wayfinder`. The **map** is a single issue with **child** issues as tickets.

- **Map**: a single issue labelled `wayfinder:map`, holding the Notes / Decisions-so-far / Fog body.
- **Child ticket**: an issue linked to the map as a GitHub sub-issue (see **Make an issue a sub-issue of a parent**). Labels: `wayfinder:<type>` (`research`/`prototype`/`grilling`/`task`). Once claimed, the ticket is assigned to the driving dev.
- **Blocking**: see **Blocking** under Conventions.
- **Frontier query**: list the map's open sub-issues, drop any with an open blocker (see **Count open blockers**) or an assignee; first in map order wins.
- **Claim**: assign the ticket to yourself (see **Assign**), the session's first write.
- **Resolve**: comment the answer, close the issue, then append a context pointer (gist + link) to the map's Decisions-so-far by editing the map body (`gh api --method PATCH $R/issues/<map> -F body=@map.md`).
