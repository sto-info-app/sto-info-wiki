# Custom Tracking

Custom Tracking lets a signed-in member define their own sections, tabs and
fields, once for all of their STO accounts or once for all of their STO
characters, and then record a separate value against each one.

It exists because no fixed set of fields covers what players actually track.
One member counts ship upgrades, another logs fleet contributions, another
keeps notes on which captain flies what. Rather than guessing at those and
adding a table per idea, the member builds the shape and the site holds the
values.

Canonical technical documentation lives in the backend repository at
`docs/custom-tracking.md`.

---

## How it is arranged

Sections contain tabs, tabs contain fields, and a field holds one value per STO
account or character. Definitions are built once per scope; values are recorded
per record.

Definitions are built in Settings and nowhere else — what to record, in what
order and who may see it are decisions about every record at once.

Values can be filled in from Settings, where you pick the record first, or from
an account or captain page itself, where "Edit tracked data" opens the same
editor on the record you are already looking at.

---

## Visibility

Everything is private by default and public sharing is opt-in at every level.
A field's value is shown to a visitor only when all of these are true:

- the member's profile is public and the account is in good standing
- the STO account is public
- the character is public, for character-scoped fields
- the section is public
- the tab is public
- the field is public
- nothing in that chain has been deleted or administratively hidden

A private ancestor hides everything beneath it, whatever the descendant says.
Turning off profile visibility removes all public custom data immediately
without touching any lower-level setting.

The chain is enforced in the backend query, not in the browser. A member who
has published none of their tracking and one who has published some and kept it
private look identical from outside.

---

## Content rules

Members define the fields, so the site cannot know in advance what goes in
them. The position taken is the honest one:

- A content agreement must be accepted before anything can be created, and it
  is versioned — raising the version blocks further editing until it is
  accepted again.
- The agreement prohibits personal information, about the member or anybody
  else, and does not claim the site can prevent it being entered.
- Pictures go through the same upload pipeline, size limits and content rules
  as everything else on the site.
- Video fields hold a YouTube identifier only, and nothing is fetched from
  YouTube until a reader presses play.

---

## Moderation

An administrator can hide a section, tab or field from public view without
deleting it. The member keeps their data, their account and their ability to
edit what they wrote; the rest of the world stops seeing it. Hiding a field
hides it for every account and character at once.

Where the problem is the member rather than one piece of content, the existing
route applies: disabling the account hides everything they have published.

Reporting an individual section, tab or field is not built. Reports are about
members, and an administrator acts from a member report and the page it names.

---

## Retention

Deleting anything hides it immediately and irreversibly — there is no undelete.
The underlying records are permanently removed 180 days later by a scheduled
job, along with any pictures they held in image storage.

One exception: an option that a surviving value still refers to is kept for
longer, because its label is the only thing that can render that value. It goes
when the last value needing it does.

Closing an account removes custom tracking data along with everything else, on
the same closed-account schedule.

---

## Related pages

- [Architecture Overview](architecture-overview.md)
- [Security and Governance Principles](security-and-governance-principles.md)
- [Repository Index](repository-index.md)
