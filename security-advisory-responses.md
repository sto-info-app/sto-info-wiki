# Security Advisory Responses

This page records how STO Info responded to external security advisories that affected more than one repository. It is an overview: the canonical, versioned detail lives in each repository's `/docs` and `SECURITY.md`, linked below.

---

## November 2026: glob and minimatch advisories

### What happened

- **glob** ([GHSA-3g3m-2fjr-6pw4](https://github.com/advisories/GHSA-3g3m-2fjr-6pw4), moderate): cancelling a file search did not stop it, so it could keep reading the filesystem after a timeout. Every release from 9.0.0 to 14.0.1 is affected.
- **minimatch** ([GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249), moderate): a crafted pattern could make matching very slow. Every release from 7.0.0 to 11.0.0 is affected.

Both were published on 30 October 2026 and fixed only in the newest major version, so the packages that depend on older versions could not pick up the fix themselves. Neither library is given untrusted input anywhere in STO Info. The response was preventive.

---

### What changed

| Area | Change |
| --- | --- |
| Overrides | The backend, frontend, file scan worker and Shortcut bot each force the affected `glob` versions to 14.0.6 or later. The first three also force the affected `minimatch` versions to 11.0.8 or later; in the bot the patched `glob` brings a patched `minimatch` with it. The overrides apply only to the vulnerable versions and stop matching once upstream packages catch up. |
| Production exposure | `glob` was in the production dependencies of the backend (through the mailer module) and the Shortcut bot (through TypeORM). Everything else was development tooling. |
| Overrides removed | Five older overrides were no longer needed and were removed: `multer` (backend and bot), `compression` and `vite` (frontend), and `argparse` (frontend and worker), whose advisory was withdrawn. |
| Dependencies | All four Node.js repositories took their latest minor and patch releases, and the pipelines took the latest CodeQL, SonarQube scan and release actions. |
| Remaining advisory | `npm audit` reports one low-severity advisory in development tooling only: `deepmerge` ([GHSA-gcqx-w48m-w2h4](https://github.com/advisories/GHSA-gcqx-w48m-w2h4)), which has no fixed release. Production dependencies are clean at every severity. |

The catalogue extractor has no runtime dependencies and its development tools were already current.

The per-repository detail is in the documents listed under [Where the detail lives](#where-the-detail-lives) below.

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
