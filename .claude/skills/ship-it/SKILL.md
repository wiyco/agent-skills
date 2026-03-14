---
name: ship-it
description: Automates branch creation, committing, PR creation, and review requests. Organizes changes into appropriate scopes to ensure a reviewer-friendly process. Triggers when the user asks to "commit" or "create a PR".
allowed-tools: Bash(git:*), Bash(gh:*)
---

# Automated commit, PR creation, and review request

Communicate in the user's preferred language. If the user does not specify a language, respond in Japanese.

## Flow

1. Branch creation
2. Commit message generation and commit execution
3. PR creation and review request

## Branch creation

Following Conventional Commits is recommended. Infer the appropriate `type` and `scope` based on the changes, and confirm with the user before creating a branch. Branch names should ideally follow the `<type>/<scope>/<description>` format. If the changes span multiple scopes, consider splitting the changes and creating multiple branches.

## Commit message generation

Following Conventional Commits is recommended. Infer the appropriate `type` and `scope` from the content of the changes, and confirm with the user before executing the commit. If the changes span multiple scopes, consider splitting them into multiple commits. If there is supplementary information, add it to the body or footer of the commit message.

examples:

```text
diff: src/routes/admin/users/admin.users.spec.ts
commit message: test(e2e/admin/users): fix flaky user creation test by replacing waitForTimeout with waitForResponse
```

```text
diff: src/routes/agent-app/[id]/components/from-tasks/UserPrompt/UserPrompt.tsx
commit message: fix(agent-app): layout shift caused by missing div wrapper in UserPrompt component
```

```text
diff: src/components/Markdown/components/Extra/MermaidRenderer.tsx
commit message: refactor(MermaidRenderer): use common sleep function instead of custom timeout for better readability and maintainability
```

```text
diff: src/lib/cookies.ts
commit message: feat(lib): add utility functions for cookie management
```

## PR creation and review request

Following Conventional Commits is recommended. Divide the changes into appropriate scopes to create reviewer-friendly PRs. If the overall changes are extensive, consider splitting them into multiple PRs.

The PR title and description MUST strictly adhere to the Pull Request Template without breaking its format. To make the PR reviewer-friendly, it is recommended to concisely summarize the changes in a table format. Ensure this table is inserted appropriately within the existing sections of the template without altering the overall template structure.

**Assign the PR creator** (the user who triggered the ship-it command) to the PR automatically after creation.

Request reviews only after all PRs have been created. Only request reviews for PRs that have successfully passed CI. Prompt the user to select a reviewer from the following list:

1. (team-name)/frontend
2. (team-name)/backend
3. (team-name)/tech-lead

If the `gh` command is unavailable, prompt the user to install the [GitHub CLI](https://cli.github.com).

## References

- [Conventional Commits](references/conventional-commits.md)
- [Pull Request Template](references/pull-request-template.md)
