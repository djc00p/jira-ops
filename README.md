# 🎫 Jira Ops

[![ClawHub Skill](https://img.shields.io/badge/ClawHub-Skill-blue)](https://clawhub.ai/djc00p/jira-ops) [![Agent Skill](https://img.shields.io/badge/Agent-Skill-blue)](#) [![Jira](https://img.shields.io/badge/Jira-0052CC.svg)](https://www.atlassian.com/software/jira) [![MCP](https://img.shields.io/badge/MCP-Supported-4CAF50.svg)](https://modelcontextprotocol.io) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Jira Ops** retrieves, analyzes, and updates Jira tickets — via an MCP server (recommended) or the direct REST API.

Beyond moving tickets around, it extracts the engineering-relevant content from a ticket: functional requirements, testable acceptance criteria, test types, edge cases, and dependencies. That's the part that turns a Jira ticket into actionable work.

---

## 🎯 When to Activate

* Fetching ticket requirements and acceptance criteria
* Adding progress comments or status updates
* Transitioning ticket status (To Do → In Progress → Done)
* Searching for issues via JQL queries
* Linking PRs or branches to tickets

---

## 🔧 Setup

### Option A: MCP Server (Recommended)

Install `mcp-atlassian` via `uvx`:

```json
{
  "jira": {
    "command": "uvx",
    "args": ["mcp-atlassian==0.21.0"],
    "env": {
      "JIRA_URL": "https://YOUR_ORG.atlassian.net",
      "JIRA_EMAIL": "your.email@example.com",
      "JIRA_API_TOKEN": "your-api-token"
    }
  }
}
```

Get your API token: <https://id.atlassian.com/manage-profile/security/api-tokens>

### Option B: Direct REST API

Set these environment variables:

* `JIRA_URL` — Jira instance URL
* `JIRA_EMAIL` — your account email
* `JIRA_API_TOKEN` — API token (**never hardcode**)

---

## 🛠 MCP Tools

With `mcp-atlassian` configured:

| Tool | Purpose |
|------|---------|
| `jira_search` | JQL queries |
| `jira_get_issue` | Fetch issue details |
| `jira_create_issue` | Create new issues |
| `jira_update_issue` | Update fields |
| `jira_transition_issue` | Change status |
| `jira_add_comment` | Add comments |
| `jira_get_transitions` | List available transitions |

---

## 🔍 Analyzing Tickets

Extract from tickets:

* **Functional requirements** — what needs to be built
* **Acceptance criteria** — testable conditions
* **Test types** — unit, integration, E2E
* **Edge cases** — error scenarios, boundary conditions
* **Dependencies** — linked issues, APIs, systems

---

## 📝 Updating Tickets

| Workflow | Jira Action |
|----------|-------------|
| Start work | Transition to "In Progress" + comment the branch name |
| Tests done | Comment with a test coverage summary |
| PR created | Comment with the link, transition if needed |
| Merged | Transition to "Done" |

---

## 🔐 Security

* **Never hardcode API tokens**
* Use environment variables or a secrets manager
* Add `.env` to `.gitignore`
* **Rotate tokens if exposed**
* Use least-privilege scopes

---

## 📚 References

* `references/mcp-setup.md` — full MCP server configuration and troubleshooting
* `references/jql-queries.md` — JQL patterns for common searches
* `references/ticket-workflows.md` — status transition workflows and comment templates

---

**Adapted from [everything-claude-code](https://github.com/affanm/everything-claude-code) by [@affaan-m](https://github.com/affaan-m) (MIT).**

**Published by [@djc00p](https://github.com/djc00p)**
