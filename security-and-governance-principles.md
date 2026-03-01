# Security and Governance Principles

Security and governance are foundational to STO Info.

All features, automation, and processes are evaluated against the following principles.

---

## Security-First Development

- No direct pushes to protected branches
- Pull request review required before merge
- Automated CI checks required before merge
- Security scanning integrated into workflows
- Strict environment variable validation at startup

---

## Branch Protection and Review Model

- `development` and `production` branches are protected
- Status checks must pass before merging
- Releases are tag-driven
- Controlled merge strategy

This ensures traceability and reduces the risk of unreviewed changes.

---

## CI/CD Enforcement

The project uses automated workflows to enforce:

- Static analysis
- Security scanning
- Dependency review
- Code quality checks
- Release validation

Automation is preferred over manual process wherever possible.

---

## Data Governance and Retention

Where user-related data is processed:

- Data minimisation principles apply
- Audit logs are retained for a defined period (currently 180 days)
- IP addresses are nullified after 90 days
- Retention enforcement is automated where possible

---

## Transparency

- Documentation lives within repositories
- The Wiki acts only as a navigation layer
- Roadmap direction is visible
- Governance decisions are documented

---

## Intellectual Property Respect

STO Info is a community-driven project and is not affiliated with:

- Cryptic Studios
- Paramount
- CBS

All content and features are designed to respect existing intellectual property boundaries.