# Security Advisory Responses

This page records how STO Info responded to external security advisories that affected more than one repository. It is an overview: the canonical, versioned detail lives in each repository's `/docs` and `SECURITY.md`, linked below.

---

## October 2026: eMudhra certificate compromise and Node.js security release

### What happened

- **eMudhra (emSign) certificate compromise**: the private keys of eight intermediate certificates issued by eMudhra, a widely trusted certificate authority, were confirmed compromised. Software that still trusted them could be shown forged HTTPS certificates.
- **Node.js security release**: Node.js shipped 22.23.4, 24.22.1 and 26.12.1, fixing TLS hostname-check and Brotli decompression flaws and distrusting the affected certificates.
- **Sonar advisory**: SonarSource asked users of SonarQube and its scanners to update or apply a workaround for the same certificate issue.

STO Info had no indication of exploitation. The response was preventive.

---

### What changed

| Area | Change |
| --- | --- |
| Node.js runtime | Every Node.js repository moved to **Node.js 24.22.1** for development, CI and Render, pinned in `.nvmrc`. The Shortcut bot gained a pinned version for the first time. |
| File scan worker image | Rebuilt on the Node.js 24.22.1 base image with a current certificate store, verified to reject the compromised chains. |
| Code quality scanning | The SonarQube scan action moved to v8.4.0 in the backend, frontend and worker pipelines. |
| Dependencies | All repositories took their latest minor and patch releases. Overrides were refreshed, and `npm audit` is clean at every severity in all four Node.js repositories. |
| Frontend performance audit | Lighthouse CI, which pinned an outdated Lighthouse with an unpatched dependency, was replaced by a script that runs Lighthouse 13 directly. |
| Frontend icons | Font Awesome is now bundled with the site rather than loaded from a third-party script on every page. This also fixed a layout shift and a forced reflow that the new audit found. |
| TypeScript | All repositories stay on TypeScript 6 because the build tooling does not yet support TypeScript 7. The code was made ready for 7, and Dependabot no longer proposes TypeScript major updates. |

The catalogue extractor, which is Python, uses the operating system's certificate store and needed no change. This wiki has no runtime.

---

### Where the detail lives

- Backend: [SECURITY.md](https://github.com/sto-info-app/sto-info-backend/blob/development/SECURITY.md) and [docs/security.md](https://github.com/sto-info-app/sto-info-backend/blob/development/docs/security.md)
- File scan worker: [SECURITY.md](https://github.com/sto-info-app/sto-info-file-scan-worker/blob/development/SECURITY.md) and [docs/infrastructure.md](https://github.com/sto-info-app/sto-info-file-scan-worker/blob/development/docs/infrastructure.md)
- Frontend: [SECURITY.md](https://github.com/sto-info-app/sto-info-frontend/blob/development/SECURITY.md), [docs/security.md](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/security.md) and [docs/github/QUALITY-AUTOMATION.md](https://github.com/sto-info-app/sto-info-frontend/blob/development/docs/github/QUALITY-AUTOMATION.md)
- Shortcut bot: [docs/DEPENDENCIES.md](https://github.com/sto-info-app/sto-info-shortcut-bot/blob/development/docs/DEPENDENCIES.md)

---

## Related pages

- [Security and Governance Principles](security-and-governance-principles.md)
- [Repository Index](repository-index.md)
