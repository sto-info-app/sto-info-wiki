# Versioning and Release Flow

This page summarises how changes move from development to production.

---

## Branching Model

- `development` – active development and default branch
- `production` – stable release branch

Feature work flows into `development` via pull requests.

---

## Pull Request Flow

1. Feature branch created from `development`
2. Changes implemented
3. Pull request opened
4. Automated checks run
5. Review required
6. Merge into `development`

No direct commits to protected branches.

---

## Release Process

Releases are tag-driven.

1. Code stabilised in `development`
2. Version bump committed
3. Release tag created
4. Automated release workflows triggered
5. Deployment executed

This ensures:

- Traceable releases
- Clear version history
- Reproducible builds

---

## CI/CD Automation

Automated workflows enforce:

- Linting
- Testing
- Security checks
- Dependency scanning
- Release validation

Production deployments only occur from validated states.

---

## Release Visibility

Each release:

- Has a version tag
- Includes release notes
- Is traceable to pull requests
- Is auditable through Git history

---

## Governance Goals

The release process is designed to:

- Minimise manual intervention
- Reduce deployment risk
- Provide clear audit trails
- Maintain consistency across backend and frontend services
