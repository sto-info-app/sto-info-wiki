# Architecture Overview

This page provides a high-level overview of how STO Info is structured.

Detailed implementation documentation is maintained within each repository.

## Core Components

### Backend

- NestJS application
- REST API
- PostgreSQL database integration
- Authentication and audit handling

Backend documentation (canonical):

- [Backend Overview](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/backend.md)
- [API Endpoints](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/api-endpoints.md)
- [Database](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/database.md)
- [Environment Variables](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/environment-variables.md)
- [Infrastructure](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/infrastructure.md)
- [Security](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/security.md)
- [Frontend (backend notes)](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/frontend.md)

### Frontend

- Angular application
- Auth integration
- API communication with backend
- UI state and data handling

Frontend documentation (canonical):

- [Docs Index](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/README.md)
- [Architecture](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/architecture.md)
- [Deployment](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/deployment.md)
- [Operations](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/operations.md)
- [Security and Data](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/security-and-data.md)
- [Memory Leak Prevention](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/memory-leak-prevention-guide.md)

## Infrastructure

- Render (application hosting)
- Cloudflare (DNS, proxy, security layer)
- Transactional email provider (system notifications)
- GitHub Actions (CI/CD automation)

See backend [Infrastructure](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/infrastructure.md) for more detail.

## Security Model (High-Level)

- Protected branches
- Pull request review requirements
- CI security checks (CodeQL, Scorecard, etc.)
- Audit logging and retention controls

Automation documentation (canonical):

- Backend: [docs/github/README.md](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/github/README.md)
- Backend: [docs/github/SECURITY-AUTOMATION.md](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/github/SECURITY-AUTOMATION.md)
- Backend: [docs/github/QUALITY-AUTOMATION.md](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/github/QUALITY-AUTOMATION.md)
- Frontend: [docs/github/README.md](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/github/README.md)
- Frontend: [docs/github/SECURITY-AUTOMATION.md](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/github/SECURITY-AUTOMATION.md)
- Frontend: [docs/github/QUALITY-AUTOMATION.md](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/github/QUALITY-AUTOMATION.md)
