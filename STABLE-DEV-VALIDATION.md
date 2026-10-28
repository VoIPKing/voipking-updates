# Stable and DEV channel validation

The Stable baseline is 0.10.8 using the exact existing signed-package bytes. Stable metadata uses the separately pinned stable-20261028 public key. The 0.10.9 DEV prerelease is a version-only candidate; no PBX feature logic is changed.

For the first test, leave the installed PBX at 0.10.8 and do not install the DEV package. Start the designated Virginia test server, sign in to the PBX, and check System > Updates. The prepared baseline should show Stable and installed 0.10.8.

In the private voipking-pbx repository, run the DEV update enrollment workflow on main for the designated instance with action enable-dev. Wait for Success. In the PBX, Check for Updates should offer 0.10.9 with DEV ONLY notes. Run the same workflow with return-stable, wait for Success, and Check for Updates again. The installed version remains 0.10.8 and the DEV offer disappears.

Return to Stable restores the exact saved feed configuration and signing trust and clears update download caches. It preserves customer data, worker journals, audit history, and rollback backups. Switching channels does not roll back installed software. Installation/rollback is a separate test.

The existing preview.json remains on 0.10.8 so older updaters retain their working entry point. The signed preview catalog retains prior releases and adds 0.10.9. Stable and preview metadata expire; renew signed metadata before expiry. This is channel-validation preparation, not final production/Marketplace acceptance.
