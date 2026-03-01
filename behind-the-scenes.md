# Behind the Scenes

This page provides onboarding context for contributors.

It outlines the systems and tools used to develop and operate STO Info.

## Development Stack

- Backend: NestJS
- Frontend: Angular
- Database: PostgreSQL
- Node.js environment

## Hosting and Infrastructure

- Render - application hosting
- Cloudflare - DNS, proxying, and security layer
- Transactional email provider for system notifications

## CI/CD and Automation

- GitHub Actions
- CodeQL
- OpenSSF Scorecard
- Dependabot
- Security and quality workflows defined per repository

Branch protections:

- No direct pushes to protected branches
- Pull request review required
- Automated checks required before merge

## Project Management

- Shortcut - primary internal planning and task tracking
- GitHub Issues - public tracking where appropriate

## Governance Principles

- Documentation lives inside repositories
- Wiki acts as a navigation layer only
- Security-first approach
- Audit and logging controls in place
- Controlled release process
