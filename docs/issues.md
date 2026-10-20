## Git and pull requests

### Branches

We use **trunk-based development**: everyone works in small, short-lived branches off `main`. No long-running development branches.

Name your branch `type/issue-number-short-description`:

- `feat/12-login-rate-limit`
- `fix/24-wrong-discount-total`
- `docs/04-adr-storage`

Merge into `main` within **2 to 3 days**. If a task is bigger than that, split it into smaller pieces.

### Merging

- Nobody pushes directly to `main`. Everything goes through a pull request (PR).
- We always use **Squash and Merge**, so `main` stays a clean, readable list of changes.
- Name your PR using [Conventional Commits](https://www.conventionalcommits.org): `feat:`, `fix:`, `docs:`, `refactor:`, or `chore:`. Example: `feat: add login rate limiting`. GitHub adds the PR number for you.

### What a good PR looks like

- **Small:** under 400 changed lines. Generated code, lockfiles, and assets don't count.
- **Linked to an issue:** write `Closes #12` in the description.
- **Green:** formatting, linting, and tests pass before anyone reviews it.

### Review comments

Start each comment with a label so the author knows how much it matters:

| Label | Meaning |
|---|---|
| `[Blocking]` | Must be fixed before merging: a bug, a missing test, an unhandled edge case, or a design problem. |
| `[Suggestion]` | A different approach or an improvement. The author can take it or leave it. |
| `[Question]` | You're curious about the reasoning or an edge case. |
| `[Nit]` | A small thing like a typo or naming. The author can fix it without asking for another review. |

---

## Issues: ready and done

### Ready (before you start coding)

An issue is ready to pick up when:

1. It's a real GitHub Issue in the right repo, not just a draft card on the board.
2. It explains the **context**, the **approach**, and the **acceptance criteria** (clear, checkable conditions for "finished").
3. It names any interfaces or schemas that will change.

### Done (before you merge)

A task is done when:

1. Every acceptance criterion in the issue is met.
2. Tests cover the new logic and its edge cases.
3. The docs and schema files affected by your change are updated **in the same PR**.
4. At least one teammate has approved.

---

## Quick checklist before opening a PR

- [ ] Branch name follows `type/issue-number-description`
- [ ] PR title follows Conventional Commits
- [ ] Description includes `Closes #<issue>`
- [ ] Under 400 changed lines
- [ ] CI is green
- [ ] Docs and schemas updated in this PR