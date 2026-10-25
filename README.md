# VoIPKing Updates

Private preparation for the official VoIPKing AWS image. No active update feed or release is published yet.

## Purpose

This repository will contain only approved update payloads, signed release metadata, complete release notes, and the source and license materials required for those releases. Existing development repositories, their history, customer data, phone enrollment, credentials, certificates and backups are not imported here.

Gabe maintains the official AWS image and approves its official releases. Offered support covers that AWS distribution; independent or self-hosted installations are outside that support scope. Open-source licensing does not imply a support commitment. Software license selection and public source publication remain separate approval steps. SIP Guard retains its existing GPL licensing.

## Preview feed plan

- Use GitHub Releases for versioned application-update archives and release-note assets. No GitHub Pages site, S3 bucket, paid runner or new AWS service is needed for this preparation.
- Reserve `preview.json` on `main` for the signed preview manifest. Do not add an unsigned placeholder or configure customer instances to use this private repository.
- Planned discovery URL after publication approval: `https://raw.githubusercontent.com/VoIPKing/voipking-updates/main/preview.json`.
- Allow only `raw.githubusercontent.com`, `github.com` and `release-assets.githubusercontent.com` for discovery and download redirects, with normal HTTPS certificate validation.
- Customer images contain the public verification key only. Private signing keys and GitHub credentials belong outside customer images and release assets. No signing credential is created by this preparation.
- Sign the exact UTF-8 manifest payload with Ed25519. Its envelope contains `key_id`, base64 `payload` and base64 `signature`.
- The signed payload identifies product `voipking-pbx`, channel `preview`, increasing release version, minimum installed version, issue/expiry times, complete notes, and the archive HTTPS URL, byte length and SHA-256. The installer additionally verifies its baseline and every previous file hash.
- Apply the stricter installer limits: 32 MiB compressed and expanded, 2 MiB per file, at most 511 changed files, and a manifest validity window no longer than 31 days.
- Assign the bootstrap release version before building the first signed delta. Build that delta against the bytes actually deployed by the approved bootstrap, rather than assuming the saved AMI already includes the updater.

## Planned release contents

1. Signed metadata for the preview channel.
2. A versioned archive containing only approved changed application files and the installer manifest.
3. Complete release notes as downloadable TXT and PDF, matching the signed notes displayed on PBX System.
4. Checksums, source/provenance and applicable license/notices materials reviewed for that release.

Application updates exclude operating-system packages, native modules, database migrations, service units, customer settings and backups. One-time updater/bootstrap installation is a separate, approved deployment. Application rollback is not a full-system backup restore.

## Before the first customer test

- Review and approve the exact files that would become public, including the source and licensing materials.
- Obtain approval before changing this repository to public, creating signing credentials, or publishing a release.
- Prepare and verify a signed, harmless preview delta and its complete notes.
- Obtain approval before starting a server, adding management access, changing AWS, or deploying the updater foundation.
- On the designated Virginia customer test, verify PBX System → Updates: check, download notes/package, install, retain customer settings and login, and roll back.
- Keep Oregon, existing images, servers and backups outside any change unless separately authorized.

## Current status and cost

Repository visibility: private. Contents: documentation only. No release, active `preview.json`, workflow, signing credential, customer launch or deployment is created here. Existing source repositories remain unchanged.

This GitHub-only preparation has no additional hosting charge and uses no Actions, Codespaces or AWS compute. Existing retained disks and snapshots continue their normal storage charges. Any later AWS build/deployment block requires a separate plan, cost ceiling and approval.

References: [GitHub plans](https://docs.github.com/en/get-started/learning-about-github/githubs-plans) · [GitHub Releases](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases)

Prepared October 25, 2026.
