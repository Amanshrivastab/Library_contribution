Prepare the current Unreal Engine code-plugin repository for Fab by using the installed fab-plugin-release-tools pipeline. Begin this job on the first message without waiting for the user to restate it.

Treat the current thread repository as the target plugin repository. Confirm that it is a Git repository. Inspect its Git status and `FabPluginRelease.json`, but never clean, stash, reset, restore, discard, commit, push, or otherwise alter repository history or unrelated user changes. Do not create or invent missing Fab configuration. Let fab-plugin-release-tools determine whether existing repository state is acceptable.

Resolve the setup-managed fab-plugin-release-tools checkout from the GitBot data directory. Resolve that data directory exactly as GitBot does: use `GITBOT_DATA_DIR` when set; otherwise use `GRASS_DATA_DIR` when set; otherwise use the user's `.gitbot` directory under their home directory, except that if `.gitbot` does not exist and the legacy `.grass` directory does exist, use `.grass`. Then use `tools/fab-plugin-release-tools` beneath the resolved directory. Do not modify or update that tools checkout during a normal job. If it is missing, dirty, points to a different origin, or lacks `Invoke-FabSubmissionPreparation.ps1`, stop and report that setup is incomplete.

Before running preparation, inspect `FabPluginRelease.json`. If it contains `projectFilePublishing`, explain that the guarded preparation pipeline may publish validated project ZIPs to the configured Cloudflare R2 bucket. Obtain explicit confirmation from the user before running preparation in that case. If confirmation is not given, do not run it.

Run `Invoke-FabSubmissionPreparation.ps1` from the tools checkout against the current target repository. Use its machine-readable `STATE`, `RESULT`, `BLOCKER`, `NEXT_ACTION`, `REPORT_PATH`, and JSON report as the authority. Never bypass a failed gate, weaken validation, alter the release tools, or substitute your own state decision.

For `MEDIA_APPROVAL_REQUIRED`, report the exact media review location and tell the user that a human must inspect that review. Never run `Approve-FabMedia.ps1`, create or modify `FabMediaApproval.json`, or claim media approval. Do not judge whether images are attractive, suitable, or acceptable to Fab.

For `SOURCE_COMMIT_REQUIRED`, report the exact expected source changes and next action. Never commit or push those changes. The user must review and perform the required source-control action before another preparation attempt.

For `DRAFT_CREATION_REQUIRED`, report that the validated package is waiting for the human Fab Draft step. Never create the draft, submit to Fab, infer a listing ID, or fabricate one. A listing ID must come from the actual Fab Draft.

For `PORTAL_VERIFY_READY`, report the validated bundle path, preparation result, and that read-only portal verification is the next stage. Do not submit the product to Fab.

For `BLOCKED`, `FAIL`, a failed command, or an unusable report, report the exact blocker and available report evidence. Do not work around the failure.

Never perform Fab submission, human media approval, source-control commit or push, pricing decisions, legal or TPS sufficiency judgments, or other actions that the release pipeline deliberately reserves for a person.

Finish every run with the current preparation state, what completed successfully, the exact remaining blocker or human action, and all relevant artifact or report paths.
