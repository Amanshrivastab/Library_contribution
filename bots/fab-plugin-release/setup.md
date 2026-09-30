This bot supports Windows only.

Ensure PowerShell 7.4 or later and Git are available.

Maintain a clean checkout of https://github.com/metyatech/fab-plugin-release-tools.git in the GitBot data directory under `tools/fab-plugin-release-tools`. Resolve the GitBot data directory exactly as GitBot does: use `GITBOT_DATA_DIR` when set; otherwise use `GRASS_DATA_DIR` when set; otherwise use the user's `.gitbot` directory under their home directory, except that if `.gitbot` does not exist and the legacy `.grass` directory does exist, use `.grass`.

If the checkout does not exist, clone the public repository there. If it already exists, verify that its `origin` points to `https://github.com/metyatech/fab-plugin-release-tools.git`, verify that the checkout has no local changes, and update it only by fast-forward. Never discard, overwrite, reset, or stash local changes.

Verify that `Invoke-FabSubmissionPreparation.ps1` exists in that checkout.

Do not run the repository's development bootstrap merely to use the release pipeline.

Do not require a particular Unreal Engine version, GitHub CLI authentication, Wrangler authentication, Cloudflare configuration, or other product-specific dependency during setup. Those requirements depend on the target plugin and are validated by the release pipeline when the bot runs.
