---
name: jira
description: Work with Jira Cloud from the command line using the official Atlassian CLI (acli) — authenticate, search with JQL, view/create/edit/transition/comment on work items, and handle multiple Atlassian sites. Use whenever the task involves Jira issues, tickets, boards, sprints, JQL, or an Atlassian API token. Also covers Confluence via the same tool.
---

# Jira via Atlassian CLI (acli)

Official Atlassian CLI. Installed at `/opt/homebrew/bin/acli`.

## Check state first

Always run this before anything else. It tells you whether you are authenticated and against which site.

```bash
acli jira auth status
```

- Logged in → proceed.
- Not logged in → see **Authentication**.
- Wrong site → `acli jira auth switch`

## Authentication

Two routes. Prefer OAuth.

### OAuth (preferred — no token to manage)

```bash
acli jira auth login --web
```

Opens a browser, user approves, credentials stored by acli. No API token needed, nothing to put in Keychain, nothing to rotate manually. Use this unless the environment is headless.

### API token (headless / CI)

Only when a browser is unavailable.

**Getting a token:** Atlassian API tokens are per *account*, not per site or org. One token authenticates the account against every Atlassian site it can reach.

1. https://id.atlassian.com/manage-profile/security/api-tokens
2. **Create API token** (or **Create API token with scopes** for a scoped one)
3. Label it, copy immediately — shown once

Scoped tokens limit *what* (products, operations), not *which* site. A `read:jira-work`-only token will not reach Confluence.

**Storing it:** macOS Keychain, keyed by account email.

```bash
# store (user runs this themselves — keeps the token out of shell history)
security add-generic-password -s atlassian-api-token -a "$ATLASSIAN_EMAIL" -w

# read
security find-generic-password -s atlassian-api-token -a "$ATLASSIAN_EMAIL" -w
```

**Logging in with it** — `--token` reads from stdin, never an argument:

```bash
security find-generic-password -s atlassian-api-token -a "$ATLASSIAN_EMAIL" -w \
  | acli jira auth login --site "yoursite.atlassian.net" --email "$ATLASSIAN_EMAIL" --token
```

Never pass a token as a command-line argument — it lands in shell history and `ps` output.

### Multiple accounts

acli manages several natively. Do not build your own namespacing on top of it.

```bash
acli jira auth status    # who am I, which site
acli jira auth switch    # change active account
acli jira auth logout
```

## Reading

```bash
# JQL search, table output
acli jira workitem search --jql "project = TEAM AND status != Done"

# machine-readable — use --json whenever you will parse the result
acli jira workitem search --jql "assignee = currentUser() AND resolution = Unresolved" --json

# pick fields, cap results
acli jira workitem search --jql "project = TEAM" --fields "key,summary,status,assignee" --limit 50

# every page (careful on big projects)
acli jira workitem search --jql "project = TEAM" --paginate

# just a count
acli jira workitem search --jql "project = TEAM" --count

# saved filter
acli jira workitem search --filter 10001

# one item
acli jira workitem view TEAM-123
acli jira workitem view TEAM-123 --fields "*all" --json
acli jira workitem view TEAM-123 --fields summary,comment
```

Default search fields: `issuetype,key,assignee,priority,status,summary`.

Pipe `--json` through `jq` rather than parsing table output.

## Writing

```bash
acli jira workitem create
acli jira workitem create-bulk         # from JSON or CSV
acli jira workitem edit
acli jira workitem transition
acli jira workitem assign
acli jira workitem comment
acli jira workitem link
acli jira workitem clone
acli jira workitem archive
acli jira workitem delete
```

Run `acli jira workitem <cmd> --help` for flags before invoking — they differ per subcommand and change between releases. Do not guess flags from memory.

### Destructive operations

`delete`, `archive`, and bulk `edit`/`transition` hit real tickets other people depend on. Confirm with the user before running any of them, and before any bulk operation regardless of verb. Bulk commands accept a JQL query or filter ID — always run the same JQL through `search --count` first and show the user how many items it matches.

## Other surfaces

```bash
acli jira --help          # project, board, sprint, and other groups
acli confluence --help    # same auth, Confluence Cloud
acli admin --help         # org admin
```

## Conventions

- `--json` for anything programmatic, human-readable tables only for direct display
- `--web` on `search` and `view` opens the browser instead of printing — use when the user wants to look at it themselves
- Check `acli --version`; command sets grow between releases, so trust `--help` over this document when they disagree
- Never echo a token, even partially

## When acli is the wrong tool

Falls short for: webhooks, custom field schema administration, anything not yet exposed as a subcommand. Fall back to the REST API directly:

```bash
curl -s -u "$ATLASSIAN_EMAIL:$TOKEN" \
  -H "Accept: application/json" \
  "https://yoursite.atlassian.net/rest/api/3/issue/TEAM-123"
```

Jira Cloud REST API v3 docs: https://developer.atlassian.com/cloud/jira/platform/rest/v3/
