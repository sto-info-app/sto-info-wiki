# Writing and Markdown

Everything a member writes on STO Info — a Storytime Chapter, a Story or Arc
description, a Character biography, a Custom Tracking note — is written as
plain text with a few marks in it, and turned into a page by a renderer that
accepts a deliberately small, closed set of marks. Anything outside the set is
shown exactly as it was typed.

The set is small because the writing is a member's rather than an
administrator's. A narrow, closed list is something the project can be certain
about; an open one is not.

---

## The site's own marks

Two of the marks are STO Info's own rather than Markdown's, because prose wants
both and Markdown has a spelling for neither:

- `{indent}` at the very start of a paragraph indents that paragraph's first
  line, the way a printed novel does.
- `{spacer}` standing alone as a block leaves a gap between one passage and the
  next, for a change of scene that wants air rather than a dividing line.

Both are exact and lower case, and each is recognised in one position only. A
member who writes either anywhere else sees it as the text it is, which is why
there is no escape syntax to learn.

They will mean nothing anywhere else Markdown is written.

---

## Where the full reference lives

Inside the application, next to the writing: the mark beside "Markdown is
supported" under any Storytime field opens the same reference the help section
shows under "Writing with Markdown". Both read from one list, so a mark the
renderer gains appears in both places or neither.

Canonical technical documentation lives in the repositories:

- Backend, for the Storytime renderer and the rules it enforces:
  [docs/backend.md](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/backend.md)
- Frontend, for the News renderer and the styling both produce:
  [docs/ui-components.md](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/ui-components.md)

---

## Related pages

- [Architecture Overview](architecture-overview.md)
- [Security and Governance Principles](security-and-governance-principles.md)
- [Repository Index](repository-index.md)
