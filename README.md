# VoIPKing updates

This repository contains signed release metadata, immutable application packages, and release notes. PBX downloads are anonymous; production upgrades do not require instance registration.

## Current channels

- `stable.json` and `stable-catalog.json`: Stable releases, signed by `stable-20261028`. Current Stable is 0.10.8.
- `dev.json` and `catalog.json`: operator-enabled DEV releases, using the existing preview signing key. DEV enrollment is managed separately in the private repository.
- `preview.json`: compatibility entry point embedded in the clean 0.10.2 Reinstall AMI. It now offers the existing, immutable 0.10.2-Reinstall-to-0.10.8 bridge. After installation, the release selector reads `legacy-stable-catalog.json`, which contains only Stable application releases under the image's existing signing trust.

## Clean 0.10.2 upgrade

For AMI `ami-0b13849c155292757`, use System > Updates > Check for Updates, Download Update, and Install Update. Then Check for Updates again to load the catalog. No SSH, channel-file edit, registration, or migration utility is required. Customer state and backups remain outside the application package. The protected installer retains exact source-file, package signature, version, and rollback checks.

This route was verified on the exact Reinstall baseline and protected installer: discovery, download, installation, application imports, Stable-only catalog, exact rollback, and reinstall. Anonymous public downloads passed; a fresh instance also completed installation with its built-in health check on 2026-10-29. The distinct original 0.10.2 image and older pre-catalog versions retain their separate legacy manifests; do not assume they have the same file baseline.

Published package bytes are never replaced. Renew signed metadata before expiry and increase catalog serials. When promoting future Stable releases, maintain both the Stable-key catalog and the legacy Stable compatibility catalog. Keep DEV releases out of both. This repository's availability does not establish AWS Marketplace acceptance or telephony certification.
